# LookupRows

### Overview
<!-- This function returns a set of unordered rows from a data extension. -->
Returns a rowset from a data extension where the field matches the specified value.

### Syntax
`LookupRows(1,2,3,[4a,4b]...)`

### Function properties
| Ordinal | Type | Required | Description |
| ------- | ---- | -------- | ----------- |
| 1 | string | true | Name of data extension from which to return the specified value |
| 2 | string | true | Name of column from which to retrieve value |
| 3 | string | true | Value used to match column value |
| 4a| string | false | Aditional column name that identifies the rows to retrieve |
| 4b| string | false | Additional value that identifies the rows to retrieve |

### Example 1
`%%=LookupRows('Products', name, Leap Wireless Earbuds)=%%`

### Output 
Returns any row that matches Leap Wireless Earbuds, and returns data from all columns including name, URL, Description, and Price.

### Example 2
```
%%[ var @domain, @rows, @rowCount, @i set @domain = Domain(emailaddr) /* get subscriber domain name from email address */ set @rows = LookupRows('AccountManagers','Domain',@domain) set @rowCount = rowcount(@rows) output (concat('Subscribers email address domain is ',@domain,'
row count: ',@rowcount,'
')) if @rowCount > 0 then for @i = 1 to 1 do var @row, @accountManagerName, @econLandingPageURL, @companyName, @accountManagerEmail set @row = row(@rows,@i) set @accountManagerName = field(@row,'AccountManagerName') set @econLandingPageURL = field(@row,'EconLandingPageURL') set @companyName = field(@row,'CompanyName') set @accountManagerEmail = field(@row,'AccountManagerEmail') output (concat('Account Manager Name: ',@accountManagerName,'
Account Manager email address: ',@accountManagerEmail,'
Subscriber works at: ',@companyName,'
Hub page: ',@econLandingPageURL)) next @i else ]%% No rows found %%[endif]%%
```

### Output
