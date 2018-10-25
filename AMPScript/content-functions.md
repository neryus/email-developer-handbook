## Overview

The Content AMPScript functions provide a means to interact, reference and output content in a Marketing Cloud account. These elements include Content Areas content blocks, Content Builder content blocks, objects in your Portfolio, files from internal or external file locations, and message context data.

### ContentBlockByID

This function returns the content stored in the specified Content Block and optionally wraps in an Impression Region.

Note: This does not retrieve contnet stored in Classic Content.

#### Arguments

`ContentBlockByID(1,2,3,4,5)`

| Ordinal | Type | Required | Description |
|:--------|:-----|:---------|:------------|
| 1 | Number | True | The ID of the content block to return. This can be specified as a String or Number. |
| 2 | String | False | Name of the Impression Region to associate with this Content Area |
| 3 | Boolean | False | Return an error if the content block cannot be found |
| 4 | String | False | Default content if an error occurs retrieving the content block specified in Ordinal 1 |
| 5 | Number | False | Numeric status code resulting from the retrieve. A value of `0` indicates the retrieve was successful, while `-1` indicates that the content was not found or empty. |

#### Example

To reference Content Block by ID:

`%%=ContentBlockByID("01234")=%%`
