## IndexOf ##

This function returns the position of the first occurrence of a specified value in a string. The index numbering starts at 1.

### Arguments ###

`IndexOf(1,2)`

| Ordinal | Type | Required | Description |
| ------: | ---- | -------- | :---------- |
| 1 | String | True | String to search |
| 2 | String | True | String value to find |

### Example ###

```
%%[
var @title, @colon

set @title = 'EMR: Visual Content Designer - Luxury Student Accommodation'

set @colon = IndexOf(@title,':') 
]%%

title: %%=v(@title)=%%<br>
colon position: %%=v(@colon)=%%
```

### Output ###

```
title: EMR: Visual Content Designer - Luxury Student Accommodation
colon position: 4
```

## Length ##

This function returns the number of characters in the specified string.

### Argument ###

`Length(1)`

| Ordinal | Type | Required | Description |
| ------: | ---- | :------- | :---------- |
| 1 | String | True | String to measure |

### Example ###

```
%%[
var @title, @l

set @title = 'Asahi UK: Insights Manager'
set @l = Length(@title)
]%%
title: %%=v(@title)=%%<br>
title length: %%=v(@l)=%%
```

### Output ###

```
title: Asahi UK: Insights Manager
title length: 26
```

## Substring ##

This function returns a portion of the specified string starting at a certain character position and no longer than the specified length. If the specified character position is more than the length of the specified string, the function returns an empty string.

### Arguments ###

`Substring(1,2,3)`

| Ordinal | Type | Required | Description |
| ------: | ---- | :------- | :---------- |
| 1 | String | True | The string from which to extract a portion |
| 2 | Number | True | Starting position of substring |
| 3 | Number | False | Length of substring |

### Example ###

```
%%[
VAR @title 
SET @title = "Brand Recruitment: SEO Specialist" /* literal value */

/* Returns the value of string in front of the colon */
IF IndexOf(@title,':') > 0 THEN
  SET @j = Substring(@title,1,Subtract(IndexOf(@title,':'),1))
ENDIF
]%%
%%=v(@j)=%%
```

#### Output ####

```
Brand Recruitment
```
