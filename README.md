Collections of responsive HTML email tricks and hacks that works and been tested on Litmus and my own devices.

## WebKit media query

This media query only targets WebKit-supported email clients, which allows to use of modern techniques like HTML5, CSS3, animation, web fonts, and more. The best way to test this media query is to use Firefox vs. Safari/Chrome browsers.
```html
@media screen and (-webkit-min-device-pixel-ratio:0) {
  /* Insert styles here */
}
```

## Outlook desktop

###Gap above images in Outlook 2013
![Gap above image](/screenshots/2016-05-17_155028.png?raw=true)

Very weird render of images in Outlook 2013 - this gap appears on images that height are less than 19px. On screen shot arrow is images, first arrow is 20px height, and second arrow is 17 px height. Outlook 2013 adding gap above for second arrow.

###Text cut off when wrapping around image in Outlook 2013, 2016
It cuts off the left side of the text only in Outlooks 2013 and 2016. Here is how it looks like in Outlook:
![Text cut off](/screenshots/screenshot-litmus com 2016-04-11 17-21-32.jpg?raw=true)

The simple solution would be add alignment to parent table `align="left"`. This works well on my issue.
Courtesy of [Chris Clemente](http://www.informz.com/blog/template-design/quick-tip-fixing-outlook-2013-wrap-padding/)

The more sophisticated solution would be using `mso-table-rspace:Npt` property on style attribute, according to [Campaign Monitor blog post](https://www.campaignmonitor.com/forums/topic/7836/text-cut-off-when-wrapping-around-image-in-nested-table-outlook-2013/)

### DPI Scaling in Outlook 2007-2013

[Litmus thread] (https://litmus.com/community/discussions/151-mystery-solved-dpi-scaling-in-outlook-2007-2013)

[Campaign Monitor thread] (https://www.campaignmonitor.com/forums/post/30195/#p30195)

### Outlook 2013 additional bullet point

Unordered list in Outlook 2013 shows additional bullet point, no problem in all other email clients. To fix this add block element with non-breaking space, it can be `div` or `span`. Basically, the bullet points can't be the last piece in the table.

```html
<ul>
    <li>Phasellus viverra nulla ut metus varius laoreet.<br /><br /></li>
    <li>Aliquam lorem ante, dapibus in, viverra quis, feugiat a, tellus.</li>
    <li>Phasellus viverra nulla ut metus varius laoreet.</li>
    <li>Aliquam lorem ante, dapibus in, viverra quis, feugiat a, tellus.</li>
</ul>
<span style="display:none;">&nbsp;</span>
```

*Courtesy of [Peter Scher](https://www.campaignmonitor.com/forums/post/30101/#p30101)*

### cellspacing
All Outlook desktop versions (Windows versions) and Lotus8 ignoring cellspacing value on table tag. No point to use them, better use nested table to create some space between elements.

After some more testing it seems that this is Internet Explorer issue. AOL, Gmail and Outlook.com ignoring cellspacing value only on Internet Explorer browser, but not Yahoo Mail.

### clipping email
As everyone knows Outlook sometimes clip email because it's too big. I had this issue when was coding long email template and Outlook was clipping it at different point, depend from amount of content. My content was wrapped in main `<table width="100%">`, I divided that table in two main tables and it's working nice. I presume Outlook was thinking that another table is new page and that's why it was working.
Tested on Windows7 - Outlook2010

### Fixed table layout issue
Another bug in Outlook '07, '10, '13 - when there are style rule `table-layout:fixed` on `table` element and `td`s don't have attribute `width` this application set different width for `td`s. But if add an empty `width` attribute to `td` it will set equal `td`s. 


## Outlook.com p margin

Outlook.com adding *margin-bottom:1.35em* to every paragraph tag. So we will force Outlook to change this by adding this rule to our style block:

```css
.ExternalClass p {Margin-bottom:0 !important;}
```
Note
Margin should be capitalize, otherwise it will not work.

##Remove blue links in iOS

Fix automatic styling of auto-generated blue-lnks on Apple devices such as iPhone

Copy paste this small piece of code below in your style tag, both above and inside your @media query and that's it!

```css
a[x-apple-data-detectors] {
    color: inherit !important;
    text-decoration: none !important;
    font-size: inherit !important;
    font-family: inherit !important;
    font-weight: inherit !important;
    line-height: inherit !important;
}
```
*Update* It's enough to put this code only twice - one in styles and another in WebKit media query, tested and it works.

*Courtesy of [removebluelinks.com](http://removebluelinks.com)*

##Gmail

`TABLE` background colour

Gmail is showing table background colour only on space that have content and it depends how much content there are. To force gmail rendering engine to show background colour on whole table add `bgcolor=""` to parent `TD`.

##Gmail App Zooming

Stop Gmail app from zooming text.

```
    style="min-width:600px"
```

*Courtesy of [Chriss Wise](http://chriswi.se/)*

##Gmail App p margin

Stop Gmail App from adding margin-top and margin-bottom.

```
    margin:0px;
```

##Gmail white line under image

To stop appear white line below image add `display:block` to image styles.

##Email size does matter atleast on Gmail
If your email exceeds 102KB, Gmail will display the first 102KB and then it will clip off the remainder with a few different variations depending on the device. Image sizes are not counted, but all comments are. Full article on [Email on Acid](https://www.emailonacid.com/blog/article/email-development/when_it_comes_to_html_email_size_does_matter/)

##Line height
A classic rule-of-thumb is 1.5x the size of body copy. The wider your measure the more generous you can be with the line height. Jason Santa Maria [explains](https://vimeo.com/34178417#t=28m14s) "As your eye gets to the end of a long line of text it needs that cushion to get to the next one without getting lost... if your lines are shorter you can pack them in a little tighter".
Very good research on this made [Style Campaign](http://stylecampaign.com/blog/2015/07/typographic-patterns-in-email/)

##Android native email client
Good examples of [Android versions](https://www.emailonacid.com/blog/article/email-development/how_android_is_strangling_responsive_design) that strip Doctype from HTML document.

##Windows Phone

### IE=Edge meta tag
This meta tag `<meta http-equiv="X-UA-Compatible" content="IE=edge" />` in the head of HTML file makes media queries work on Windows Phone 7.5 and higher. More about this on [Campaign Monitor forum](https://www.campaignmonitor.com/forums/topic/7989/windows-phone-8-has-full-css3media-query-support/)

### Address blue colour

Any ideas?

