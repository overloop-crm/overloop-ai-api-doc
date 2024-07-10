# Lists
## The list object
```
# EXAMPLE OBJECT
```

```json
{
  "data": {
    "id": "1",
    "type": "lists",
    "attributes": {
      "name": "LinkedIn",
      "created_at": "2015-08-15T16:48:46+02:00",
      "updated_at": "2016-11-25T12:40:46+01:00"
    }
  }
}
```

### Object attributes
Attribute | Filterable? | Description
--------- | ----------- | -----------
id | no | **integer** <br />A unique identifier for the list
name | no | **string** <br />The list's name
created_at | no | **datetime** <br />ISO 8601 format with timezone offset
updated_at | no | **datetime** <br />ISO 8601 format with timezone offset

## List lists

```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/lists

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/lists" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "lists",
      "attributes": {
        ...
      }
    },
    {
      "id": "2",
      "type": "list",
      "attributes": {
        ...
      }
    }
  ],
  "links": {
    "self": "https://api.overloop.ai/public/v1/lists/?page%5Bnumber%5D=1&page%5Bsize%5D=100",
    "next": "https://api.overloop.ai/public/v1/lists/?page%5Bnumber%5D=2&page%5Bsize%5D=100",
    "last": "https://api.overloop.ai/public/v1/lists/?page%5Bnumber%5D=5&page%5Bsize%5D=100"
  }
}
```

Returns a list of lists.

This list is [paginated](#pagination) by 100 records and can also be [sorted](#sorting) or [filtered](#filtering).
