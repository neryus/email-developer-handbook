# Domain
This function returns domain portion of an email address.

## Syntax
`Domain(1)`

## Function properties

| Ordinal | Type | Requried | Description |
| ------- | ---- | -------- | ----------- |
| 1 | String | True | Email address |

## Example
The following example displays the domain of the Subscriber’s email address using the `emailaddr` email Subscriber data string.
```
<p>Email address %%emailaddr%% domain is %%=Domain(emailaddr)=%%</p>
```

For a Subscriber with the email address nerijus@paukste.com, the following output will be displayed:
```
<p>Email address nerijus@paukste.com domain is paukste.com</p>
```

---

# Empty
This function provides a conditional evaluation of an expression. If the expression evaluates `null` or empty, the function will output `true`, otherwise it will output `false`.

## Syntax
`Empty(1)`

## Function properties

| Ordinal | Type | Requried | Description |
| ------- | ---- | -------- | ----------- |
| 1 | String | True | An attribute, variable or nested function to evaluate |

## Example
```
SET @BrandsRepresenting = Field(@Row, "RepresentingBrands")
IF EMPTY(@BrandsRepresenting) THEN SET @BrandsRepresenting = "<em>(please provide)</em>" ENDIF
```

### Output
```
Brands that you handle for the agency: (please provide)
```
