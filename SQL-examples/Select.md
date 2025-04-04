### Select

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
