# System Strings #

The library of system-based personalization strings which can be used in a message or on a page to output a value, based on the context of the Subscriber, Contact or a message.

## Email URL Data Strings ##

String | Description | Example Output
------ | ----------- | --------------
`unsub_center_url` | URL of the Subscriber's One-Click Unsubscribe page | `http://pub.s6.exacttarget.com/unsub_center.apsx?qs=...`
`view_email_url` | `URL to view the email` | `http://view.s6.exacttarget.com?qs=...`

## Subscriber Data Strings ##

String | Description | Example Output
------ | ----------- | --------------
`%%_listname%%` | The user-defined list name (publication list); returns the empty value if the All Subscribers list is used, returns the All Subscribers for test emails. | `Newsletter`
`%%emailaddr%%` | The email address of the subscriber. | `name.surname@domain.com` 
`%%memberid%%` | Business unit ID in the Exact Target. | `1234567` 

## Date strings ##

Note. The date string use the sytem time (the data center location of MC account) and appear in US format. These values can be transformed using AMPscript date functions.

String | Description | Example Output
------ | ----------- | --------------
`%%xtyear%%` | Current year when the email was sent. | `2018`
`%%xtmonth%%` | Full name of the month when email is sent. | `February`
`%%xtmonthnumeric%%` | Current month as a number. | `2`
`%%xtday%%` | Current day of the month when the email was sent. | `29`
`%%xtdayofweek%%` | Current day of the week when the email was sent. | `Monday`
`%%xtshortdate%%` | Current date when the email wassent in short format, month/day/year. | `02/29/2018`
`%%xtlongdate%%` | Current date when the email was sent in long format, day of week, month day, year. | `Monday, February 29, 2018`
