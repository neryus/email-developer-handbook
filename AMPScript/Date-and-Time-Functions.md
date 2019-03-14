# Date & Time Functions
The date and time AMPscript functions are used to return, convert and adjust date and time values.

- [Date Add](#dateadd)
- [Now](#now)

For functions with date-input arguments, those arguments must take one of the following forms:

- Includes a date only.
- Includes both a date and time.
- Includes a time only; in this case, the current date is assumed.
- Includes the GMT qualifier and conforms to the [RFC 1123](https://www.ietf.org/rfc/rfc1123.txt) time format.
- Includes the date, time and a timezone offset. These must conform to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format.



## DateAdd

This function returns a date with the specified number interval added to the specified part of the date.

#### Syntax
`DateAdd(1,2,3)`

#### Function Properties
| Ordinal | Type | Required | Description |
| :-----: | :--- | :------- | :---------- |
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

## Now
This function returns the current system date and time. The system date and time is based on the data center location of Marketing Cloud account.

#### Syntax
`Now()`

#### Function Properties
| Ordinal | Type | Required | Description |
| :-----: | :--- | :------- | :---------- |
| 1 | Bollean | False | Preserve the send time value. A value of `true` will preserve it. The default value is `false` if no value is specified. |

#### Example 1
```
Current system date and time: %%=Now()=%%
Current system date and time with True value: %%=Now(true)=%%
```

#### Output
```
Current system date and time: 3/14/2019 5:55:04 AM
Current system date and time with True value: 3/14/2019 5:55:04 AM
```
The `true` value preserves the date and time of sending when email opens in the browser.
