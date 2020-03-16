### Example

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
