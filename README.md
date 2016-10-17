Collections of responsive HTML email tricks and hacks that works and been tested on Litmus and my own devices.

##Why we need to have image attribute `width` and we can't have instead `max-width` property?
These versions of Outlook don't read `style` properties and that's why we need to have `width` attribute for images.

* Outlook 2007
* Outlook 2010
* Outlook 2013
* Windows 10 Mail
 
## WebKit media query

This media query only targets WebKit-supported email clients, which allows to use of modern techniques like HTML5, CSS3, animation, web fonts, and more. The best way to test this media query is to use Firefox vs. Safari/Chrome browsers.
```html
@media screen and (-webkit-min-device-pixel-ratio:0) {
  /* Insert styles here */
}
```

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

#Gmail

##[Gmail supports CSS and media queries](https://developers.google.com/gmail/design/css)
*Last updated October 17, 2016*

Gmail supports queries agains the screen width, orientation, and resolution.
Supported types

- all
- screen

Supported queries

- min-width
- max-width
- min-device-width
- max-device-width
- orientation
- min-resolution
- max-resolution

Supported keywords

- and
- only

Full list of supported [CSS properties](https://developers.google.com/gmail/design/reference/supported_css).

List of supported [email markup](https://developers.google.com/gmail/markup/) by Gmail, like [highlights](https://developers.google.com/gmail/markup/overview#highlights_in_inbox), [actions](https://developers.google.com/gmail/markup/overview#gmail_actions), [answers](https://developers.google.com/schemas/search/answers), [confirmation cards](https://developers.google.com/schemas/now/cards).

This will take effect for Webmail users, but not for mobile because the end user needs to update software and not everyone will update it immediately. So this is not a good time to get rid of all Gmail markup/style tricks.

##`TABLE` background colour

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

##Email size does matter at least on Gmail
If your email exceeds 102KB, Gmail will display the first 102KB and then it will clip off the remainder with a few different variations depending on the device. Image sizes are not counted, but all comments are. Full article on [Email on Acid](https://www.emailonacid.com/blog/article/email-development/when_it_comes_to_html_email_size_does_matter/)

##Line height
A classic rule-of-thumb is 1.5x the size of body copy. The wider your measure the more generous you can be with the line height. Jason Santa Maria [explains](https://vimeo.com/34178417#t=28m14s) "As your eye gets to the end of a long line of text it needs that cushion to get to the next one without getting lost... if your lines are shorter you can pack them in a little tighter".
Very good research on this made [Style Campaign](http://stylecampaign.com/blog/2015/07/typographic-patterns-in-email/)

##Android native email client
Good examples of [Android versions](https://www.emailonacid.com/blog/article/email-development/how_android_is_strangling_responsive_design) that strip Doctype from HTML document.

#Windows Phone

###IE=Edge meta tag
This meta tag `<meta http-equiv="X-UA-Compatible" content="IE=edge" />` in the head of HTML file makes media queries work on Windows Phone 7.5 and higher. More about this on [Campaign Monitor forum](https://www.campaignmonitor.com/forums/topic/7989/windows-phone-8-has-full-css3media-query-support/)

###Email clients that don't inherit font-family property
- Outlook 2007
- Outlook 2010
- Outlook 2013
- Outlook 2016
- Windows 10 Mail

