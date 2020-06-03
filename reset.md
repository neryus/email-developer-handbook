# Why we need all this CSS rules added to email head?

```
body {
	-ms-text-size-adjust: 100%;
}
```

*What it does?*

Windows Mobile Text Size Adjustment. Much like in OSX and iOS, small text is also resized on Windows Mobile, this rule set stops from resizing small text.

----
```
body {
	-webkit-text-size-adjust: 100%;
}
```

*What it does?*

WebKit Text Size Adjustment. WebKit looks for any text that happens to be sized smaller than 13px and increases it to that number, which can sometimes cause design issues in places intended for small text. Setting -webkit-text-size-adjust to none will prevent iOS platforms from resizing the text, but this method also prevents OSX applications like Safari from bumping the text size up - something that can cause issues for people who need the text size to be large. Setting -webkit-text-size-adjust to 100% seems to be the best of both worlds.

----
```
body {
	-webkit-font-smoothing: antialiased;
}
```

*What it does?*

----
```
body {
	-moz-osx-font-smoothing: grayscale;
}
```

*What it does?*

----
```
body {
	margin: 0 !important;
}
```

*What it does?*

Removes left and right margins from body element in Android 4.4 email client.

```
div[style*="margin: 16px 0"] {
	margin:0 !important;
}
```

*What it does?*

Removes top and bottom margin value from wrapper div element in Android 4.4 email client.

The issue explained in James White article. https://blog.jmwhite.co.uk/2015/09/19/revealing-why-emails-appear-off-centre-in-android-4-4-kitkat/

----
```
table, td {
	mso-table-lspace:0pt !important;
	mso-table-rspace:0pt !important;
}
```

*What it does?*

Stops Outlook from adding extra spacing to tables.

----
```
table {
	border-spacing: 0 !important;
	border-collapse: collapse !important;
	table-layout: fixed !important;
	margin: 0 auto !important;
}
table table table {
	table-layout: auto;
}
```

*What it does?*

Fixes webkit padding issue. Fix for Yahoo Mail table alignment bug. Applies table-layout to the first 2 tables then removes for anything nested deeper.

----
```
img{
	-ms-interpolation-mode: bicubic;
	display:block;
}
```

*What it does?*

Uses a better rendering method when resizing images in IE.

----
```
*[x-apple-data-detectors] {
	color: inherit !important;
	text-decoration: none !important;
	font-size: inherit !important;
	font-family: inherit !important;
	font-weight: inherit !important;
	line-height: inherit !important;
}
```

*What it does?*

A work-around for iOS meddling in triggered links.

----
```
.x-gmail-data-detectors,
.x-gmail-data-detectors *,
.aBn {
	border-bottom: 0 !important;
	cursor: default !important;
}
```

*What it does?*

A work-around for Gmail meddling in triggered links.

----
```
.a6S {
	display: none !important;
	opacity: 0.01 !important;
}

```

*What it does?*

Prevents Gmail from displaying a download button on large, non-linked images.

```
img.g-img + div {
	display: none !important;
}
```

*What it does?*

If the above doesn't work, add .g-img class to any image in question.

----
```

```

*What it does?*



----
