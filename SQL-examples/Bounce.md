Find bounces for specific domain name

```
SELECT SubscriberKey, JobID, EventDate, SMTPBounceReason, SMTPMessage, BounceCategory
FROM _bounce 
WHERE Domain like '%domainname.com'
```
SQL reference
https://help.salesforce.com/s/articleView?id=mktg.mc_as_sql_reference.htm&type=5

Data View: Bounce
https://help.salesforce.com/s/articleView?id=mktg.mc_as_data_view_bounce.htm&type=5

Not: bounce data is retained for six months.
