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
