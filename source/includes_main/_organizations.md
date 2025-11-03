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
      "website": "https://overloop.com",
      "email": "contact@overloop.com",
      "phone": "+32-481-754-301",
      "country": "Belgium",
      "state": "Brussels Region",
      "city": "Brussels",
      "address": "Rue des Pères Blancs 4",
      "c_custom_field_a": "My organization’s custom field value",
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
website | **yes** | **string** <br />The organization’s website
description | **yes** | **string** <br />The organization’s description
email | **yes** | **string** <br />The organization’s email
phone | **yes** | **string** <br />The organization’s phone number
country | **yes** | **string** <br />The organization’s country
city | **yes** | **string** <br />The organization’s city
state | **yes** | **string** <br />The organization’s state
address | **yes** |**string** <br />The organization’s full address
lists | no | **array** <br /> Name of the lists of the organization
created_at | no | **datetime** <br />ISO 8601 format with timezone offset
updated_at | no | **datetime** <br />ISO 8601 format with timezone offset

### Organization Custom Fields

Custom fields can be used as normal attributes by using their `identifier` as attribute key, see the `c_custom_field_a` example in the above payload.

You can retrieve the list of your custom fields by using the [custom fields index endpoint](#list-custom-fields).

They accept a value depending on [their format](#the-custom-field-object)

### Relationships
Object | Description
--------- | -----------
creator | The [user](#users) who created the organization
updater | The [user](#users) who updated the organization

## Create an organization
```shell
# DEFINITION
POST https://api.overloop.ai/public/v1/organizations

# EXAMPLE
curl -X POST "https://api.overloop.ai/public/v1/organizations" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8" \
-d '{
  "data": {
    "type": "organizations",
    "attributes": {
      "name": "Overloop",
      "lists": ["Belgium", "IT"],
      "c_custom_field_a": "My organization’s custom field value"
    }
  }
}'
```

This will create a new organization. If you don’t set the `owner_id` parameter then the user who performed the action will be assigned as the owner.

### Parameters
Parameter | Default | Description
--------- | ------- | ------------
name<br />*string* | *NULL* | The name of the organization
website<br />*string* | *NULL* | The organization’s website
description<br />*string* | *NULL* | The organization’s description
email <br />*string*| *NULL* | The organization’s email
phone<br />*string* | *NULL* | The organization’s phone number
country<br />*string* | *NULL* | The organization’s country
city<br />*string* | *NULL* | The organization’s city
state<br />*string* | *NULL* | The organization’s state
address<br />*string* | *NULL* |The organization’s full address
lists<br />*array* | *NULL* | Name of the lists of the organization
owner_id<br />*integer* | *ID of the user who created the organization* | The ID of the user owning this organization

This method accepts an optional URL parameter `return_existing`. When set to true (default is false),
that will return an existing organization if an organization with that name already exists (with 200 HTTP status code, 422 otherwise).

### Returns
Returns the [organization object](#the-organization-object).

## Retrieve an organization
```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/organizations/{ORGANIZATION_ID}

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/organizations/1" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

### Parameters
Parameter | Description
--------- | -----------
id<br />**required** - *integer* | The ID of the organization to retrieve

### Returns
Returns the [organization object](#the-organization-object).

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
      "name": "Overloop",
      "c_custom_field_a": "My organization’s custom field value"
    }
  }
}'
```

Updates the specified organization by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

### Parameters
Parameter | Description
--------- | -----------
id<br />**required** - *integer* | A unique identifier for the organization
name<br /> *string* | The name of the organization
website<br /> *string* | The organization’s website
description<br /> *string* | The organization’s description
email<br /> *string* | The organization’s email
phone<br /> *string* | The organization’s phone number
country<br /> *string* | The organization’s country
city<br /> *string* | The organization’s city
state<br /> *string* | The organization’s state
address<br /> *string* | The organization’s full address
lists<br /> *array* | Name of the lists of the organization
owner_id<br /> *integer* | The ID of the user owning this organization

### Returns
Returns the [organization object](#the-organization-object).

## Delete an organization
```shell
# DEFINITION
DELETE https://api.overloop.ai/public/v1/organizations/{ORGANIZATION_ID}

# EXAMPLE
curl -X DELETE "https://api.overloop.ai/public/v1/organizations/1" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "1",
    "type": "organizations"
  }
}
```

Permanently deletes an organization. It cannot be undone.


### Parameters
Parameter | Required? | Type | Description
--------- | --------- | -----| -----------
id | **yes** | integer | The ID of the organization to delete

### Returns
Returns an object containing the organization ID.

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
