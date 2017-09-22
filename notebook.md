## T-Online.de

The email client don't display the inlined border value. The workaround can be to use div element as parent with border style.



## Targeting Yahoo! Mail

To target only Yahoo! Mail use this media querry:

````
@media yahoo {
  .div1 {width:200px;}
}
````

## Hide content
`mso-hide:all` - Outlook (Word) clients, if there are nested tables this rule should be aplied to them too.

`display:none` - Generic (exept Outlook-Word, Yahoo).


## [SFR.fr](https://www.sfr.fr/cas/login?service=https%3A%2F%2Fwebmail.sfr.fr%2Fwebmail%2Fj_spring_cas_security_check#sfrintid=HH_Top) email client

To align `table` to center nest it inside `<div align="center">`, this email client ignore parent `td` aligned to center.

Email client don't like when `b` tag have nested span element, e.g. `<b><span style="color:#fbr843>Hello Mickey</span></b>` it will not change text to bold.

## [Orange.fr](https://id.orange.fr/auth_user/bin/auth_user.cgi?source_url=/auth_user/bin/auth_user.cgi&return_url=http://rms.orange.fr/mail/inbox%3f) web mail client

The vertical alignment of `TD` content works only if CSS property - `vertical-align` used. The client ignore `valign` attribute.

## [Mail.ru](https://e.mail.ru/login)

If the text size is big then `line-height` style property should be added, other wise the text will overlap.
