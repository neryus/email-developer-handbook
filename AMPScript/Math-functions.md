## Add()
This function returns the sum of two numbers.

### Arguments
`Add(1,2)`

| Ordinal | Type | Required | Description |
| ------- | :--- | :------- | :---------- |
| 1 | Number | True | First value |
| 2 | Number | True | Second value |

### Example 1
```
%%[
VAR @sum, @n1, @n2
SET @n1 = 9
SET @n2 = 33

SET @sum = Add(@n1,@n2)
]%%
%%=v(@n1)=%% + %%=v(@n2)=%% = %%=v(@sum)=%%
```

#### Output
```
9 + 33 = 42
```

## Mod()
This function returns the remainder after dividing one number by another (also known as a modulo operation).

### Arguments
`Mod(1,2)`

| Ordinal | Type | Required | Description |
| ------- | :--- | :------- | :---------- |
| 1 | Number | True | Value to be divided |
| 2 | Number | True | Value to divide by |

NOTE: This function will return a decimal if either parameter is a decimal.

### Example 1
```
%%[
var @modulus, @n1, @n2

set @n1 = 19
set @n2 = 4

set @modulus = mod(@n1, @n2)
]%%

%%=v(@n1)=%% / %%=v(@n2)=%% = %%=v(@modulus)=%%
```

#### Output
```
19 / 4 = 3
```

### Example 2 - From the real world.

The task is to display content from the XML feed in the HTML table 3-column grid.
One thing that we don't know is how many content items will be on the feed. If there are more than 2 content items, then the third item should go onto a new table row and so on. The middle cell is used as fake divider between cells with content.

```
<table border="1" style="table-layout:fixed; width:450px;">
    <tr>
%%[
SET @cell = 0 
SET @rowCount = 5 /* Try to change digit to even to see the result */
    IF @rowCount > 0 THEN
       FOR @i = 1 TO @rowCount DO
         SET @cell = Add(@cell, 1)
          IF @i == @rowCount THEN
              output(concat("<td>This is the last item: (", @cell,")</td>"))
          ELSEIF mod(@i,2) == 0 THEN
              output(concat("<td>The cell number is even (", @i,")</td></tr><tr>"))
          ELSE
              output(concat("<td>The cell number is odd (", @i,")</td><td>The empty cell</td>"))
          ENDIF
       NEXT @i
    ELSE ENDIF
]%%
    </tr>
</table>
```

#### HTML Output

```
<table border="1" style="table-layout:fixed; width:450px;">
  <tr>
    <td>The cell number is odd (1)</td>
    <td>The empty cell</td>
    <td>The cell number is even (2)</td>
  </tr>
  <tr>
    <td>The cell number is odd (3)</td>
    <td>The empty cell</td>
    <td>The cell number is even (4)</td>
  </tr>
  <tr>
    <td>This is the last item: (5)</td>
  </tr>
</table>
```
