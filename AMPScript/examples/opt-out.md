Synopsis
----

The opt-out process is handled differently for subs and prospects of the same email - subscribers will manage they subscription wihtin profile page and prospects within Marketing Cloud.

```
%%[
VAR @optOutSub, @type, @email, @partyID, @optOutLink
SET @optOutSub = 'https://www.foresightnews.com/unsubscribe/?newsletterCode=FN08'
SET @type = Type
SET @email = emailaddr
SET @partyID = PartyID

IF @type == 'Sub' THEN
 SET @optOut = Concat(@optOutSub,'&email=',@email,'&pianoId=',@partyID) ELSE
 SET @optOut = [unsub_center_url] ENDIF
]%%


<p>
  %%=v(@type)=%%
</p>
<p>
  %%=v(@email)=%%
</p>
<p>
  %%=v(@partyID)=%%
</p>
<p>
  opt-out link: %%=v(@optOut)=%%
</p>
```
