* [IndexOf](#indexof)
* [Length](#length)
* [Substring](#substring)
* [Subtract](#subtract)

## IndexOf

This function returns the position of the first occurrence of a specified value in a string. The index numbering starts at 1.

### Arguments

`IndexOf(1,2)`

| Ordinal | Type | Required | Description |
| ------: | ---- | -------- | :---------- |
| 1 | String | True | String to search |
| 2 | String | True | String value to find |

### Example
```
%%[
var @title, @colon
set @title = 'EMR: Visual Content Designer - Luxury Student Accommodation'

set @colon = IndexOf(@title,':') 
]%%
title: %%=v(@title)=%%<br>
colon position: %%=v(@colon)=%%
```

#### Output
```
title: EMR: Visual Content Designer - Luxury Student Accommodation
colon position: 4
```

## Length

This function returns the number of characters in the specified string.

### Argument

`Length(1)`

| Ordinal | Type | Required | Description |
| ------: | ---- | :------- | :---------- |
| 1 | String | True | String to measure |

### Example

```
%%[
var @title, @l

set @title = 'Asahi UK: Insights Manager'
set @l = Length(@title)
]%%
title: %%=v(@title)=%%<br>
title length: %%=v(@l)=%%
```

#### Output

```
title: Asahi UK: Insights Manager
title length: 26
```

## Substring

This function returns a portion of the specified string starting at a certain character position and no longer than the specified length. If the specified character position is more than the length of the specified string, the function returns an empty string.

### Arguments

`Substring(1,2,3)`

| Ordinal | Type | Required | Description |
| ------: | ---- | :------- | :---------- |
| 1 | String | True | The string from which to extract a portion |
| 2 | Number | True | Starting position of substring |
| 3 | Number | False | Length of substring |

### Example 1

Returns the value of string in front of the specified character.
```
%%[
VAR @title 
SET @title = "Brand Recruitment: SEO Specialist" /* literal value */

IF IndexOf(@title,':') > 0 THEN
  SET @j = Substring(@title,1,Subtract(IndexOf(@title,':'),1))
ENDIF
]%%
%%=v(@j)=%%
```

#### Output

```
Brand Recruitment
```

### Example 2
Returns the value of string found after the specified character.
```
%%[
VAR @title, @w
SET @title = "Better Placed: SEO Account Manager"

IF IndexOf(@title,':') > 0 THEN
    SET @w = Substring(@title, Add(IndexOf(@title,':'),1))
ENDIF
]%%
%%=v(@w)=%%
```

#### Output
```
SEO Account Manager
```

## Subtract

This function returns the difference between two numbers.

### Arguments

`Subtract(1,2)`

| Ordinal | Type | Required | Description |
| ------: | ---- | :------- | :---------- |
| 1 | Number | True | First value |
| 2 | Number | True | Second value |


### Example 1

```
%%[
VAR @n1, @n2, @d
SET @n1 = 19
SET @n2 = 7

SET @d = Subtract(@n1, @n2)
]%%
%%=v(@n1)=%% - %%=v(@n2)=%% = %%=v(@d)=%%
```

#### Output

```
19 - 7 = 12
```

### Example 2

The example counts characters in the string (including the space between words).

```
%%[
VAR @jt, @title
SET @title = "Brand Recruitment: Online Marketing Specialist"

SET @jt = Subtract(IndexOf(@title,':'),1)
]%%
%%=v(@jt)=%%
```

#### Output

```
17
```

### Example 3

The example counts characters find after the specified character in the string (including the spaces).

```
%%[
VAR @title, @q
SET @title = "Brand Recruitment: PR and Social Media Manager"

SET @q = Subtract(Length(@title), IndexOf(@title, ':'))
]%%
%%=v(@q)=%%
```

#### Output

```
28
```
