## Select

The `SELECT` statement opens each query. It picks the columns from the source data extensions and system data views and allows you to create entirely new data points.

The `Select` statement will return every email address used in a specified job.
```
SELECT SubscriberKey
FROM _Sent
WHERE JobID = '123456789'
```

The `Select` statement will return every subscriber with a specific domain from a specific sent job.
```
SELECT SubscriberKey as Email
FROM _Sent
WHERE JobID = '123456789' AND SubscriberKey LIKE '%@centaurmedia.com'
```

The `Select` statement will return every subscriber with a specific domain name from `All Subscribers`.
```
SELECT SubscriberID, EmailAddress, Status
FROM _subscribers
WHERE Domain like '%centaurmedia.com'
```

The `Select` statement will compare two data extensions and return matching email addresses with additional data columns from the 'Universe' data extension.
```
SELECT A.EMAIL, B.Country, B.Job_Title, B.Design_Job_Role, B.Experience_Level
FROM [Third_Party] A
LEFT JOIN [UNIVERSE] B
ON A.Email = B.Email
```

### Distinct
The `Distinct` clause is the most straightforward deduplication tool. When added to the `Select` statement, it will check all available values and leave unique ones.\
*Unique subscriber from the sent data view*
```
SELECT DISTINCT
  SubscriberKey
FROM _Sent
```
It's perfect for single-column deduplication. However, applying it to a select with multiple columns will leverage all of them for deduplication.\
*Unique subscribers from the sent data view for every new day*
```
SELECT DISTINCT
  SubscriberKey,
  EventDate
FROM _Sent
```
In the above case, you will get a separate row for each Subscriber Key - email Send Date pair. You might receive multiple rows with the same Subscriber Key, but each with a different Send Date.

Reference
[Mateusz Dabrowaki](https://mateuszdabrowski.pl/docs/sql/sfmc-sql-select/)
