### Synopsis

To pull in a profile center opt-out link or system unsubscribe string depending on email subscription type.

### Requisites

One email copy.
Two data extensions.
Two email subscription types (prospects and subs).

### Solution

Run IF statement to look for the `Type` flag within data extensions. Depending on result assign URL to a variable.

#### Script v1
```
%%[
VAR @optOutSub, @type, @email, @partyID, @optOutLink
SET @optOutSub = 'https://www.foresightnews.com/unsubscribe/?newsletterCode=FN08'
SET @type = Type
SET @email = emailaddr
SET @partyID = PartyID

IF @type == 'Sub' THEN
 SET @optOutLink = Concat(@optOutSub,'&email=',@email,'&pianoId=',@partyID) ELSE
 SET @optOutLink = [unsub_center_url] ENDIF
]%%

```

#### Script v2
```
%%[
VAR @optOutSub, @type, @optOutLink
SET @optOutSub = 'https://www.foresightnews.com/unsubscribe/?newsletterCode=FN08'
SET @type = Type

IF @type == 'Sub' THEN
 SET @optOutLink = Concat(@optOutSub,'&email=',[emailaddr],'&pianoId=',[partyID]) ELSE
 SET @optOutLink = [unsub_center_url] ENDIF
]%%

```

#### Output

Both scripts will produce the same output.

```
Unsubscribe URL: %%=RedirectTo(@optOutLink)=%%
```

#### Note

`[unsub_center_url]` system strings must be wrapped into square brackets for reference inside a script.

