* [Windows 10 Mail](#windows-10-mail-link-underline)
* [T-Online](#t-onlinede-border-issue)
* [Yahoo Mail](#targeting-yahoo-mail)
* [SFR.fr](#sfrfr-email-client)
* [Orange.fr](#orangefr-web-mail-client)
* [Mail.ru](#mailru)

## Windows 10 Mail link underline

W10 Mail email client displays underline even the 'text-decoration:none' is defined inline for links.
![Imgur](https://i.imgur.com/uEO1vEN.png)

The solution is to add global styles declaration for Outlook specific styles by targeting Windows 10 Mail client:
```html
<!--[if (mso 16)]>
<style type="text/css">
a{text-decoration:none;}
</style>
<![endif]-->
```

## Windows 10 Mail body background

For this email client the background colour value should be set on container `table` instead of the `body` element.

## T-Online.de border issue

The email client don't display the inlined border value. The workaround can be to use div element as parent with border style.
Update. The border value is not displayed for `table` element, but it displayed for `td` element.
![T-Online.de](https://i.imgur.com/vBcIjgC.png)
![Web.de](https://i.imgur.com/tYYxO3i.png)


## Targeting Yahoo! Mail

To target only Yahoo! Mail use this media querry:

```css
@media yahoo {
  .div1 {width:200px;}
}
```

## Hide content
`mso-hide:all` - Outlook (Word) clients, if there are nested tables this rule should be aplied to them too.

`display:none` - Generic (exept Outlook-Word, Yahoo).


## [SFR.fr](https://www.sfr.fr/cas/login?service=https%3A%2F%2Fwebmail.sfr.fr%2Fwebmail%2Fj_spring_cas_security_check#sfrintid=HH_Top) email client

The email client don't align to center a `table` element (fixed width or no width values) if `align="center"` is placed inside a `table` or a parent `td`, this affect Firefox and Chrome, the Explorer apply this value. To align `table` to center nest it inside centered `div` element.

Email client don't like when `b` tag have nested span element, e.g. `<b><span style="color:#fbr843>Hello Mickey</span></b>` it will not change text to bold.

## [Orange.fr](https://id.orange.fr/auth_user/bin/auth_user.cgi?source_url=/auth_user/bin/auth_user.cgi&return_url=http://rms.orange.fr/mail/inbox%3f) web mail client

The vertical alignment of `TD` content works only if CSS property - `vertical-align` used. The client ignore `valign` attribute.

## [Mail.ru](https://e.mail.ru/login)

If the text size is big then `line-height` style property should be added, other wise the text will overlap.
