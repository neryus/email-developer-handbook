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


## Sentence

The code examples all accomplish the same thing: A customer’s favorite color displays in lowercase in the sent email, even if the data is stored in all caps per the sample data in this chart.

| Style type | Sample code | When to use | Where to use |
|------------|-------------| ----------- | ------------ |
| Inline AMPscript | `%%=LOWERCASE(FavoriteColor)=%%` | Simple output | Free Form blocks, code snippet blocks, HTML content blocks |
| AMPscript block  | `%%[Output(LOWERCASE(FavoriteColor))]%%` | More complex code with miltiple steps or conditional logic | Code snippet blocks, HTML content blocks |
| AMPscript tag    | `<script runat=server language=ampsript> Output(LOWERCASE(FavoriteColor))</script>` | More complex code with multiple steps or conditional logic. Use if you are more familiar with web script syntax (Javascript) | Code snippet blocks, HTML content blocks |

## Comments

Comments can be included in AMPscript blocks. They are contained within an opening `/*` and closing `*/` syntax pair and provide the ability to include a readable explanation or annotation for users. Any comments are ignored by Marketing Cloud and will not be interpreted. They can be used on a single line or traverse multipled lines.

`/* Comment */`

## Values

One of the core language elements of AMPscript are values, which can be either variables, constants, or attributes.

### Variables

A variable is a storage location for the information you want to reference later within a script statement or function. Variable names must begin with @ and include at least one other letter, number, or underscore. For example: `@firstName` or `@first_Name`. Note that spaces and commas aren’t allowed in a variable name.
Variables are declared in your code by using the keyword `VAR` followed by one or more comma-delimited variable name(s). Once declared, variables are assigned using the keyword `SET` followed by the variable name, equal sign, and value. A variable’s value can be a constant or an attribute.

#### Defining Variables

How the code elements work together to define and set variables.
|Code|What it does|
|--|--|
|`VAR @cats`|Defines the placeholders.|
|`SET @cats = breed`|Define a value from a sendable data extension.|
|`SET @cats = "tabby"`|Set a specific or literal value.|
|`%%=v(@cats)=%%`|Inline AMPscript used in your email content to return the value.|

Note if the data extension field name has a space in it, the field name needs to be contained in square brackets. Example `SET @fname = [First name]`

### Constants and Attributes

| Value type | Description | Code example |
|---|---|---|
| Constant |A constant is a value that cannot be altered by the system. It is what it is when it is set. These can be numeric, string, Boolean, or null values.|`%%[ VAR @firstName SET @firstName = "Susan" ]%%`|
| Attribute |Attributes (or data extension values) refer to any content held inside a subscriber list or a data extension. They are recognized as unquoted strings. Values that have a space or special character require opening and closing brackets. Therefore it is best practice to include opening and closing brackets around all values for consistency and troubleshooting.|`%%[ VAR @firstName SET @firstName = [First Name] ]%%`|

## Operators

A key component of AMPscript is the ability to compare and add data into an email. AMPscript uses common operators for data comparison criteria, like greater than, equal to, and so on.

|Comparison operators| |
|---|----|
|`==`|Is equal to|
|`!=`|Is not equal to|
|`>` or `>=`|Greater than ot greater that or equal to|
|`<` or `<=`|Less than or less than or equal to|

Comparison operators are controlled in AMPscript by using parentheses. So if you are looking for a new orange tabby cat or kitten, your comparison operators might be: (Cat AND Orange) OR (Kitten AND Orange).

|Join operators| |
|---|----|
|`AND`|In order for the condition to be true, both expressions must evaluate to true.|
|`OR`|In order for the condition to be true either of the expressions must evaluate to true.|

### Conditional operators

These terms are used to define data or narrow down results based on set criteria.

| Operator | Additional Info |
|---|----|
|`IF`|To perform conditional processing.|
|`ELSEIF`|Multiple ELSEIF statements can appear within an IF block.|
|`ELSE`|Only one ELSE statement can appear within an IF block.|
|`ENDIF`|Use the ENDIF statement to end an IF block. Only one ENDIF statement must appear at the end of an IF block.|

#### Example Code

Let’s see an example of how the IF syntax would be used to set a default first name for a customer whose first name is missing in your data.

```
%%[ VAR @firstName
SET @firstName = [First Name]
IF Empty(@firstName) THEN
SET @firstName = "NTO Rockstar"
ENDIF
]%%
```

Note. AMPscript is not case sensitive, however, it is a good idea to pick a standard and be consistent in your code.

##  AMPscript Functions

The previous language elements are all used within functions. Functions are self-contained modules of code that accomplish specific tasks. Functions usually take in data, process it, and return a result. For example, the function `%%=Format(@price, "C", 'en-US')=%%` updates a product’s price to reflect the proper formatting for US currency.

Functions are written like this: `FunctionName(X)`
- FunctionName: A unique name that describes the function.
- ( ): Opening and closing parentheses.
- X: The parameters being evaluated. If there are multiple, they are separated by commas, like 1, 2, 3.

Functions can accept variables, constants, and attributes as parameters between the parentheses.
AMPscript doesn’t support the creation of custom functions, there are plenty of built-in functions that can be easily added to your code.

### Common AMPscript functions

#### Date funcions
- [FormatDate(1,2,3,4)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/FormatDate.html)
- [DateAdd(1,2,3)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/DateAdd.html)
- [DateDiff(1,2,3)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/DateDiff.html)

Note that Marketing Cloud’s system time is central standard time, and it does not adjust for daylight saving time.

#### Math functions
- [Add(1,2)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/Add.html)
- [Subtract(1,2)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/Subtract.html)
- [Multiply(1,2)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/Multiply.html)
- [Divide(1,2)](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/Divide.html)

[Full list](https://developer.salesforce.com/docs/marketing/marketing-cloud/guide/functions.html) of AMPscript functions. 
