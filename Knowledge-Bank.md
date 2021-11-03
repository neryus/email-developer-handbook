## Email Client

*Last updated: 18 Aug, 2021*

Email client is an application that enables onfiguring one or more email adresses to receive, read, compose and send emails from that email address through user interface.
Email client is also known as email reader or mail user agent (MUA).

Source: [Technopedia](https://www.techopedia.com/definition/1656/email-client)

## Mailto attribute

*Added: 3 Nov, 2021*

Mailto links are used to redirect the user to an email address instead of a link. When the user clicks on a mailto link, the default email client opens on the user's computer and suggests sending an email to the address included in the mailto link.

### Create mailto links in HTML

You can create an HTML mailto link by using an anchor tag with the href attribute and inserting the 'mailto' parameter after it. Clicking on the link will open a new default email software window.

```
<a href="mailto:nerijus@paukste.com">Email Nerijus</a>
```

If you want to send an email to more than one address, separate your email address with a comma:

```
<a href="mailto:nerijus@paukste.com, paukste@nerijus.com">Send email</a>
```

### Mailto parameters

The mailto attribute accepts seven parameters, as described below:
|Parameter|Required|Description|
|-|-|-|
|mailto|Required|This parameter specifies the email address of the recipient.|
|cc|Optional|this parameter is used to add another email address that will receive the mail's copy.|
|bcc|Optional|This parameterspecifies another email that will receive the blnd carbon copy of the email.|
|subject|Optional|This parameter is used to fill the subject of the email.|
|body|Optional|This parameter is used to fill the content of the email.|
|?|Optional|This parameter is the first parameter delimeter.|
|&|Optional|This holds the other parameter delimeter.|

```
<a href="mailto:nerijus@paukste.com?cc=paukste@nerijus.com&subject=Hello World&body=What a great day!">Send your feedback by email</a>
```

Source: [simplilearn.com](https://www.simplilearn.com/tutorials/html-tutorial/html-mailto)

<!--## Heading

*Last updated: timestamp*

Copy

Source: []()-->
