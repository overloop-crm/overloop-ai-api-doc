# Account
## The account object
```
# EXAMPLE OBJECT
```

```json
{
  "data": {
    "id": "1",
    "type": "companies",
    "attributes": {
      "name": "Overloop.ai",
      "website": "https://overloop.ai",
      "phone_number": "",
      "billing_name": "Overloop.ai SRL",
      "address": "rue des Pères Blancs 4, 1040 Brussels",
      "country": "BE",
      "vat": "BE0645917753",
      "plan_name": "Starter",
      "plan_code": "starter_monthly_usd",
      "remaining_credits": 249,
      "created_at": "2024-08-15T16:48:46+02:00",
      "updated_at": "2025-10-25T12:40:46+01:00"
    }
  }
}
```

### Object attributes
Attribute | Description
--------- | -----------
id | **integer** <br />A unique identifier for the account
name | **string** <br />The account’s name
website | **string** <br />The account’s website
phone_number | **string** <br />The account’s phone number
billing_name | **string** <br />The account’s billing name (the name that will appear on invoices)
address | **string** <br />The account’s address
country | **string** <br />The account’s country code (ISO)
vat | **string** <br />The account’s VAT number
plan_name | **string** <br />The account’s plan
plan_code | **string** <br />The account’s plan code
remaining_credits | **integer** <br />The number of credits remaining
created_at | **datetime** <br />ISO 8601 format with timezone offset
updated_at | **datetime** <br />ISO 8601 format with timezone offset

## Retrieve your account
```shell
# DEFINITION
GET https://api.overloop.ai/public/v1/account

# EXAMPLE
curl -X GET "https://api.overloop.ai/public/v1/account" \
-H "Authorization: your_api_key" \
-H "Content-Type: application/vnd.api+json; charset=utf-8"
```

### Parameters
*none*

### Returns
Returns the [account object](#the-account-object).
