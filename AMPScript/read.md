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

<!--
### Attribute and Data Extension values

Functions and scripts reference subscriber attributes, email attributes and data extension column values as unquoted strings. If the attribute, data extension column, table, or relationship name includes a space or special character, or hyphen, enclose value in square brackets.

`[Data Extension Attribute Name]`  
`[Attribute-Name]`
-->
