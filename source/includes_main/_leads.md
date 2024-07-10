# Leads
## The lead object
```
# EXAMPLE OBJECT
```

```json
{
  "data": {
    "id": "1",
    "type": "leads",
    "attributes": {
      "email": "vincenzo@overloop.ai",
      "first_name": "Vincenzo",
      "last_name": "Ruggiero",
      "description": null,
      "jobtitle": "CEO",
      "linkedin_profile": "https://www.linkedin.com/in/vincenzor",
      "phone": "+32-481-754-301",
      "title": "Mr.",
      "country": "Belgium",
      "state": "Walloon Brabant",
      "city": "Wavre",
      "industry": "IT",
      "lists": [
        "CEO",
        "BE"
      ],
      "email_status": "found",
      "c_custom_field_a": "Hot lead",
      "created_from": "extension",
      "last_emailed_at": null,
      "opened": false,
      "opened_at": null,
      "clicked": false,
      "clicked_at": null,
      "bounced": false,
      "replied": false,
      "replied_at": null,
      "excluded": false,
      "url": "https://overloop.ai/leads/1",
      "lists": ["Belgium", "Manager"],
      "created_at": "2015-08-15T16:48:46+02:00",
      "updated_at": "2016-11-25T12:40:46+01:00"
    },
    "relationships": {
      "creator": {
        "data": {
          "id": "1",
          "type": "users"
        }
      },
      "owner": {
        "data": {
          "id": "2",
          "type": "users"
        }
      },
      "organization": {
        "data": {
          "id": "2",
          "type": "organizations"
        }
      }
    }
  }
}
```

### Object attributes
Attribute | Filterable? | Description
--------- | ---------- | -----------
id | **yes** | **integer** <br />A unique identifier for the lead
email | **yes** | **string** <br />The lead's email address
first_name | **yes** | **string** <br />The lead's first name
last_name | **yes** | **string** <br />The lead's last name
description | no | **string** <br />A text description of the lead
jobtitle | **yes** | **string** <br />The lead's job title
linkedin_profile | no |**string** <br />A link to the lead's LinkedIn profile
phone | **yes** | **string** <br />The lead's phone number
title | **yes** | **string** <br />The lead's title of civility
country | **yes** | **string** <br />The lead's country
state | **yes** | **string** <br />The lead's state or region
city | **yes** | **string** <br />The lead's city
industry | **yes** | **string** <br />The lead's industry
created_from | no | **string** <br />The source of the lead. Can be `web`, `extension`, `api` or `import`
last_emailed_at | no | **datetime** <br />The date and time of the last email sent to this lead in ISO 8601 format with timezone offset
excluded | **yes** | **boolean** <br />Whether or not the lead is marked as excluded
opened | **yes** | **boolean** <br />Wheteer or not the lead opened any of your emails
opened_at | no | **datetime** <br />The date and time when the lead last opened an email
open_count | **no** | **integer** <br />The number of times the lead opened any of your emails
clicked | **yes** | **boolean** <br />Wheter or not the lead clicked a link in any of your emails
clicked_at | no | **datetime** <br />The date and time when the lead last clicked a link in an email
click_count | **no** | **integer** <br />The number of times the lead clicked a link in any of your emails
replied | **yes** | **boolean** <br />Whether or not the lead replied to one of your emails or LinkedIn messages
replied_at | no | **datetime** <br />The date and time when the lead last replied to an email or a LinkedIn message
email_reply_count | **no** | **integer** <br />The number of times the lead replied to one of your emails
linkedin_reply_count | **no** | **integer** <br />The number of times the lead replied to one of your LinkedIn messages
bounced | **yes** | **boolean** <br />Whether or not the lead email bounced
url | no | **string** <br />The full URL to the lead on Overloop.ai
lists | no | **array** <br /> Name of the lists of the lead
email_status | no | **string** <br />Indicate if the lead’s email address has been searched for by the Email Finder and the result of the last search. Can be `found`, `searching`, `search_failed`, `user_edited` or `not_searched`
created_at | no | **datetime** <br />ISO 8601 format with timezone offset
updated_at | no | **datetime** <br />ISO 8601 format with timezone offset

### Relationships
Object | Description
--------- | -----------
creator | The [user](#users) who created the lead
organization | The [organization](#organizations) of this lead
owner | The [user](#users) who owns the lead

## List leads

```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/leads

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/leads" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
    {
      "id": "1",
      "type": "leads",
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
      "type": "leads",
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
    "self": "https://api.overloop.ai/public/v1/leads/?page%5Bnumber%5D=1&page%5Bsize%5D=100",
    "next": "https://api.overloop.ai/public/v1/leads/?page%5Bnumber%5D=2&page%5Bsize%5D=100",
    "last": "https://api.overloop.ai/public/v1/leads/?page%5Bnumber%5D=5&page%5Bsize%5D=100"
  }
}
```

Returns a list of leads.

This list is [paginated](#pagination) by 100 records. It can also be [sorted](#sorting) or [filtered](#filtering).

### Returns
Returns the [lead object](#the-lead-object).

## Update a lead
```shell
# DEFINITION
PATCH https://api.overloop.ai/public/v1/leads/{CONTACT_ID}

# EXAMPLE
curl -X PATCH "https://api.overloop.ai/public/v1/leads/1" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8" \
-d '{
  "data": {
    "type": "leads",
    "attributes": {
      "email": "vincenzo@overloop.ai",
      "first_name": "Vincent",
      "c_custom_field_a": "Hot lead"
    }
  }
}'
```

Updates the specified lead by setting the values of the parameters passed. Any parameters not provided will be left unchanged.

### Parameters
Parameter | Description
--------- | -----------
id<br />**required** - *integer* | The ID of the lead to update
email<br />*string* | The lead's email
first_name<br />*string* | The lead's first name
last_name<br />*string* | The lead's last name
description<br />*string* | A text description of the lead
jobtitle<br />*string* | The lead's job title
linkedin_profile<br />*string* | A link to the lead's LinkedIn profile
phone<br />*string* | The lead's phone number
title<br />*string* | The lead's title of civility
country<br />*string* | The lead's country
state<br />*string* | *NULL* | The lead's state or region
city<br />*string* | *NULL* | The lead's city
industry<br />*string* | The lead's industry
lists<br />*array* | Name of the lists where to save the lead<br/>(note: we will create the lists if they don't exist)
owner_id<br />*integer* | The ID of the user owning this lead
organization_id<br />*integer* | ID of the organization this lead belongs to | See [create an organization](#create-an-organization)

### Returns
Returns the [lead object](#the-lead-object).
