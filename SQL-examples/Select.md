### Select

The `Select` statement will return every email address used in a specified job.

```select _subscriberkey from _sent where jobID ='0123456789'```

Select a subscriber with a specific domain name.
```
SELECT SubscriberID, EmailAddress, Status
FROM _subscribers
WHERE Domain like '%centaurmedia.com'
```
