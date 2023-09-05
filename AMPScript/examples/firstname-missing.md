## Example

Adding custom string if data extension field Firstname is empty.

```
%%[
var @firstName, @displayName
set @firstName = [Firstname] 
if empty(@firstName) then 
  set @displayName = "friend"
else 
  set @displayName = @firstName 
endif 
]%% 

Hello %%=v(@displayName)=%%
```

### Output

```
Hello friend
```
## Example #2

If the data extension missing firstname column value then the output is the string "Hi,". If it has then change the case and output string "Hi Paul,". Used to remove space character between "hi" and comma when firstname is missing within send list.
```
%%[
set @firstname = [Firstname]    
if empty(@firstname) then 
 set @firstname = "Hi"
else 
 set @firstname = Concat("Hi ", Propercase(@firstname), ",")
endif
]%%

%%=v(@firstname)=%%
```

### Output

```
Hello
```

## Example #3

Adding custom string if data extension field firstname is shorter than 2 characters or have underscore as first letter.

```
%%[
Set @FirstName = [FirstName] 
IF Length(@FirstName) < 2 OR Empty(@FirstName) OR Substring(@FirstName, 1, 2) == "_ " 
THEN Set @FirstName = "Friend" 
ENDIF
]%%
Hello %%=v(@FirstName)=%%
```
### Output

```
Hello Friend
```
