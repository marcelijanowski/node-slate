# Introduction

Welcome to the 3A Middleware API!

# Cars

## Get car makes

```bash
curl "http://example.com/cars/makes?year=2014"
```

> The above command returns JSON structured like this:

```json
[
  {
      "make_id": "acura",
      "make_display": "Acura",
      "make_is_common": "1",
      "make_country": "USA"
  },
  {
      "make_id": "audi",
      "make_display": "Audi",
      "make_is_common": "1",
      "make_country": "Germany"
  }
]
```

This endpoint retrieves makes by production year.

### HTTP Request

`GET http://example.com/cars/makes?year=:year`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
year | none | Year of model as number


## Get car models

```bash
curl "http://example.com/cars/make/ford?year=2017"
```

> The above command returns JSON structured like this:

```json
[
    {
        "model_name": "C-Max Energi",
        "model_make_id": "Ford",
        "year": 2017
    },
    {
        "model_name": "C-Max Hybrid",
        "model_make_id": "Ford",
        "year": 2017
    }
]
```

This endpoint retrieves models by make and year

### HTTP Request

`GET http://example.com/cars/make/:make?year=:year`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
year | none | Year of model as number
make | none | Make of car (ford, bwm)

## Get car colour

```bash
curl "http://example.com/cars/colours"
```

> The above command returns JSON structured like this:

```json
[
    {
        "name": "green",
        "display": "Green"
    },
    {
        "name": "yellow",
        "display": "Yellow"
    }
]
```

This endpoint retrieves colour of cars

### HTTP Request

`GET http://example.com/cars/colour`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

# Application

## Health check

```bash
curl "http://example.com/healthcheck"
```

> The above command returns JSON structured like this:

```json
{
    "uptime": 9871.694
}
```

This endpoint health check for server

### HTTP Request

`GET http://example.com/app/features`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

## Features

```bash
curl "http://example.com/app/features"
```

> The above command returns app base features (feature flags)

```json
{
    "rso-flag": true,
    "another-flag": false
}
```

This endpoint retrives features flags for application

### HTTP Request

`GET http://example.com/app/features`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

## Localization

```bash
curl "http://example.com//app/localization"
```

> The above command basic localization strings

```json
{
    "ok": "OK",
    "cancel": "Cancel",
    "next": "Next"
}
```

This endpoint retrives localization strings

### HTTP Request

`GET http://example.com/order`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

# Orders

## Create order

```bash
curl --request POST \
  --url 'http://localhost:8000/order' \
  --header 'Content-Type: application/json' \
  --data '{
  "memberNumber": "4290050026360715",
  "comment": "clevertech",
  "userId": "602675",
  "pacesetterCode": "L302",
  "contact": {
    "firstName": "PRIMARY",
    "lastName": "DEPENDENT",
    "telephoneNumber": "4075551234"
  },
  "location": {
    "latitude": 37.708,
    "longitude": -121.909
  },
  "vehicle": {
    "color": "Black",
    "make": "FORD",
    "model": "Pinto",
    "year": "2003",
    "driveLine": "2WD"
  }
}
'
```

> The above command order return sample response

```json
{
    "date": "2018-08-09",
    "id": 8,
    "minutes": 120
}
```

This endpoint create order

### HTTP Request

`POST http://example.com/order`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Body
`{
  "memberNumber": "4290050026360715",
  "comment": "clevertech",
  "userId": "602675",
  "pacesetterCode": "L302",
  "contact": {
    "firstName": "PRIMARY",
    "lastName": "DEPENDENT",
    "telephoneNumber": "4075551234"
  },
  "location": {
    "latitude": 37.708,
    "longitude": -121.909
  },
  "vehicle": {
    "color": "Black",
    "make": "FORD",
    "model": "Pinto",
    "year": "2003",
    "driveLine": "2WD"
  }
}`

## Get order

```bash
curl "http://example.com/order?date=2018-07-31&&id=1"
```

> The above command returns JSON structured like this:

```json
{
    "history": [
        {
            "date": "2018-08-03T00:38:56",
            "status": {
                "code": "RE",
                "description": "Received"
            },
            "updatedStatus": {
                "code": "RE",
                "description": "Received"
            },
            "reason": {
                "code": "2K",
                "description": "Call Received"
            }
        }
    ],
    "call_id": 1,
    "call_date": "2018-08-03"
}
```

This endpoint retrieves makes by production year.

### HTTP Request

`GET http://example.com/order?date=:date&&id=:id`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
date | none | Date in format YYYY-mm-dd (2018-01-01)
id | none | Order id as number

# Member

## Get member by member number

```bash
curl "http://example.com/member?id=4290058524515011"
```

> The above command returns JSON structured like this:

```json
{
    "clubCode": "005",
    "membershipId": "85245150",
    "associateId": "1",
    "memberNumber": "4290058524515011",
    "type": "B",
    "firstName": "ADAM",
    "lastName": "LUCAS",
    "expiration": "2019-04-20",
    "status": "A",
    "joinYear": 2015,
    "yearsWithAAA": 5,
    "telephoneNumbers": [
        "4155180959"
    ],
    "address": {
        "line1": "2529 NOBLE AVE",
        "city": "ALAMEDA",
        "state": "CA",
        "postalCode": "94501"
    }
}
```

This endpoint member by member number

### HTTP Request

`GET http://example.com/member?id=:id`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | none | member number 

## Get member by phone number

```bash
curl "http://example.com/member?phone=4290058524515011"
```

> The above command returns JSON structured like this:

```json
{
    "clubCode": "005",
    "membershipId": "85245150",
    "associateId": "1",
    "memberNumber": "4290058524515011",
    "type": "B",
    "firstName": "ADAM",
    "lastName": "LUCAS",
    "expiration": "2019-04-20",
    "status": "A",
    "joinYear": 2015,
    "yearsWithAAA": 5,
    "telephoneNumbers": [
        "4155180959"
    ],
    "address": {
        "line1": "2529 NOBLE AVE",
        "city": "ALAMEDA",
        "state": "CA",
        "postalCode": "94501"
    }
}
```

This endpoint member by member number

### HTTP Request

`GET http://example.com/member?phone=:id`

### Header
 | |
--------- | ------- 
**Content-Type** | application/json

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | none | member phone number