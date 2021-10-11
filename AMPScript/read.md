## Overview

AMPscript is a scripting language for Salesforce Marketing Cloud. The language is a server-side scripting that has been developed for a specific runtime environment (Salesforce Marketing Cloud), where scripts are interpreted and executed when the content is rendered.
AMPscript is a language in two parts: a syntax and library of functions.

### Fundamentals and Syntax
  
At the most basic level, AMPscript calls act as a placeholder for the data requested from Marketing Cloud or a data extension. These calls can appear in one of three basic forms.
- Inline AMPscript: `%%=LOWERCASE(Name)=%%`
- AMPscript block: `%%[ LOWERCASE(Name) ]%%`
- AMPscript tag:
```
<script runat=server language=ampscript>
   Lowercase(Name)
</script>
```

AMPscript can handle constant values, values from attributes and data extensions, and keywords. This example shows how to produce the same results for all three language elements.

- `'example@example.com'` note the quotes around the string constant
- `SubscriberEmail` this string returns the value of SubscriberEmail from a data extension, which conveniently is example@example.com
- `@EmailAddress` this variable holds the value assigned to it earlier in the AMPscript block, which would be example@example.com

AMPscript uses terms you're probably familiar with, such as IF, ELSEIF, ELSE, and ENDIF. Take a look at this example to see how to implement these conditions in your AMPscript.

```
<script runat=server language=ampscript>
   IF @region == '1' THEN
      SET @greeting = 'Bonjour!'
   ELSEIF @region == '2' THEN
      SET @greeting = 'Hola!'
   ELSE
      SET @greeting = 'Hi!'
   ENDIF
</script>
```

You can include as many ELSEIF statements as necessary for all conditions you need to evaluate.

You can also set up FOR loops in AMPscript to iterate over content as many times as necessary, This example sets applicable first name values for the number of included roles.

```
%%[FOR @Position = '1' TO @Position = @rowCount DO ]%%
   SET @FirstName = FirstName
%%[NEXT @Position]%%
```

And, of course, you can assign variables (declared as VAR) in AMPscript using SET.

```
%%[ VAR @text
    SET @text = "Hello, world!"
    Output(v(@text))]%%
```

Notice how the `Output()` function prints the value of the variable contained in the `v()`.

For email messages, remember that AMPscript processes the HTML body of the messages first (including any preheader), then the text body. The subject line goes last.

### AMPscript Functions

AMPscript uses functions-an extremely large number of functions. We divide functions into several different categories.

|AMPscript|What it does|
|---|----|
|API|Create SOAP API interactions|
|Contacts|Modify Maarketing Cloud contact information|
|Content|Modify Marketing Cloud content, such as text and images in email messages|
|Data Extension|Modify data in data extensions|
|Encryption|Encrypt and decrypt Marketing Cloud data|
|HTTP|Get, post, and modify HTTP information in Marketing Cloud|
|Math|Perform basic math functions|
|Microsoft Dynamic CRM|Interact with Microsoft Dynamic CRM data|
|Salesforce|Interact with Sales Cloud data in Marketing Cloud|
|Sites|Interact with CloudPages sites|
|Social|Interact with Social Forward functionality in Email Studio|
|String|Modify string information in Marketing Cloud|
|Utilities|Return and evaluate types of Marketing Cloud data|

### Personalization Strings

AMPscript offers some easy strings to pull information into content, email addresses, and other areas where you need to dynamically assign values. These personalization strings return data from Email Studio lists. Use AMPscript functions to return content from data extensions in other Marketing Cloud functions.

### Impression Tracking

AMPscript lets you determine which sections of an email message perform better in sends. Surround a piece of content-pulled in using the `ContentArea()` or `ContentAreaByName()` functions-with the `BeginImpressionRegion()` and `EndImpressionRegion()` functions, and use impression tracking reports to see how your content measure up.

### Example

AMPscript is usually used to pull data from data extensions using calls like `Lookup()` and `LookupRow()`. These functions look for data in specified data extensions and return fields based on the values you include in the functions. This example looks up purchases made by a contact identified by a member ID and returns any rows containing purchase information.

```
%%[ VAR @row
    SET @row = LookupRows("Purchases","MemberID",@memID)]%%
```

This example shows how to retrive a content area from Content Builder in an email message, using the key value.
```
%%=ContentBlockbyKey("myContentBlock")=%%
```

Once you retrieve that information, you can perform all manner of modifications and transformations to accomplish what you need.

<!--
### Attribute and Data Extension values

Functions and scripts reference subscriber attributes, email attributes and data extension column values as unquoted strings. If the attribute, data extension column, table, or relationship name includes a space or special character, or hyphen, enclose value in square brackets.

`[Data Extension Attribute Name]`  
`[Attribute-Name]`
-->
