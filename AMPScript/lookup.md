# Lookup

## Overview

Returns specified value from a data extension. You can specify multiple additional field and value pairs as part of an AND clause.

### Syntax

`Lookup(1,2,3,4,[5a,5b]...)`

### Function Properties

| Ordinal | Type | Required | Description |
| ------- | ---- | -------- | ----------- |
| 1 | string | true | Name of the data extension from which to return the value |
| 2 | string | true | Name of the column from which to return a value |
| 3 | string | true | Name of column used to identify row containing lookup value |
| 4 | string | true | Value to match string against |
| 5a | string | false | Additional column name that identifies the row to retrieve |
| 5b | string | false | Additional value that identifies the row to retrieve |

### Example 1

