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
