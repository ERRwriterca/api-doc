---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Phone Number Storer (PNS) API! You can use our API to access PNS API endpoints, which can get information on the various phone numbers, as well as their related names and locations that are stored in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'pns'

api = pns::APIClient.authorize!('rinnnnng')
```

```python
import pns

api = pns.authorize('rinnnnng')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');

let api = pns.authorize('rinnnnng');
```

Phone Number Storer uses API keys to allow access to the API. You can register a new PNS API key at our [developer portal](http://example.com/developers).

PNS expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: rinnnnng`
 

# Numbers

## Get All Records
This retrieves all records from the database.

```ruby
require 'pns'

api = pns::APIClient.authorize!('rinnnnng')
api.numbers.get
```

```python
import pns

api = pns.authorize('rinnnnng')
api.numbers.get()
```

```shell
curl "http://example.com/api/numbers" \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');

let api = pns.authorize('rinnnnng');
let numbers = api.numbers.get();
```

> The above command returns JSON structured like this:

```json
[
 {
    "name": "John Doe",
    "state": "nevada",
    "phone": 2342342345 
  },
  {
    "name": "Max Stars",
    "state": "maine",
    "phone": 3105551212 
  }
]
```

This endpoint retrieves all records in the database.

### HTTP Request

`GET http://example.com/api/numbers`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_name | false | If set to true, the result will also include names.
include_state | false | If set to true, the result will also include locations.

## Get a Specific Record

```ruby
require 'pns'

api = pns::APIClient.authorize!('rinnnnng')
api.numbers.get(3105551212)
```

```python
import pns

api = pns.authorize('rinnnnng')
api.numbers.get(3105551212)
```

```shell
curl "http://example.com/api/numbers/3105551212" \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');

let api = pns.authorize('rinnnnng');
let max = api.numbers.get(3105551212);
```

> The above command returns JSON structured like this:

```json
  {
    "name": "Max Stars",
    "state": "maine",
    "phone": 3105551212 
  }
```

This endpoint retrieves a specific record.

### HTTP Request

`GET http://example.com/numbers/<phone>`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----------
phone | number | The phone number of the record to retrieve

## Add a Record

```ruby
require 'pns'
require 'name'
require 'state'
require 'phone'

api = pns::APIClient.authorize!('rinnnnng')
api.numbers.add('Jane Doe','texas',1234441234)
```

```python
import pns
import name
import state
import phone

api = pns.authorize('rinnnnng')
api.numbers.add('Jane Doe','texas',1234441234)
```

```shell
curl "http://example.com/api/numbers/add/1234441234" \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');
const name = require('name');
const state = require('state');
const phone = require('phone');

let api = pns.authorize('rinnnnng');
let max = api.numbers.add('Jane Doe','texas',1234441234);
```

> The above command returns JSON structured like this:

```json
  {
    "name": "Jane Doe",
    "state": "texas",
    "phone": 1234441234 
  }
```

This endpoint adds a specific record with a name, location, and phone number.

### HTTP Request

`POST http://example.com/numbers/add?name='Jane Doe'&state='texas'&phone=1234441234`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----------
name | string | The name associated with the new record.
state | string | The location associated with the new record.
phone | number | The phone number of the new record.

## Update a Record

```ruby
require 'pns'
require 'name'
require 'state'
require 'phone'

api = pns::APIClient.authorize!('rinnnnng')
api.numbers.update(1234441234)
```

```python
import pns
import name
import state
import phone

api = pns.authorize('rinnnnng')
api.numbers.update(1234441234)
```

```shell
curl "http://example.com/api/numbers/update/1234441234" \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');
const name = require('name');
const state = require('state');
const phone = require('phone');

let api = pns.authorize('rinnnnng');
let max = api.numbers.update(1234441234);
```

> The above command returns JSON structured like this:

```json
  {
    "name": "Jane Doe",
    "state": "texas",
    "phone": 1234441234 
  }
```

This endpoint updates the name and location of a specific record.

### HTTP Request

`POST http://example.com/numbers/update?name='Jane Doe'&state='texas'&phone=1234441234`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----------
name | string | The name associated with the new record.
state | string | The location associated with the new record.
phone | The phone number of the new record.

## Delete a Specific Record

```ruby
require 'pns'

api = pns::APIClient.authorize!('rinnnnng')
api.numbers.delete(3105551212)
```

```python
import pns

api = pns.authorize('rinnnnng')
api.numbers.delete(3105551212)
```

```shell
curl "http://example.com/api/numbers/3105551212" \
  -X DELETE \
  -H "Authorization: rinnnnng"
```

```javascript
const pns = require('pns');

let api = pns.authorize('rinnnnng');
let max = api.numbers.delete(3105551212);
```

> The above command returns JSON structured like this:

```json
{
  "phone": 3105551212,
  "deleted" : ":("
}
```

This endpoint deletes a specific record from the PNS database.

### HTTP Request

`DELETE http://example.com/numbers/delete/<phone>`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----------
phone | number | The phone number of the record to delete.

