# Organizations
## The organization object
```
# EXAMPLE OBJECT
```

```json
{
  "data": {
    "id": "1",
    "type": "organizations",
    "attributes": {
      "name": "Overloop.ai",
      "description": null,
      "website": "https://overloop.ai",
      "email": "contact@overloop.ai",
      "phone": "+32-481-754-301",
      "country": "Belgium",
      "state": "Walloon Brabant",
      "city": "Wavre",
      "address": "Wavre",
      "c_custom_field_a": "Hot lead",
      "created_from": "extension",
      "lists": ["Belgium", "IT"],
      "created_at": "2015-08-15T16:48:46+02:00",
      "updated_at": "2016-11-25T12:40:46+01:00"
    }
  }
}
```

### Object attributes
Attribute | Filterable? | Description
--------- | ---------- | -----------
id | **yes** | **integer** <br />A unique identifier for the organization
name | **yes** | **string** <br />The name of the organization
website | **yes** | **string** <br />The organization's website
description | **yes** | **string** <br />The organization's description
email | **yes** | **string** <br />The organization's lead email
phone | **yes** | **string** <br />The organization's lead phone number
country | **yes** | **string** <br />The organization's country
city | **yes** | **string** <br />The organization's city
state | **yes** | **string** <br />The organization's state
address | **yes** |**string** <br />The organization's full address
lists | no | **array** <br /> Name of the lists of the organization
created_at | no | **datetime** <br />ISO 8601 format with timezone offset
updated_at | no | **datetime** <br />ISO 8601 format with timezone offset

### Relationships
Object | Description
--------- | -----------
creator | The [user](#users) who created the organization
updater | The [user](#users) who updated the organization

## List organizations

```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/organizations

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/organizations" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "organizations",
      "attributes": {
        ...
      },
      "relationships": {
        "owner": {
          "data": {
            ...
          }
        }
      }
    },
    {
      "id": "2",
      "type": "organizations",
      "attributes": {
        ...
      },
      "relationships": {
        "owner": {
          "data": {
            ...
          }
        }
      }
    }
  ],
  "links": {
    "self": "https://api.overloop.ai/public/v1/organizations/?page%5Bnumber%5D=1&page%5Bsize%5D=100",
    "next": "https://api.overloop.ai/public/v1/organizations/?page%5Bnumber%5D=2&page%5Bsize%5D=100",
    "last": "https://api.overloop.ai/public/v1/organizations/?page%5Bnumber%5D=5&page%5Bsize%5D=100"
  }
}
```

Returns a list of organizations.

This list is [paginated](#pagination) by 100 records. It can also be [sorted](#sorting) or [filtered](#filtering).


## Update an organization
```shell
# DEFINITION
PATCH https://api.overloop.ai/public/v1/organizations/{ORGANIZATION_ID}

# EXAMPLE
curl -X PATCH "https://api.overloop.ai/public/v1/organizations/1" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8" \
-d '{
  "data": {
    "type": "organizations",
    "attributes": {
      "name": "Overloop.ai",
      "c_custom_field_a": "Hot lead"
    }
  }
}'
```

Updates the specified organization by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

### Parameters
Parameter | Description
--------- | -----------
id<br />**required** - *integer* | A unique identifier for the organization
name | The name of the organization
website | The organization's website
description | The organization's description
email | The organization's lead email
phone | The organization's lead phone number
country | The organization's country
city | The organization's city
state | The organization's state
address | The organization's full address
lists | Name of the lists of the organization
owner_id | The ID of the user owning this organization
created_at | ISO 8601 format with timezone offset
updated_at | ISO 8601 format with timezone offset

### Returns
Returns the [organization object](#the-organization-object).
