```
select p.* from [Exclude - bought passes] p
left join [VIP data to exclude] s
on p.email = s.email
where s.email is not null
```
Compare two data extensions to find records not in both data extensions.
