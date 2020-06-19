## HTTPGet ##

This function returns the content from a specified publicly accessible URL.

Note: The function only works with HTTP content on TCP/IP port 80 and HTTPS on port 443. Basic access authentication in URLs is not supported (for example, `https://username:password@https://dpmain.com`).

Note 2: Marketing Cloud honors any character set returned in the HTTP headers via Content Type. For example, you can use a UTF-8 encoded HTML file with **Content-Type: text/html; charset=utf-8** included in the header. If the encoding is not specified in the header, the application assumes all returned data will be in the character set **WindowsCodePage 1252**. You can change this default by contacting your Marketing Cloud account rep.

### Syntax ###

`HTTPGet(1,2,3,4)`

### Function Porperties ###

Ordinal | Type | Required | Description
------- | ---- | -------- | -----------
1       | string  | yes    | URL from which ttto return content
2       | boolean | | Defines whether the process continues on error. Defaults to false. A value of true ignores errors in process.
3       | int     | | Defines whether the function allows empty content. A value of 0 allows for empty content. A value of 1 returns an error. A value of 2 skips the subscriber.
4       | string  | | Output of function status. This function defaults to 0. A value of 0 indicates status is OK. A value of -1 indicates a missing URL. A value of -2 indicates an HTTP request error. A value of -3 indicates empty content; the function completed successfully but did not return any content.

### Example 1 ###

`%%httpget "https://httpbin.org/html"%%`

### Output ###

This string will output the content from the URL on the landing page:
```
<!DOCTYPE html>
<html>
  <head>
  </head>
  <body>
      <h1>Herman Melville - Moby-Dick</h1>
      <div>
        <p>
          Availing himself of the mild, summer-cool weather that now reigned in these latitudes, and in preparation for the peculiarly active pursuits ... Hadst thou taken this old blacksmith to thyself ere his full ruin came upon him, then had the young widow had a delicious grief, and her orphans a truly venerable, legendary sire to dream of in their after years; and all of them a care-killing competency.
        </p>
      </div>
  </body>
</html>
```
