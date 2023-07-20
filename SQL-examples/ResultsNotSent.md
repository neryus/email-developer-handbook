Compare two data extensions to find records not in both data extensions.
```
select p.* from EmailProduction p
left join EmailProduction_ST s
on p.email = s.email
where s.email is null
```
Compare two data extensions to find records in both data extensions.
```
select p.* from [Exclude - bought passes] p
left join [VIP data to exclude] s
on p.email = s.email
where s.email is not null
```
Note. When data extension names have spaces they must be embedded into square brackets.
