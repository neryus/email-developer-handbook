# Date & Time Functions
The date and time AMPscript functions are used to return, convert and adjust date and time values.

- [Date Add](#dateadd)
- [Now](#now)

For functions with date-input arguments, those arguments must take one of the following forms:

- Includes a date only.
- Includes both a date and time.
- Includes a time only; the current date is assumed.
- Includes the GMT qualifier and conforms to the [RFC 1123](https://www.ietf.org/rfc/rfc1123.txt) time format.
- Includes the date, time and timezone offset. These must conform to the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format.



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
The system returns tomorrow's date, along with a time stamp.

#### Example 2
The objective is to output the date of next Monday.
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
#### Example 3
The objective is to output the Monday date if tomorrow is Saturday.
```
%%[
VAR @tomorrowSystemTime, @formatSystemDate, @formattedDate
SET @tomorrowSystemTime = DateAdd(Now(true),1,'d')
SET @formatSystemDate = FormatDate(@tomorrowSystemTime, 'ddddd') /*convert integral to string so it can be used in the IF statement*/
  IF @formatSystemDate == 'Saturday' THEN
    SET @tomorrowSystemTime = DateAdd(Now(true),3,'d')
  ENDIF
SET @formattedDate = FormatDate(@tomorrowSystemTime, 'ddddd DD MMMM YYYY')
]%%
%%=v(@formatSystemDate)=%%<br>
%%=FormatDate(@tomorrowSystemTime, 'ddddd DD MMMM YYYY')=%%
```
#### Output
```
Saturday
Monday 18 March 2019
```

## Now
This function returns the current system date and time. The system date and time are based on the data center location of the Marketing Cloud account.

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
The `true` value preserves the date and time of sending when the email opens in the browser.

#### Example 2
The objective is to display today's London time. Because the system time is the US and if an email is scheduled to go earlier than 7 AM it will display the previous day's date.
What does the function `DateAdd`? It adds 7 hours to the system time.
```
%%[
SET @LondonTime = DateAdd(Now(true), '7', 'h')
]%%
Current system date and time: %%=Now()=%%
London date and time: %%=v(@LondonTime)=%%
```

#### Output
```
Current system date and time: 11/21/2024 12:27:15 PM
London date and time: 11/21/2024 7:27:15 PM
```
