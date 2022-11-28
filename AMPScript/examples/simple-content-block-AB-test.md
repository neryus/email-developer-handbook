## Code Example

The aim is to run a simple A/B content block test - for data extension 'AB Test Value' data flag 'A' display one content block and for flag 'B' display another one, if data flag is empty don't display anything.

*Note that data flag is embedded into square brackets because it has spaces in the name.*

```
%%[
IF [AB Test Value] == 'A' THEN 
]%%
%%=ContentBlockByID("117590")=%%
%%[ 
ELSEIF [AB Test Value] == 'B' THEN
]%%
    %%=ContentBlockByID("119272")=%%
%%[
ELSE
]%%
%%[
ENDIF
]%%
```
