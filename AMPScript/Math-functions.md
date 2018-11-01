## Add
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
