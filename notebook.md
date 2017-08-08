## [SFR.fr](https://www.sfr.fr/cas/login?service=https%3A%2F%2Fwebmail.sfr.fr%2Fwebmail%2Fj_spring_cas_security_check#sfrintid=HH_Top) email client

Web mail client don't like the `table` without width values, it not aligns them to the center or right.

Email client don't like when `b` tag have nested span element, e.g. `<b><span style="color:#fbr843>Hello Mickey</span></b>` it will not change text to bold.

## [Orange.fr](https://id.orange.fr/auth_user/bin/auth_user.cgi?source_url=/auth_user/bin/auth_user.cgi&return_url=http://rms.orange.fr/mail/inbox%3f) web mail client

The alignment styles should be added to `style` attribute to make `table` aligned to center or right. It ignore the `align` attribute.
