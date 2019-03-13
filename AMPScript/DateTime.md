### DateAdd

This function returns a date with the specified number interval added to the specified part of the date.

#### Syntax
`DateAdd(1,2,3)`

#### Function Properties
| Ordinal | Type | Required | Description |
| :------ | :--- | :------- | :---------- |
| 1 | Date | True | The date to adjust |
| 2 | Number | True | The interval to add |
| 3 | String | True | The part of the date to adjust by the preceding interval. Valid values include `Y`, `M`, `D`, `H`, and `MI` |

#### Example
```
%%=DateAdd(Now(),1,'D')=%%
```
#### Output
The system returns tomorrow's date, alogn with a time stamp.
