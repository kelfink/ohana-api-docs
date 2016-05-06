# Phones

## Create a new phone

Phones can be created for either a location or a contact.

```ruby
# Create a phone for location with id 1
Ohanakapa.post('locations/1/phones/', query: { number: '123-456-7890', extension: '1200', department: 'Referrals',  number_type: 'voice', country_prefix: '+1' })
```

```shell
curl -X POST "https://ohana-api-demo.herokuapp.com/api/locations/1/phones" -d '{"number": "123-456-7890", "extension": "1200", "department": "Referrals", "number_type": "voice", "country_prefix": "+1"}' -H "X-Api-Token: your_token" -H "Content-Type: application/json"
```

> When successful, the above command returns a `201` HTTP status code and JSON
> structured like this:

```json
{
  "id": 1,
  "number": "123-456-7890",
  "extension": "1200",
  "department": "Referrals",
  "number_type": "voice",
  "country_prefix": "+1"
}
```

This endpoint creates a new phone for the specified entity.

### HTTP Request

For locations:
`POST https://ohana-api-demo.herokuapp.com/api/locations/:location_id/phones`

For contacts:
`POST https://ohana-api-demo.herokuapp.com/api/locations/:location_id/contacts/:contact_id/phones`

### JSON Parameters

| Name | Type | Requirement | Detail |
|:-----|:-----|:---------|:-------|
| number | string | required | The 10-digit US phone number. |
| vanity_number | string | optional | The 10-digit US phone number with vanity letters. For example: 703-555-HELP |
| extension | string | optional | The phone number extension. Must only contain numbers. For example: "1234" |
| department | string | optional | The department this phone number reaches. |
| number_type | string | required | Can be one of these four values: `fax`, `voice`, `hotline`, `tty`. |
| country_prefix | string | optional | The country prefix code, such as `+1` for the USA. |

<aside class="warning">All POST requests require a valid token passed via the
`X-Api-Token` HTTP header</aside>
