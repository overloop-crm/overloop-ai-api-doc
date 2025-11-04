# Users
## The user object
```
# EXAMPLE OBJECT
```

```json
{
  "data": {
    "id": "11",
    "type": "users",
    "attributes": {
      "name": "Vincenzo Ruggiero",
      "email": "vincenzo@overloop.ai",
      "role": "admin",
      "phone_number": "",
      "disabled": false,
      "timezone": "Brussels",
      "created_at": "2015-08-15T16:48:46+02:00",
      "updated_at": "2016-11-25T12:40:46+01:00"
    },
    "relationships": {
      "company": {
        "data": {
          "id": "5",
          "type": "companies"
        }
      }
    }
  }
}
```

### Object attributes
Attribute | Filterable? | Description
--------- | ----------- | -----------
id | no | **integer** <br />A unique identifier for the user
name | no | **string** <br />The user’s name
email | no | **string** <br />The user’s email address
role | no | **string** <br />The user’s role. Can be `admin`, `user` or `read_only`
phone_number | no | **string** <br />The user’s phone number
disabled | **yes** | **boolean** <br />Whether the user is disabled or not
timezone | no | **string** <br />The user’s time zone
created_at | no | **datetime** <br />ISO 8601 format with timezone offset
updated_at | no | **datetime** <br />ISO 8601 format with timezone offset

### Relationships
Object | Description
--------- | -----------
company | The user’s company

## List users
```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/users

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/users" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "11",
      "type": "users",
      "attributes": {
        ...
      }
    },
    {
      "id": "38",
      "type": "users",
      "attributes": {
        ...
      }
    },
  ],
  "links": {
    "self": "https://api.overloop.ai/public/v1/users?page%5Bnumber%5D=1&page%5Bsize%5D=100",
    "next": "https://api.overloop.ai/public/v1/users?page%5Bnumber%5D=2&page%5Bsize%5D=100",
    "last": "https://api.overloop.ai/public/v1/users?page%5Bnumber%5D=5&page%5Bsize%5D=100"
  }
}
```

Returns a list of users.

This list is [paginated](#pagination) by 100 records and can also be [sorted](#sorting) or [filtered](#filtering).
