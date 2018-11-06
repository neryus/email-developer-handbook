### The example of RSS feed
```
<rss xmlns:opensearch="http://a9.com/-/spec/opensearch/1.1/" xmlns:atom="http://www.w3.org/2005/Atom" version="2.0">
  <channel>
    <item>
      <title>EMR: Interim Head of Ecommerce</title>
      <description> £65k - £79k pa + prorated: EMR: Six month FTC Head of Digital Trading and Development for well-known British retailer West Midlands </description>
      <link>https://jobs.example.com/job/409859/interim-head-of-ecommerce/?TrackID=8</link>
      <pubDate>Wed, 24 Oct 2018 18:29:00 +0000</pubDate>
      <guid isPermaLink="true"> https://jobs.example.com/job/409859/interim-head-of-ecommerce/?TrackID=8 </guid>
    </item> 
    <item>
      <title>EMR: Digital Creative Director</title>
      <description> £100k - £120k pa: EMR: Our client is a 50-strong brand studio based in London who are on a mission to be the world's most progressive brand company and we're looking for a Creative Director to help them get there - by shaping brand for the future, through technology. London </description>
      <link>https://jobs.example.com/job/409918/digital-creative-director/?TrackID=8</link>
      <pubDate>Tue, 06 Nov 2018 12:04:00 +0000</pubDate>
      <guid isPermaLink="true"> https://jobs.example.com/job/409918/digital-creative-director/?TrackID=8 </guid>
    </item>
    <item>
      <title> Brand Recruitment: Digital Marketing Executive - SEO focus </title>
      <description> £30k - £35k pa: Brand Recruitment: Digital Marketing Executive - SEO focus, Aylesbury - Are you a Digital Marketing Executive looking to develop their career and specialise in SEO?.. Aylesbury </description>
      <link>https://jobs.example.com/job/409916/digital-marketing-executive-seo-focus/?TrackID=8</link>
      <pubDate>Mon, 05 Nov 2018 17:10:00 +0000</pubDate>
      <guid isPermaLink="true"> https://jobs.example.com/job/409916/digital-marketing-executive-seo-focus/?TrackID=8 </guid>
    </item>
  </channel>
</rss>
```

The AMPscript to retrieve content.
The challenge is to divide `<title>` element content into company and job position. The title element content pattern company name and job position is divided by colon and space.
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
      SET @q = Subtract(Length(@title),IndexOf(@title,':'))
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

#### Output
