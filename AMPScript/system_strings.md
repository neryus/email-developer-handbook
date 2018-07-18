# System Strings #

The library of system-based personalization strings which can be used in a message or on a page to output a value, based on the context of the Subscriber, Contact or a message.

## Subscriber Data Strings ##

String | Description | Example Output
------ | ----------- | --------------
`_listname` | The user-defined list name (publication list); returns the empty value if the All Subscribers list is used, returns the All Subscribers for test emails. | `Newsletter`
`emailaddr` | The email address of the subscriber. | `name.surname@domain.com` 
`memberid` | Business unit ID in the Exact Target. | `1234567` 
