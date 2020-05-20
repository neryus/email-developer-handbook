# TBC

`-ms-text-size-adjust: 100%;`

*What it does?*

Windows Mobile Text Size Adjustment. Much like in OSX and iOS, small text is also resized on Windows Mobile, this rule set stops from resizing small text.

----
```-webkit-text-size-adjust: 100%;```

*What it does?*

WebKit Text Size Adjustment. WebKit looks for any text that happens to be sized smaller than 13px and increases it to that number, which can sometimes cause design issues in places intended for small text. Setting -webkit-text-size-adjust to none will prevent iOS platforms from resizing the text, but this method also prevents OSX applications like Safari from bumping the text size up - something that can cause issues for people who need the text size to be large. Setting -webkit-text-size-adjust to 100% seems to be the best of both worlds.

----
`-webkit-font-smoothing: antialiased;`

*What it does?*

----
`-moz-osx-font-smoothing: grayscale;`

*What it does?*
