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

#### Example 1
```
%%=DateAdd(Now(),1,'D')=%%
```
#### Output
The system returns tomorrow's date, alogn with a time stamp.

#### Example 2
Find next Monday date and display it.
```
%%[
VAR @today, @monday, @weekday
SET @today = Now(1) /*today date*/

  FOR @x = 1 TO 7 DO
   SET @today = DateAdd(@today,1,'d') /*add one day to today's system date*/
   SET @weekday = FormatDate(@today,'ddddd') /*change date format to string to be able to run IF statement*/
     IF @weekday == 'Monday' THEN
     SET @monday = @today
     ENDIF
  NEXT @x
]%%
Next Monday date is %%=FormatDate(@monday,'MMMM DD YYYY')=%%
```
#### Output
```
Next Monday date is March 18 2019 
```
