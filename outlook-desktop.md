###The white horizontal line Outlook 2016

![The actual issue](http://i.imgur.com/Mf0qqHd.png)
![The fixed version](http://i.imgur.com/cOSDS7W.png)

The fix for this design/code was very simple - remove all height values from parent `TD` element.

The [Litmus thread](https://litmus.com/community/discussions/4990-outlook-2016-1px-horizontal-lines-showing-up-in-the-body) on this issue.

###Gap above images in Outlook 2013
![Gap above image](/screenshots/2016-05-17_155028.png?raw=true)

Very weird render of images in Outlook 2013 - this gap appears on images that height are less than 19px. On screen shot arrow is images, first arrow is 20px height, and second arrow is 17 px height. Outlook 2013 adding gap above for second arrow.

###Text cut off when wrapping around image in Outlook 2013, 2016
It cuts off the left side of the text only in Outlook 2013 and 2016. Here is how it looks like in Outlook:
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

### `cellspacing`
All Outlook desktop versions (Windows versions) and Lotus8 ignoring cellspacing value on table tag. No point to use them, better use nested table to create some space between elements.

After some more testing it seems that this is Internet Explorer issue. AOL, Gmail and Outlook.com ignoring cellspacing value only on Internet Explorer browser, but not Yahoo Mail.

### The Outlook 2007-2013 page break issue
The Word engine has a [document length limit of 22 inches](http://support.microsoft.com/kb/95109) or around 1800 pixels. When a document - an email, in this case - hits that length, Outlook inserts a page break to aid with document printing.
As one of the solutions would be divided container table to two tables and force Outlook to think that each table is a page.
Tested on Windows7 - Outlook2010


### `table-layout:fixed` issue
Another bug in Outlook '07, '10, '13 - when there are style rule `table-layout:fixed` on `table` element and `td`s don't have attribute `width` this application set different width for `td`s. But if add an empty `width` attribute to `td` it will set equal `td`s.

###Conditional comments

```
<!--[if mso]>
Outlook desktop conditional comment syntax
<![endif]-->
```

For more selective targeting we can use '**gte**', '**lte**', '**gt**', '**lt**' and a number of Outlook version.

- '**gte**' stands for greater than or equal to.
- '**lte**' stands for less than or equal to.
- '**gt**' and '**lt**' which stands for greater than or less than, respectively.

Outlook version numbers

* Outlook 2000 - Version 9
* Outlook 2002 - Version 10
* Outlook 2003 - Version 11
* Outlook 2007 - Version 12
* Outlook 2010 - Version 14
* Outlook 2013 - Version 15
* Outlook 2016 - Version 16

The [full list](http://www.slipstick.com/outlook/outlook-version-numbers/) of Outlook version numbers
