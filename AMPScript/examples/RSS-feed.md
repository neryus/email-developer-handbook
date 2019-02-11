### The example of RSS feed
```
<rss xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/" xmlns:atom="http://www.w3.org/2005/Atom" version="2.0">
  <channel>
    <item>
      <title>EMR: Interim Head of Ecommerce</title>
      <description> £65k - £79k pa + prorated: EMR: Six month FTC Head of Digital Trading and Development for well-known British retailer West Midlands </description>
      <link>https://jobs.example.com/job/409859/interim-head-of-ecommerce/?TrackID=8</link>
      <pubDate>Wed, 24 Oct 2018 18:29:00 +0000</pubDate>
    </item> 
    <item>
      <title>EMR: Digital Creative Director</title>
      <description> £100k - £120k pa: EMR: Our client is a 50-strong brand studio based in London who are on a mission to be the world's most progressive brand company and we're looking for a Creative Director to help them get there - by shaping brand for the future, through technology. London </description>
      <link>https://jobs.example.com/job/409918/digital-creative-director/?TrackID=8</link>
      <pubDate>Tue, 06 Nov 2018 12:04:00 +0000</pubDate>
    </item>
    <item>
      <title> Brand Recruitment: Digital Marketing Executive - SEO focus </title>
      <description> £30k - £35k pa: Brand Recruitment: Digital Marketing Executive - SEO focus, Aylesbury - Are you a Digital Marketing Executive looking to develop their career and specialise in SEO?.. Aylesbury </description>
      <link>https://jobs.example.com/job/409916/digital-marketing-executive-seo-focus/?TrackID=8</link>
      <pubDate>Mon, 05 Nov 2018 17:10:00 +0000</pubDate>
    </item>
  </channel>
</rss>
```

### The AMPscript to retrieve content from XML
The challenge is to separate the `title` value into two values. The title consists of a company name and job title, and they are separated with a colon character. 

```
%%[
 VAR @xml, @t, @d, @u, @p, @rowCount, @i, @title, @description, @link, @pubDate, @jt, @j, @l, @q, @w

 SET @xml = HTTPGet("https://jobs.example.com/rss/?countrycode=GB")
 SET @t = BuildRowsetFromXML(@xml,"//channel/item/title",1)
 SET @d = BuildRowsetFromXML(@xml,"//channel/item/description",1)
 SET @u = BuildRowsetFromXML(@xml,"//channel/item/link",1)
 SET @p = BuildRowsetFromXML(@xml,"//channel/item/pubDate",1)
 
 SET @rowCount = RowCount(@t)
 FOR @i = 1 TO @rowCount DO
 SET @title = Field(Row(@t,@i), "Value")
 SET @description = Field(Row(@d,@i), "Value")
 SET @link = Field(Row(@u,@i), "Value")
 SET @pubDate = Field(Row(@p,@i), "Value")
 SET @l = Length(@title)
 SET @colon = IndexOf(@title,':')
    IF IndexOf(@title,':') > 0 THEN
      SET @jt = Subtract(IndexOf(@title,':'),1)
    ENDIF
    IF IndexOf(@title,':') > 0 THEN
      SET @j = Substring(@title,1,Subtract(IndexOf(@title,':'),1))
    ENDIF
    IF IndexOf(@title,':') > 0 THEN
      SET @w = Substring(@title,Add(IndexOf(@title,':'),1))
    ENDIF
 ]%%
 Company: %%=v(@j)=%%<br>
 Job position: %%=v(@w)=%%<br>
 Description: %%=v(@description)=%%<br>
 URL: %%=v(@link)=%%<br>
 Date of publication: %%=v(@pubDate)=%%<br><br>
 %%[
  NEXT @i
  ENDIF
 ]%%
```
- First we start with counting characters in the title `Length(@title)`. 
- Next step is to find a position of colon in the title `IndexOf(@title,':')`. 
- Next, by using the Subtract function `Subtract(IndexOf(@title,':'),1)` get the number of characters in front of the colon character, which is company name.
- Then, by using the Substring function `Substring(@title,1,Subtract(IndexOf(@title,':'),1))` return the value of the `title` between the first character and the colon.
- Next, by using the Add function `Add(IndexOf(@title,':'),1)` get the number of characters in the `title` including the colon character.
- Then, by using the Substring function `Substring(@title,Add(IndexOf(@title,':'),1))` return the value of the `title` after the colon and space characters pair.

The rest is a basic value assigning to a variable.

### Output
```
Company: EMR
Job position: Interim Head of Ecommerce
Description: £65k - £79k pa + prorated: EMR: Six month FTC Head of Digital Trading and Development for well-known British retailer West Midlands
URL: https://jobs.example.com/job/409859/interim-head-of-ecommerce/?TrackID=8
Date of publication: Wed, 24 Oct 2018 18:29:00 +0000

Company: EMR
Job position: Digital Creative Director
Description: £100k - £120k pa: EMR: Our client is a 50-strong brand studio based in London who are on a mission to be the world's most progressive brand company and we're looking for a Creative Director to help them get there - by shaping brand for the future, through technology. London
URL: https://jobs.example.com/job/409918/digital-creative-director/?TrackID=8
Date of publication: Tue, 06 Nov 2018 12:04:00 +0000

Company: Brand Recruitment
Job position: Digital Marketing Executive - SEO focus
Description: £30k - £35k pa: Brand Recruitment: Digital Marketing Executive - SEO focus, Aylesbury - Are you a Digital Marketing Executive looking to develop their career and specialise in SEO?.. Aylesbury
URL: https://jobs.example.com/job/409916/digital-marketing-executive-seo-focus/?TrackID=8
Date of publication: Mon, 05 Nov 2018 17:10:00 +0000
```
