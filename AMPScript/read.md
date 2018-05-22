## Overview

AMPscript is a scripting language for Salesforce Marketing Cloud. The language is a server-side scripting that has been developed for a specific runtime environment (Salesforce Marketing Cloud), where scripts are interpreted and executed when the content is rendered.
AMPscript is a language in two parts: a syntax and library of functions.

## Syntax

### Attribute and Data Extension values  
Functions and scripts reference subscriber attributes, email attributes and data extension column values as unquoted strings. If the attribute, data extension column, table, or relationship name includes a space or special character, or hyphen, enclose value in square brackets.

`[Data Extension Attribute Name]`  
`[Attribute-Name]`
