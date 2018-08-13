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
