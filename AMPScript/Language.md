# Overview

AMPscript is a scripting language for Salesforce Marekting Cloud. You can use it create highly sophisticated, personalized content through an extensive set of functions. The language follows a simple syntax and semantics, making it quick to learn and easy to code.

AMPscript is a server-side scripting language that has been developed for a specific runtime environment (Salesfroce Marketing Cloud), where scripts are interpreted and executed when the content is rendered.

AMPscript is a language in two parts: a syntax and library of functions. With an understanding of these, it's possible to quickly gain proficiency in the language, without prior programming or scripting experience, and create highly personalized, dynamic content for direct marketing campaigns.

## Syntax

As AMPscript is a server-side language, the code can be included in any location in an email, web page, SMS or push message. Similar to other scripting languages, AMPscript is interpreted and not compiled, which means that it's interpreted in the order it is written. So if you are using AMPscript to include personalized content in an email, the AMPscript code will need to be defined before or at the point where the personalized content should appear.

AMPscript code is contained within a character sequence that opens and closes with double percentage marks `%%` and either contains an inner bracket delimiter `[` and `]`, for AMPscript blocks, or an equality character `=`, for inline AMPscript. All AMPscript code must be surrounded by matching opening and closing delimiter patterns, otherwise the code will be ignored.

## Characters

| Characters | Purpose |
|------------|---------|
|`%%`|The starting and ending point for all AMPscript.|
|`%%= describe what you want here =%%`|Indicates the beginning and ending of inline AMPscript, which displays the return value of the function referenced. Basically, you identify the info you want to be displayed.|
|`%%[ describe what you want and the steps on how to get what you want =%%`|Indicates the beginning and ending of an AMPscript code block. An AMPscript block can do a bit more than inline, as it can have multiple steps. It can help declare and set variable alues. It can also help process conditional logic.|
|`" "`|Used to define a literal item, for example a data extension name, a column name, or a data point.|
|`(m == money and money == good)`|Parentheses identify an order of group operations within the code.|
|`(@money)`|The @ symbol shows us what we are looking for. In this example, money.|
|`v(@allthemoney)`|This refers to the value of a variable found in your data.|

## Comments

Comments can be included in AMPscript blocks. They are contained within an opening `/*` and closing `*/` syntax pair and provide the ability to include a readable explanation or annotation for users. Any comments are ignored by Marketing Cloud and will not be interpreted. They can be used on a single line or traverse multipled lines.

`/* Comment */`

## Operators

|Comparison operators| |
|---|----|
|`==`|Is equal to|
|`!=`|Is not equal to|
|`>` or `>=`|Greater than ot greater that or equal to|
|`<` or `<=`|Less than or less than or equal to|

|Join operators| |
|---|----|
|`AND`|In order for the condition to be true, both expressions must evaluate to true.|
|`OR`|In order for the condition to be true either of the expressions must evaluate to true.|

|Conditional operators| |
|---|----|
|`IF, ELSEIF, ELSE, ENDIF`|These terms are used to define data or narrow down results based on set criteria.|
