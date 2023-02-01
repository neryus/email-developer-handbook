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

Adding custom string if data extension field firstname have less than 2 characters or have underscore as first letter.

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
