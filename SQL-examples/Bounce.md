Find bounces for specific domain name

```
SELECT SubscriberKey, JobID, EventDate, SMTPBounceReason, SMTPMessage, BounceCategory
FROM _bounce 
WHERE Domain like '%domainname.com'
```
SQL reference
[https://help.salesforce.com/s/articleView?id=mktg.mc_as_query_bounce_history.htm&type=5](https://help.salesforce.com/s/articleView?id=mktg.mc_as_sql_reference.htm&type=5)
