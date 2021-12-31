---
title: EasyTravelApi v0.1.23
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="easytravelapi">EasyTravelApi v0.1.23</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

API for travel agents

Base URLs:

* <a href="https://test.easytravelapi.com/rest">https://test.easytravelapi.com/rest</a>

<h1 id="easytravelapi-default">Default</h1>

## getAvailableActivities

<a id="opIdgetAvailableActivities"></a>

`GET /{authtoken}/activity/available`

*Get available activities*

By passing a resort and holidays dates you get a list of the available activities

<h3 id="getavailableactivities-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|start|query|integer(int32)|false|Holidays start date in YYYYMMDD format|
|resorts|query|string|false|Resort ID. You can get it from commons/getportfolio|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableActivities": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getavailableactivities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableActivitiesRS](#schemagetavailableactivitiesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookActivity

<a id="opIdbookActivity"></a>

`POST /{authtoken}/activity/booking`

*Book an activity*

Here you can confirm an activity booking. You must provide a price key and some additional data (lead name, comments, ...)

> Body parameter

```json
{
  "fileId": "string",
  "key": "string",
  "pickup": "string",
  "date": 0,
  "language": "string",
  "activityLanguage": "string",
  "shiftId": "string",
  "adults": 0,
  "children": 0,
  "infants": 0,
  "supplementIds": "string",
  "mailingUnwanted": false,
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "roomNumber": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "supplements": "string",
  "coupon": "string"
}
```

<h3 id="bookactivity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookActivityRQ](#schemabookactivityrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="bookactivity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookActivityRS](#schemabookactivityrs)|

<aside class="success">
This operation does not require authentication
</aside>

## checkActivity

<a id="opIdcheckActivity"></a>

`GET /{authtoken}/activity/check/{key}`

*Check activity availability*

By passing a price key you get extra info

<h3 id="checkactivity-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The activity price key, as provided in the /activity/available step|
|date|query|integer(int32)|false|none|
|language|query|string|false|none|
|adults|query|integer(int32)|false|none|
|children|query|integer(int32)|false|none|
|variant|query|string|false|none|
|shift|query|string|false|none|
|pickup|query|string|false|none|
|activityLanguage|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}
```

<h3 id="checkactivity-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CheckActivityRS](#schemacheckactivityrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFilteredActivities

<a id="opIdgetFilteredActivities"></a>

`GET /{authtoken}/activity/filter`

*Get available activities filtered*

By passing a resort and holidays dates you get a list of the available activities

<h3 id="getfilteredactivities-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|start|query|integer(int32)|false|Holidays start date in YYYYMMDD format|
|resourceid|query|string|false|Resort ID. You can get it from commons/getportfolio|
|language|query|string|false|none|
|minprice|query|number(double)|false|Min price range to filter|
|maxprice|query|number(double)|false|Max price range to filter|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableActivities": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getfilteredactivities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableActivitiesRS](#schemagetavailableactivitiesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getActivityPriceDetails

<a id="opIdgetActivityPriceDetails"></a>

`GET /{authtoken}/activity/pricedetails/{key}`

*Get activity price details*

By passing a price key you get extra info

<h3 id="getactivitypricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The activity price key, as provided in the /activity/available step|
|language|query|string|false|none|
|supplements|query|string|false|none|
|coupon|query|string|false|Discount coupons|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "cancellationFreeDate": "string",
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string"
}
```

<h3 id="getactivitypricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityPriceDetailsRS](#schemagetactivitypricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getActivityRates

<a id="opIdgetActivityRates"></a>

`GET /{authtoken}/activity/rates/{activityId}`

*Get activity rates*

By passing a price key you get extra info

<h3 id="getactivityrates-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|activityId|path|string|true|The activity price key, as provided in the /activity/available step|
|date|query|integer(int32)|false|none|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ],
  "shifts": [
    {
      "id": "string",
      "name": "string",
      "languages": [
        {
          "id": "string",
          "name": "string"
        }
      ],
      "pickups": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getactivityrates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityRatesRS](#schemagetactivityratesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## login

<a id="opIdlogin"></a>

`POST /{authtoken}/agents/login`

*Use this method to login the tickets app*

> Body parameter

```json
{
  "user": "string",
  "password": "string"
}
```

<h3 id="login-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetLoginRQ](#schemagetloginrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "authUser": "string",
  "message": "string",
  "logged": false
}
```

<h3 id="login-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetLoginRS](#schemagetloginrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getPassengerDetails

<a id="opIdgetPassengerDetails"></a>

`GET /{authtoken}/agents/passengerdetails`

*Get available generic products*

you get a list of the available generic products by type

<h3 id="getpassengerdetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|q|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "found": false,
  "agency": "string",
  "fileId": "string",
  "leadName": "string",
  "comments": "string",
  "prodCenterId": "string",
  "hotelName": "string",
  "roomNumber": "string",
  "telephone": "string",
  "email": "string"
}
```

<h3 id="getpassengerdetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetPassengerDetailsRS](#schemagetpassengerdetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getPlainList

<a id="opIdgetPlainList"></a>

`GET /{authtoken}/agents/plainlist`

*Use this method to get  all lists of available activities for an agent*

<h3 id="getplainlist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|user|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ],
  "plainActivities": [
    {
      "id": "string",
      "description": "string",
      "htmlDescription": "string",
      "activityId": "string",
      "retailPrice": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "groupReference": "string",
      "groupDescription": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "currencies": [
    {
      "name": "string",
      "value": 0
    }
  ],
  "companyData": {
    "name": "string",
    "legalText": "string",
    "contactPhone": "string",
    "contactEmail": "string"
  }
}
```

<h3 id="getplainlist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetPlainListRS](#schemagetplainlistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getProductionCentersList

<a id="opIdgetProductionCentersList"></a>

`GET /{authtoken}/agents/productioncenters`

*Get available generic products*

you get a list of the available generic products by type

<h3 id="getproductioncenterslist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|user|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "productionCenters": [
    {
      "id": "string",
      "name": "string",
      "hotelName": "string"
    }
  ]
}
```

<h3 id="getproductioncenterslist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetProductionCentersListRS](#schemagetproductioncenterslistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## updateBookings

<a id="opIdupdateBookings"></a>

`POST /{authtoken}/agents/updatebookings`

*Use this method to syncronize data from offline tickets app*

> Body parameter

```json
{
  "userId": "string",
  "cartList": [
    {
      "fileId": "string",
      "agencyReference": "string",
      "productionCenterId": "string",
      "date": "string",
      "personaldata": {
        "hotel": "string",
        "telefono": "string",
        "titular": "string",
        "email": "string",
        "habitacion": "string",
        "comments": "string"
      },
      "total": "string",
      "payments": [
        {
          "amount": "string",
          "paymentMethod": {
            "key": "string",
            "name": "string",
            "currencyIsoCode": "string"
          },
          "currency": {
            "name": "string",
            "value": 0
          }
        }
      ],
      "cart": [
        {
          "precio": "string",
          "img": "string",
          "qty": "string",
          "id": "string",
          "nombre": "string",
          "nombreHtml": "string",
          "qrCode": "string",
          "groupReference": "string"
        }
      ],
      "status": "string"
    }
  ]
}
```

<h3 id="updatebookings-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetUpdatedCartsRQ](#schemagetupdatedcartsrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="updatebookings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[UpdateBookingRS](#schemaupdatebookingrs)|

<aside class="success">
This operation does not require authentication
</aside>

## confirmServices

<a id="opIdconfirmServices"></a>

`POST /{authtoken}/channel/confirm`

*Use this method to confirm or reject services*

> Body parameter

```json
{
  "serviceConfirmations": [
    {
      "bookingId": "string",
      "confirmed": false,
      "comments": "string"
    }
  ]
}
```

<h3 id="confirmservices-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[ConfirmServicesRQ](#schemaconfirmservicesrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="confirmservices-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[ConfirmServicesRS](#schemaconfirmservicesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getGrantedHotels

<a id="opIdgetGrantedHotels"></a>

`GET /{authtoken}/channel/granted`

*Use this method to know which hotels are you allowed to update. It provides the ids to be used by the channel manager*

<h3 id="getgrantedhotels-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "grantedHotels": [
    {
      "hotelId": "string",
      "hotelName": "string",
      "roomIds": [
        {
          "id": "string",
          "description": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getgrantedhotels-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetGrantedHotelsRS](#schemagetgrantedhotelsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## update

<a id="opIdupdate"></a>

`POST /{authtoken}/channel/hotel/inventory`

*Use this method to update hotel inventory*

> Body parameter

```json
{
  "operations": [
    {
      "hotelId": "string",
      "roomId": "string",
      "action": "string",
      "startDate": 0,
      "endDate": 0,
      "newValue": "string"
    }
  ]
}
```

<h3 id="update-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[UpdateRQ](#schemaupdaterq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="update-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[UpdateRS](#schemaupdaters)|

<aside class="success">
This operation does not require authentication
</aside>

## getRoomingList

<a id="opIdgetRoomingList"></a>

`GET /{authtoken}/channel/roominglist`

*Use this method to download the list of hotel bookings*

<h3 id="getroominglist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|confirmedfrom|query|integer(int32)|false|Starting date you want service bookings confirmed from. In YYYYMMDD format|
|confirmedto|query|integer(int32)|false|Ending date you want service bookings confirmed to. In YYYYMMDD format|
|startingfrom|query|integer(int32)|false|Starting date you want service bookings starting from. In YYYYMMDD format|
|startingto|query|integer(int32)|false|Ending date you want service bookings starting from. In YYYYMMDD format|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookings": [
    {
      "bookingId": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string",
      "serviceType": "string",
      "serviceDescription": "string",
      "start": "string",
      "end": "string",
      "status": "string",
      "leadName": "string",
      "retailValue": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "netValue": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "commentsToProvider": "string",
      "privateComments": "string",
      "stays": [
        {
          "start": 0,
          "end": 0,
          "roomId": "string",
          "roomName": "string",
          "boardBasisId": "string",
          "boardBasisName": "string",
          "numberOfRooms": 0,
          "paxPerRoom": 0,
          "ages": [
            0
          ]
        }
      ]
    }
  ]
}
```

<h3 id="getroominglist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetRoomingListRS](#schemagetroominglistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAvailableCircuits

<a id="opIdgetAvailableCircuits"></a>

`GET /{authtoken}/circuit/available`

*Get available circuits*

By passing a resort and holidays dates you get a list of the available circuits

<h3 id="getavailablecircuits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableCircuits": [
    {
      "circuitId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getavailablecircuits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableCircuitsRS](#schemagetavailablecircuitsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookCircuit

<a id="opIdbookCircuit"></a>

`POST /{authtoken}/circuit/booking`

*Book a circuit*

Here you can confirm a circuit booking. You must provide a price key and some additional data (lead name, comments, ...)

> Body parameter

```json
{
  "fileId": "string",
  "key": "string",
  "date": 0,
  "language": "string",
  "shiftId": "string",
  "variantId": "string",
  "adults": 0,
  "children": 0,
  "infants": 0,
  "mailingUnwanted": false,
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "supplements": "string",
  "coupon": "string"
}
```

<h3 id="bookcircuit-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookCircuitRQ](#schemabookcircuitrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="bookcircuit-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookCircuitRS](#schemabookcircuitrs)|

<aside class="success">
This operation does not require authentication
</aside>

## checkCircuit

<a id="opIdcheckCircuit"></a>

`GET /{authtoken}/circuit/check/{key}`

*Check circuit availability*

By passing a price key you get extra info

<h3 id="checkcircuit-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The activity price key, as provided in the /activity/available step|
|date|query|integer(int32)|false|none|
|language|query|string|false|none|
|adults|query|integer(int32)|false|none|
|children|query|integer(int32)|false|none|
|variant|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}
```

<h3 id="checkcircuit-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CheckCircuitRS](#schemacheckcircuitrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFilteredCircuits

<a id="opIdgetFilteredCircuits"></a>

`GET /{authtoken}/circuit/filter`

*Get available circuits filtered*

<h3 id="getfilteredcircuits-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|labels|query|string|false|Holidays start date in YYYYMMDD format|
|language|query|string|false|none|
|minprice|query|number(double)|false|Min price range to filter|
|maxprice|query|number(double)|false|Max price range to filter|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableCircuits": [
    {
      "circuitId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getfilteredcircuits-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableCircuitsRS](#schemagetavailablecircuitsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getCircuitPriceDetails

<a id="opIdgetCircuitPriceDetails"></a>

`GET /{authtoken}/circuit/pricedetails/{key}`

*Get circuit price details*

By passing a price key you get extra info

<h3 id="getcircuitpricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The circuit price key, as provided in the /circuit/available step|
|language|query|string|false|none|
|supplements|query|string|false|none|
|coupon|query|string|false|Discount coupons|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}
```

<h3 id="getcircuitpricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetCircuitPriceDetailsRS](#schemagetcircuitpricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getCircuitRates

<a id="opIdgetCircuitRates"></a>

`GET /{authtoken}/circuit/rates/{key}`

*Get circuit rates*

By passing a price key you get extra info

<h3 id="getcircuitrates-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The circuit price key, as provided in the /circuit/available step|
|date|query|integer(int32)|false|none|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ]
}
```

<h3 id="getcircuitrates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetCircuitRatesRS](#schemagetcircuitratesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getActivityAvailabilityCalendar

<a id="opIdgetActivityAvailabilityCalendar"></a>

`GET /{authtoken}/cms/activityavailabilitycalendar`

*Use this method to know which hotels are available and their prices*

<h3 id="getactivityavailabilitycalendar-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|resorts|query|string|false|The comma separated list of resorts you are interested in|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}
```

<h3 id="getactivityavailabilitycalendar-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityAvailabilityCalendarRS](#schemagetactivityavailabilitycalendarrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getActivityCheckList

<a id="opIdgetActivityCheckList"></a>

`GET /{authtoken}/cms/activitychecklist`

*Use this method to get  all lists of available activities in a given date*

<h3 id="getactivitychecklist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|date|query|integer(int32)|false|Date of activities |

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ]
}
```

<h3 id="getactivitychecklist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityCheckListRS](#schemagetactivitychecklistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## cartBooking

<a id="opIdcartBooking"></a>

`POST /{authtoken}/cms/cartbooking`

*Use this method to syncronize data from offline tickets app*

> Body parameter

```json
{
  "bookings": [
    {
      "property1": {},
      "property2": {}
    }
  ],
  "captchaToken": "string",
  "language": "string",
  "mailingUnwanted": false,
  "travelAssuranceId": "string"
}
```

<h3 id="cartbooking-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookCMSRQ](#schemabookcmsrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="cartbooking-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookCMSRS](#schemabookcmsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## cartCompletion

<a id="opIdcartCompletion"></a>

`POST /{authtoken}/cms/cartcompletion`

*Use this method to syncronize data from offline tickets app*

> Body parameter

```json
{
  "bookings": [
    {
      "property1": {},
      "property2": {}
    }
  ],
  "captchaToken": "string",
  "language": "string",
  "mailingUnwanted": false,
  "travelAssuranceId": "string",
  "geoLoc": "string"
}
```

<h3 id="cartcompletion-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[CartCompletionRQ](#schemacartcompletionrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "additionalServicesLinks": [
    {
      "type": "string",
      "uri": "string"
    }
  ],
  "travelInsurance": {
    "id": "string",
    "name": "string",
    "description": "string",
    "icon": "string",
    "value": 0,
    "currency": "string",
    "totalIfIncluded": 0
  }
}
```

<h3 id="cartcompletion-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CartCompletionRS](#schemacartcompletionrs)|

<aside class="success">
This operation does not require authentication
</aside>

## checkTicket

<a id="opIdcheckTicket"></a>

`GET /{authtoken}/cms/checkticket`

*Use this method to validate a ticket QR code with an activity's event*

<h3 id="checkticket-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|eventId|query|string|false|Event Id|
|qrcode|query|string|false|ticket's QR Code |

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "ticket": {
    "id": "string",
    "qrcode": "string",
    "leadname": "string",
    "pax": 0,
    "checkedDate": 0,
    "checkedTime": 0,
    "checked": false,
    "comments": "string"
  },
  "validationMessage": "string",
  "valid": false
}
```

<h3 id="checkticket-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CheckTicketRS](#schemacheckticketrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getCircuitAvailabilityCalendar

<a id="opIdgetCircuitAvailabilityCalendar"></a>

`GET /{authtoken}/cms/circuitavailabilitycalendar`

*Use this method to know which hotels are available and their prices*

<h3 id="getcircuitavailabilitycalendar-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|circuit|query|string|false|The comma separated list of resorts you are interested in|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}
```

<h3 id="getcircuitavailabilitycalendar-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityAvailabilityCalendarRS](#schemagetactivityavailabilitycalendarrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getEventCheckList

<a id="opIdgetEventCheckList"></a>

`GET /{authtoken}/cms/eventchecklist`

*Use this method to get  all lists of available events in a given excursion date*

<h3 id="geteventchecklist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|date|query|integer(int32)|false|Activity Date|
|activityId|query|string|false|Activity Id|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "event": [
    {
      "id": "string",
      "name": "string",
      "activityId": "string"
    }
  ]
}
```

<h3 id="geteventchecklist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetEventCheckListRS](#schemageteventchecklistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getGenericAvailabilityCalendar

<a id="opIdgetGenericAvailabilityCalendar"></a>

`GET /{authtoken}/cms/genericavailabilitycalendar`

*Use this method to know which hotels are available and their prices*

<h3 id="getgenericavailabilitycalendar-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|product|query|string|false|The comma separated list of resorts you are interested in|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}
```

<h3 id="getgenericavailabilitycalendar-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetActivityAvailabilityCalendarRS](#schemagetactivityavailabilitycalendarrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getHotelAvailabilityCalendar

<a id="opIdgetHotelAvailabilityCalendar"></a>

`GET /{authtoken}/cms/hotelavailabilitycalendar`

*Use this method to know which hotels are available and their prices*

<h3 id="gethotelavailabilitycalendar-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|resorts|query|string|false|The comma separated list of resorts you are interested in|
|checkin|query|integer(int32)|false|The locale checkin date in YYYYMMDD format|
|checkout|query|integer(int32)|false|The locale checkout date in YYYYMMDD format|
|occupancies|query|string|false|List comma separated list of occupancies you need in <nr of rooms>x<pax>[-<age>]* format|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}
```

<h3 id="gethotelavailabilitycalendar-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetHotelAvailabilityCalendarRS](#schemagethotelavailabilitycalendarrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getInitialConfig

<a id="opIdgetInitialConfig"></a>

`GET /{authtoken}/cms/initialconfig`

*Use this method to know which hotels are available and their prices*

<h3 id="getinitialconfig-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "contactEmail": "string"
}
```

<h3 id="getinitialconfig-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetInitialConfigRS](#schemagetinitialconfigrs)|

<aside class="success">
This operation does not require authentication
</aside>

## loginToTicketsApp

<a id="opIdloginToTicketsApp"></a>

`POST /{authtoken}/cms/login`

*Use this method to login the tickets app*

> Body parameter

```json
{
  "user": "string",
  "password": "string"
}
```

<h3 id="logintoticketsapp-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetLoginRQ](#schemagetloginrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "authUser": "string",
  "message": "string",
  "logged": false
}
```

<h3 id="logintoticketsapp-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetLoginRS](#schemagetloginrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getOfflineCheckList

<a id="opIdgetOfflineCheckList"></a>

`GET /{authtoken}/cms/offlinechecklist`

*Use this method to get  all lists of available activities in a given date*

<h3 id="getofflinechecklist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ],
  "event": [
    {
      "id": "string",
      "name": "string",
      "activityId": "string"
    }
  ],
  "ticketList": [
    {
      "ticket": [
        {
          "id": "string",
          "qrcode": "string",
          "leadname": "string",
          "pax": 0,
          "checkedDate": 0,
          "checkedTime": 0,
          "checked": false,
          "comments": "string"
        }
      ],
      "totalTickets": 0,
      "checkedTickets": 0,
      "remainingTickets": 0,
      "totalPax": 0,
      "checkedPax": 0,
      "remainingPax": 0,
      "eventId": "string"
    }
  ]
}
```

<h3 id="getofflinechecklist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetOfflineCheckListRS](#schemagetofflinechecklistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getTerms

<a id="opIdgetTerms"></a>

`GET /{authtoken}/cms/terms`

*Use this method to get  terms and conditions from backoffice*

<h3 id="getterms-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "terms": "string",
  "unmailing": "string"
}
```

<h3 id="getterms-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetTermsRS](#schemagettermsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getTicketCheckList

<a id="opIdgetTicketCheckList"></a>

`GET /{authtoken}/cms/ticketchecklist`

*Use this method to get list of tickets for an event*

<h3 id="getticketchecklist-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|eventId|query|string|false|Event Id|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "ticket": {
    "ticket": [
      {
        "id": "string",
        "qrcode": "string",
        "leadname": "string",
        "pax": 0,
        "checkedDate": 0,
        "checkedTime": 0,
        "checked": false,
        "comments": "string"
      }
    ],
    "totalTickets": 0,
    "checkedTickets": 0,
    "remainingTickets": 0,
    "totalPax": 0,
    "checkedPax": 0,
    "remainingPax": 0,
    "eventId": "string"
  }
}
```

<h3 id="getticketchecklist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetTicketCheckListRS](#schemagetticketchecklistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## updateTickets

<a id="opIdupdateTickets"></a>

`POST /{authtoken}/cms/updatetickets`

*Use this method to syncronize data from offline tickets app*

> Body parameter

```json
{
  "userId": "string",
  "tickets": [
    {
      "id": "string",
      "qrcode": "string",
      "leadname": "string",
      "pax": 0,
      "checkedDate": 0,
      "checkedTime": 0,
      "checked": false,
      "comments": "string"
    }
  ]
}
```

<h3 id="updatetickets-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetUpdatedTicketsRQ](#schemagetupdatedticketsrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="updatetickets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GeUpdatedTicketsRS](#schemageupdatedticketsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getBooking

<a id="opIdgetBooking"></a>

`GET /{authtoken}/commons/booking/{bookingid}`

*Method to get a booking*

<h3 id="getbooking-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|bookingid|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "booking": {
    "bookingId": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string",
    "serviceType": "string",
    "serviceDescription": "string",
    "start": "string",
    "end": "string",
    "status": "string",
    "leadName": "string",
    "retail": 0,
    "net": 0,
    "currencyIsoCode": "string",
    "cancellationCost": [
      {
        "retail": 0,
        "net": 0,
        "gmttime": "string"
      }
    ],
    "commentsToProvider": "string",
    "privateComments": "string"
  }
}
```

<h3 id="getbooking-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetBookingRS](#schemagetbookingrs)|

<aside class="success">
This operation does not require authentication
</aside>

## cancelBooking

<a id="opIdcancelBooking"></a>

`DELETE /{authtoken}/commons/booking/{bookingid}`

*Method to cancel a service booking*

<h3 id="cancelbooking-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|bookingid|path|string|true|The service booking id you want to cancel|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="cancelbooking-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CancelBookingRS](#schemacancelbookingrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getBookingForWeb

<a id="opIdgetBookingForWeb"></a>

`GET /{authtoken}/commons/bookingforweb/{email}/{bookingid}`

*Method to get a booking*

<h3 id="getbookingforweb-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|email|path|string|true|none|
|bookingid|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "booking": {
    "bookingId": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string",
    "serviceType": "string",
    "serviceDescription": "string",
    "start": "string",
    "end": "string",
    "status": "string",
    "leadName": "string",
    "retail": 0,
    "net": 0,
    "currencyIsoCode": "string",
    "cancellationCost": [
      {
        "retail": 0,
        "net": 0,
        "gmttime": "string"
      }
    ],
    "commentsToProvider": "string",
    "privateComments": "string"
  }
}
```

<h3 id="getbookingforweb-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetBookingRS](#schemagetbookingrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getBookings

<a id="opIdgetBookings"></a>

`GET /{authtoken}/commons/bookings`

*Method to get a list of bookings*

<h3 id="getbookings-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|confirmedfrom|query|integer(int32)|false|Starting date you want service bookings confirmed from. In YYYYMMDD format|
|confirmedto|query|integer(int32)|false|Ending date you want service bookings confirmed to. In YYYYMMDD format|
|startingfrom|query|integer(int32)|false|Starting date you want service bookings starting from. In YYYYMMDD format|
|startingto|query|integer(int32)|false|Ending date you want service bookings starting from. In YYYYMMDD format|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookings": [
    {
      "bookingId": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string",
      "serviceType": "string",
      "serviceDescription": "string",
      "start": "string",
      "end": "string",
      "status": "string",
      "leadName": "string",
      "retail": 0,
      "net": 0,
      "currencyIsoCode": "string",
      "cancellationCost": [
        {
          "retail": 0,
          "net": 0,
          "gmttime": "string"
        }
      ],
      "commentsToProvider": "string",
      "privateComments": "string"
    }
  ]
}
```

<h3 id="getbookings-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetBookingsRS](#schemagetbookingsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getDataSheet

<a id="opIdgetDataSheet"></a>

`GET /{authtoken}/commons/datasheet/{resourceid}`

*Method to get a resource data sheet. E.g. descriptions, images, features*

<h3 id="getdatasheet-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|resourceid|path|string|true|none|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "values": [
    {
      "key": "string",
      "value": "string"
    }
  ]
}
```

<h3 id="getdatasheet-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetDataSheetRS](#schemagetdatasheetrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFile

<a id="opIdgetFile"></a>

`GET /{authtoken}/commons/file/{fileid}`

*Method to get a file*

<h3 id="getfile-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|fileid|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "file": {
    "fileId": "string",
    "bookings": [
      {
        "bookingId": "string",
        "created": "string",
        "createdBy": "string",
        "modified": "string",
        "serviceType": "string",
        "serviceDescription": "string",
        "start": "string",
        "end": "string",
        "status": "string",
        "leadName": "string",
        "retail": 0,
        "net": 0,
        "currencyIsoCode": "string",
        "cancellationCost": [
          {
            "retail": 0,
            "net": 0,
            "gmttime": "string"
          }
        ],
        "commentsToProvider": "string",
        "privateComments": "string"
      }
    ],
    "totalPrice": {
      "currencyIsoCode": "string",
      "value": 0
    },
    "leadName": "string",
    "email": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string"
  }
}
```

<h3 id="getfile-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetFileRS](#schemagetfilers)|

<aside class="success">
This operation does not require authentication
</aside>

## cancelFile

<a id="opIdcancelFile"></a>

`DELETE /{authtoken}/commons/file/{fileid}`

*Method to cancel a service file*

<h3 id="cancelfile-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|fileid|path|string|true|The service file id you want to cancel|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="cancelfile-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CancelFileRS](#schemacancelfilers)|

<aside class="success">
This operation does not require authentication
</aside>

## getFileForWeb

<a id="opIdgetFileForWeb"></a>

`GET /{authtoken}/commons/fileforweb/{email}/{fileid}`

*Method to get a file*

<h3 id="getfileforweb-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|email|path|string|true|none|
|fileid|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "file": {
    "fileId": "string",
    "bookings": [
      {
        "bookingId": "string",
        "created": "string",
        "createdBy": "string",
        "modified": "string",
        "serviceType": "string",
        "serviceDescription": "string",
        "start": "string",
        "end": "string",
        "status": "string",
        "leadName": "string",
        "retail": 0,
        "net": 0,
        "currencyIsoCode": "string",
        "cancellationCost": [
          {
            "retail": 0,
            "net": 0,
            "gmttime": "string"
          }
        ],
        "commentsToProvider": "string",
        "privateComments": "string"
      }
    ],
    "totalPrice": {
      "currencyIsoCode": "string",
      "value": 0
    },
    "leadName": "string",
    "email": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string"
  }
}
```

<h3 id="getfileforweb-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetFileRS](#schemagetfilers)|

<aside class="success">
This operation does not require authentication
</aside>

## getFiles

<a id="opIdgetFiles"></a>

`GET /{authtoken}/commons/files`

*Method to get a list of files*

<h3 id="getfiles-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|confirmedfrom|query|integer(int32)|false|Starting date you want service file confirmed from. In YYYYMMDD format|
|confirmedto|query|integer(int32)|false|Ending date you want service files confirmed to. In YYYYMMDD format|
|startingfrom|query|integer(int32)|false|Starting date you want service files starting from. In YYYYMMDD format|
|startingto|query|integer(int32)|false|Ending date you want service files starting from. In YYYYMMDD format|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "files": [
    {
      "fileId": "string",
      "bookings": [
        {
          "bookingId": "string",
          "created": "string",
          "createdBy": "string",
          "modified": "string",
          "serviceType": "string",
          "serviceDescription": "string",
          "start": "string",
          "end": "string",
          "status": "string",
          "leadName": "string",
          "retail": 0,
          "net": 0,
          "currencyIsoCode": "string",
          "cancellationCost": [
            {
              "retail": 0,
              "net": 0,
              "gmttime": "string"
            }
          ],
          "commentsToProvider": "string",
          "privateComments": "string"
        }
      ],
      "totalPrice": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "leadName": "string",
      "email": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string"
    }
  ]
}
```

<h3 id="getfiles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetFilesRS](#schemagetfilesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFromLocator

<a id="opIdgetFromLocator"></a>

`GET /{authtoken}/commons/fromlocator/{locatorid}`

*get data from a Locator*

<h3 id="getfromlocator-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|locatorid|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "leadName": "string",
  "email": "string",
  "destination": "string",
  "destinationName": "string",
  "checkin": 0,
  "checkout": 0,
  "occupation": "string",
  "pax": 0,
  "origen": "string",
  "origenName": "string"
}
```

<h3 id="getfromlocator-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetLocatorRS](#schemagetlocatorrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getMealPlans

<a id="opIdgetMealPlans"></a>

`GET /{authtoken}/commons/mealplans`

*Method to get a list of board types*

<h3 id="getmealplans-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "mealPlans": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}
```

<h3 id="getmealplans-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[MealPlansListRS](#schemamealplanslistrs)|

<aside class="success">
This operation does not require authentication
</aside>

## renewToken

<a id="opIdrenewToken"></a>

`GET /{authtoken}/commons/newtoken`

*Use this method to get or renew your authentication token*

<h3 id="renewtoken-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|user|query|string|false|none|

> Example responses

> 200 Response

```json
"string"
```

<h3 id="renewtoken-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|string|

<aside class="success">
This operation does not require authentication
</aside>

## getPortfolio

<a id="opIdgetPortfolio"></a>

`GET /{authtoken}/commons/portfolio`

*Method to get the whole product tree*

<h3 id="getportfolio-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "countries": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "urlFriendlyName": "string",
      "states": [
        {
          "resourceId": "string",
          "name": {
            "property1": "string",
            "property2": "string"
          },
          "urlFriendlyName": "string",
          "cities": [
            {
              "resourceId": "string",
              "name": {
                "property1": "string",
                "property2": "string"
              },
              "urlFriendlyName": "string",
              "resources": [
                {
                  "resourceId": "string",
                  "name": {
                    "property1": "string",
                    "property2": "string"
                  },
                  "type": "string",
                  "longitude": "string",
                  "latitude": "string",
                  "description": {
                    "property1": "string",
                    "property2": "string"
                  }
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

<h3 id="getportfolio-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetPortfolioRS](#schemagetportfoliors)|

<aside class="success">
This operation does not require authentication
</aside>

## searchPortfolio

<a id="opIdsearchPortfolio"></a>

`GET /{authtoken}/commons/search`

*Method to get the whole product tree*

<h3 id="searchportfolio-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|2 chars language iso code|
|product|query|string|false|none|
|query|query|string|false|Search text|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "matches": [
    {
      "resourceId": "string",
      "name": "string",
      "description": "string",
      "metadata": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="searchportfolio-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[SearchPortfolioRS](#schemasearchportfoliors)|

<aside class="success">
This operation does not require authentication
</aside>

## searchTransferPoints

<a id="opIdsearchTransferPoints"></a>

`GET /{authtoken}/commons/searchtransferpoints`

*Method to get the transfer points*

<h3 id="searchtransferpoints-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|2 chars language iso code|
|query|query|string|false|Search text|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "matches": [
    {
      "resourceId": "string",
      "name": "string",
      "description": "string",
      "metadata": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="searchtransferpoints-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[SearchPortfolioRS](#schemasearchportfoliors)|

<aside class="success">
This operation does not require authentication
</aside>

## getAirportsByName

<a id="opIdgetAirportsByName"></a>

`GET /{authtoken}/flight/airportsbyname`

*Get airports list*

Use this method to get all available airports

<h3 id="getairportsbyname-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|text|query|string|false|The airport id to get destinations|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "airports": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getairportsbyname-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAirportsRS](#schemagetairportsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAvailableFlights

<a id="opIdgetAvailableFlights"></a>

`GET /{authtoken}/flight/available`

*Get available transfers*

Use this method to know which transfers are available and their prices

<h3 id="getavailableflights-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|origin|query|string|false|Flight origin, airport IATA code|
|destination|query|string|false|Flight destination, airport IATA code|
|adults|query|integer(int32)|false|Number of adults|
|children|query|integer(int32)|false|Number of children|
|infants|query|integer(int32)|false|Number of infants|
|departuredate|query|integer(int32)|false|Locale date for the departure, in YYYYMMDD format|
|returndate|query|integer(int32)|false|Locale date for the return, in YYYYMMDD format|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "currency": "string",
  "departureBestPrices": [
    {
      "formattedDate": "string",
      "date": "string",
      "price": 0,
      "current": false
    }
  ],
  "departureFlights": [
    {
      "economyKey": "string",
      "businessKey": "string",
      "origin": "string",
      "destination": "string",
      "company": "string",
      "companyLogo": "string",
      "departureDate": "string",
      "departureTime": "string",
      "arrivalDate": "string",
      "arrivalTime": "string",
      "duration": "string",
      "operatedBy": "string",
      "economyPrice": 0,
      "businessPrice": 0,
      "segments": [
        {
          "originId": "string",
          "originDescription": "string",
          "destinationId": "string",
          "destinationDescription": "string",
          "company": "string",
          "companyLogo": "string",
          "flightNumber": "string",
          "airplane": "string",
          "departureDate": "string",
          "departureTime": "string",
          "arrivalDate": "string",
          "arrivalTime": "string",
          "duration": "string"
        }
      ]
    }
  ],
  "returnBestPrices": [
    {
      "formattedDate": "string",
      "date": "string",
      "price": 0,
      "current": false
    }
  ],
  "returnFlights": [
    {
      "economyKey": "string",
      "businessKey": "string",
      "origin": "string",
      "destination": "string",
      "company": "string",
      "companyLogo": "string",
      "departureDate": "string",
      "departureTime": "string",
      "arrivalDate": "string",
      "arrivalTime": "string",
      "duration": "string",
      "operatedBy": "string",
      "economyPrice": 0,
      "businessPrice": 0,
      "segments": [
        {
          "originId": "string",
          "originDescription": "string",
          "destinationId": "string",
          "destinationDescription": "string",
          "company": "string",
          "companyLogo": "string",
          "flightNumber": "string",
          "airplane": "string",
          "departureDate": "string",
          "departureTime": "string",
          "arrivalDate": "string",
          "arrivalTime": "string",
          "duration": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getavailableflights-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableFlightsRS](#schemagetavailableflightsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookFlight

<a id="opIdbookFlight"></a>

`POST /{authtoken}/flight/booking`

*Confirm transfer booking*

Use this method to confirm a transfer service booking

> Body parameter

```json
{
  "fileId": "string",
  "departureKey": "string",
  "returnKey": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "contactPhone": "string",
  "email": "string",
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "promoCode": "string",
  "mailingUnwanted": false,
  "pax": [
    {
      "firstName": "string",
      "surname": "string",
      "age": 0,
      "birthDate": 0,
      "type": "string",
      "documentType": "string",
      "documentId": "string",
      "groupId": "string"
    }
  ]
}
```

<h3 id="bookflight-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookFlightRQ](#schemabookflightrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="bookflight-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookFlightRS](#schemabookflightrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getDestinationAirports

<a id="opIdgetDestinationAirports"></a>

`GET /{authtoken}/flight/destinationairports`

*Get airports list*

Use this method to get all available airports

<h3 id="getdestinationairports-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|originAirportId|query|string|false|The airport id to get destinations|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "airports": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getdestinationairports-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAirportsRS](#schemagetairportsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getOriginAirports

<a id="opIdgetOriginAirports"></a>

`GET /{authtoken}/flight/originairports`

*Get airports list*

Use this method to get all available airports

<h3 id="getoriginairports-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|destinationAirportId|query|string|false|The airport id to get destinations|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "airports": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getoriginairports-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAirportsRS](#schemagetairportsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFlightPriceDetails

<a id="opIdgetFlightPriceDetails"></a>

`GET /{authtoken}/flight/pricedetails/{departurekey}/{returnkey}`

*Get transfer price details*

Use this method to guess cancellation costs and important remarks

<h3 id="getflightpricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|departurekey|path|string|true|The hotel price key, as provided in the /transfer/available step|
|returnkey|path|string|true|none|
|language|query|string|false|none|
|promoCode|query|string|false|Discount coupons|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "availableSupplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "arrivalInstructions": "string",
  "departureInstructions": "string",
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}
```

<h3 id="getflightpricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetFlightPriceDetailsRS](#schemagetflightpricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAvailableGenerics

<a id="opIdgetAvailableGenerics"></a>

`GET /{authtoken}/generic/available`

*Get available generic products*

you get a list of the available generic products by type

<h3 id="getavailablegenerics-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|destination|query|string|false|none|
|productType|query|string|false|none|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableGenerics": [
    {
      "genericId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "type": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getavailablegenerics-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableGenericsRS](#schemagetavailablegenericsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookGeneric

<a id="opIdbookGeneric"></a>

`POST /{authtoken}/generic/booking`

*Book a Generic Product*

Here you can confirm Generic booking. You must provide a price key and some additional data (lead name, comments, ...)

> Body parameter

```json
{
  "fileId": "string",
  "key": "string",
  "supplementIds": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "coupon": "string",
  "mailingUnwanted": false
}
```

<h3 id="bookgeneric-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookGenericRQ](#schemabookgenericrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="bookgeneric-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookGenericRS](#schemabookgenericrs)|

<aside class="success">
This operation does not require authentication
</aside>

## checkGeneric

<a id="opIdcheckGeneric"></a>

`GET /{authtoken}/generic/check/{key}`

*Check generic availability*

By passing a price key you get extra info

<h3 id="checkgeneric-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The activity price key, as provided in the /activity/available step|
|adults|query|integer(int32)|false|none|
|children|query|integer(int32)|false|none|
|units|query|integer(int32)|false|none|
|start|query|integer(int32)|false|none|
|end|query|integer(int32)|false|none|
|language|query|string|false|none|
|variant|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}
```

<h3 id="checkgeneric-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[CheckGenericRS](#schemacheckgenericrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFilteredGeneric

<a id="opIdgetFilteredGeneric"></a>

`GET /{authtoken}/generic/filter`

*Get available generic filtered*

By passing a resort and holidays dates you get a list of the available generic products

<h3 id="getfilteredgeneric-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|destination|query|string|false|List of type of product to filter by separated by ,|
|productType|query|string|false|none|
|language|query|string|false|none|
|labels|query|string|false|none|
|minprice|query|number(double)|false|Min price range to filter|
|maxprice|query|number(double)|false|Max price range to filter|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableGenerics": [
    {
      "genericId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "type": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}
```

<h3 id="getfilteredgeneric-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableGenericsRS](#schemagetavailablegenericsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getGenericPriceDetails

<a id="opIdgetGenericPriceDetails"></a>

`GET /{authtoken}/generic/pricedetails/{key}`

*Get generic price details*

By passing a price key you get extra info

<h3 id="getgenericpricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The generic product price key, as provided in the /genericty/available step|
|language|query|string|false|none|
|supplements|query|string|false|none|
|coupon|query|string|false|Discount coupons|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "couponMsg": "string",
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}
```

<h3 id="getgenericpricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetGenericPriceDetailsRS](#schemagetgenericpricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getGenericRates

<a id="opIdgetGenericRates"></a>

`GET /{authtoken}/generic/rates/{productId}`

*Get generic rates*

By passing a price key you get extra info

<h3 id="getgenericrates-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|productId|path|string|true|The activity price key, as provided in the /activity/available step|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "dateDependant": false,
  "datesRangeDependant": false,
  "unitsDependant": false,
  "adultsDependant": false,
  "childrenDependant": false,
  "variantDependant": false,
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ]
}
```

<h3 id="getgenericrates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetGenericRatesRS](#schemagetgenericratesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAvailableHotels

<a id="opIdgetAvailableHotels"></a>

`GET /{authtoken}/hotel/available`

*Get available hotels*

Use this method to know which hotels are available and their prices

<h3 id="getavailablehotels-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|2 chars language iso code|
|resorts|query|string|false|The comma separated list of resorts you are interested in|
|checkin|query|integer(int32)|false|The locale checkin date in YYYYMMDD format|
|checkout|query|integer(int32)|false|The locale checkout date in YYYYMMDD format|
|occupancies|query|string|false|List comma separated list of occupancies you need in <nr of rooms>x<pax>[-<age>]* format. E.g.: 2x4-10-6-2,1x2 means 2 rooms occupied by 4 pax where 3 of them are 10, 6 and 2 years old and 1 room occupied by 2 pax|
|includestaticinfo|query|boolean|false|Set to true if you want the response to include static info (hotel description, main hotel image, ...). If false (default value) static info will not be included in order to make the response lighter|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "hotels": [
    {
      "hotelId": "string",
      "hotelName": "string",
      "hotelCategoryId": "string",
      "hotelCategoryName": "string",
      "stars": 0,
      "keys": 0,
      "longitude": "string",
      "latitude": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "address": "string",
      "mainImage": "string"
    }
  ],
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0
}
```

<h3 id="getavailablehotels-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableHotelsRS](#schemagetavailablehotelsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookHotel

<a id="opIdbookHotel"></a>

`POST /{authtoken}/hotel/booking`

*Confirm hotel booking*

Use this method to confirm a hotel service

> Body parameter

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "boardId": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ]
    }
  ],
  "promoCode": "string",
  "fileId": "string",
  "bookingReference": "string",
  "leadName": "string",
  "email": "string",
  "phoneNumber": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "captchaToken": "string",
  "mailingUnwanted": false
}
```

<h3 id="bookhotel-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookHotelRQ](#schemabookhotelrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="bookhotel-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookHotelRS](#schemabookhotelrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFilteredHotels

<a id="opIdgetFilteredHotels"></a>

`GET /{authtoken}/hotel/filter`

*Get available hotels filtered*

Use this method to filter hotels available and their prices

<h3 id="getfilteredhotels-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|language|query|string|false|2 chars language iso code|
|resorts|query|string|false|The comma separated list of resorts you are interested in|
|checkin|query|integer(int32)|false|The locale checkin date in YYYYMMDD format|
|checkout|query|integer(int32)|false|The locale checkout date in YYYYMMDD format|
|occupancies|query|string|false|List comma separated list of occupancies you need in <nr of rooms>x<pax>[-<age>]* format|
|categories|query|string|false|List of categories selected to filter|
|minprice|query|number(double)|false|Min price range to filter|
|maxprice|query|number(double)|false|Max price range to filter|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "hotels": [
    {
      "hotelId": "string",
      "hotelName": "string",
      "hotelCategoryId": "string",
      "hotelCategoryName": "string",
      "stars": 0,
      "keys": 0,
      "longitude": "string",
      "latitude": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "address": "string",
      "mainImage": "string"
    }
  ],
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0
}
```

<h3 id="getfilteredhotels-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableHotelsRS](#schemagetavailablehotelsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getHotelPriceDetails

<a id="opIdgetHotelPriceDetails"></a>

`POST /{authtoken}/hotel/pricedetails`

*Get hotel price details*

Use this methos to guess cancellation costs and important remarks regarding a price

> Body parameter

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "boardId": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ]
    }
  ],
  "promoCode": "string"
}
```

<h3 id="gethotelpricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetHotelPriceDetailsRQ](#schemagethotelpricedetailsrq)|false|All the info needed to retrieve |

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "status": "string",
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "roomName": "string",
      "boardId": "string",
      "boardName": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ],
      "retailPrice": 0,
      "netPrice": 0,
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false,
      "availableSupplements": [
        {
          "id": "string",
          "description": "string",
          "price": 0
        }
      ]
    }
  ],
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "cancellationFreeDate": "string",
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "promoCodeMsg": "string",
  "terms": "string",
  "mailingUnwantedText": "string"
}
```

<h3 id="gethotelpricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetHotelPriceDetailsRS](#schemagethotelpricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getRates

<a id="opIdgetRates"></a>

`POST /{authtoken}/hotel/rates`

*Get available hotel rates*

Use this method to get available room rates for a hotel

> Body parameter

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "occupancies": "string"
}
```

<h3 id="getrates-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[GetHotelRatesRQ](#schemagethotelratesrq)|false|All the info needed to retrieve all available rates for a hotel and occupancies|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "currencyIsoCode": "string",
  "rates": [
    {
      "numberOfRooms": 0,
      "paxPerRoom": 0,
      "ages": [
        0
      ],
      "options": [
        {
          "roomId": "string",
          "roomName": "string",
          "roomDescription": "string",
          "image": "string",
          "prices": [
            {
              "boardBasisId": "string",
              "boardBasisName": "string",
              "retailPrice": 0,
              "netPrice": 0,
              "offer": false,
              "offerText": "string",
              "onRequest": false,
              "onRequestText": "string",
              "nonRefundable": false,
              "rateId": "string"
            }
          ],
          "allotment": 0
        }
      ]
    }
  ]
}
```

<h3 id="getrates-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetHotelRatesRS](#schemagethotelratesrs)|

<aside class="success">
This operation does not require authentication
</aside>

## ingestHotels

<a id="opIdingestHotels"></a>

`POST /{authtoken}/ingestion/hotels`

*Use this method to upload a list of hotel (and transfer) bookings*

> Body parameter

```json
[
  {
    "agencyId": "string",
    "agencyReference": "string",
    "additional": false,
    "currency": "string",
    "value": 0,
    "passengerName": "string",
    "phone": "string",
    "email": "string",
    "adults": 0,
    "children": 0,
    "babies": 0,
    "extras": 0,
    "ages": "string",
    "comments": "string",
    "hotel": "string",
    "hotelCountry": "string",
    "hotelDestination": "string",
    "hotelZone": "string",
    "hotelName": "string",
    "hotelAddress": "string",
    "numberOfRooms": 0,
    "room": "string",
    "board": "string",
    "serviceType": "string",
    "vehicle": "string",
    "arrivalStatus": "string",
    "arrivalAirport": "string",
    "arrivalFlightDate": "string",
    "arrivalFlightTime": "string",
    "arrivalFlightNumber": "string",
    "arrivalFlightCompany": "string",
    "arrivalOriginAirport": "string",
    "arrivalComments": "string",
    "arrivalPickupDate": "string",
    "arrivalPickupTime": "string",
    "departureStatus": "string",
    "departureAirport": "string",
    "departureFlightDate": "string",
    "departureFlightTime": "string",
    "departureFlightNumber": "string",
    "departureFlightCompany": "string",
    "departureDestinationAirport": "string",
    "departureComments": "string",
    "departurePickupDate": "string",
    "departurePickupTime": "string"
  }
]
```

<h3 id="ingesthotels-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[HotelRQ](#schemahotelrq)|false|List of hotel requests|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="ingesthotels-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[HotelsIngestionRS](#schemahotelsingestionrs)|

<aside class="success">
This operation does not require authentication
</aside>

## ingestTransfers

<a id="opIdingestTransfers"></a>

`POST /{authtoken}/ingestion/transfers`

*Use this method to upload a list of transfer bookings*

> Body parameter

```json
[
  {
    "agencyId": "string",
    "agencyReference": "string",
    "currency": "string",
    "value": 0,
    "serviceType": "string",
    "vehicle": "string",
    "passengerName": "string",
    "phone": "string",
    "email": "string",
    "adults": 0,
    "children": 0,
    "babies": 0,
    "extras": 0,
    "comments": "string",
    "arrivalStatus": "string",
    "arrivalAirport": "string",
    "arrivalZone": "string",
    "arrivalAddress": "string",
    "arrivalFlightDate": "string",
    "arrivalFlightTime": "string",
    "arrivalFlightNumber": "string",
    "arrivalFlightCompany": "string",
    "arrivalOriginAirport": "string",
    "arrivalComments": "string",
    "arrivalPickupDate": "string",
    "arrivalPickupTime": "string",
    "departureStatus": "string",
    "departureAirport": "string",
    "departureZone": "string",
    "departureAddress": "string",
    "departureFlightDate": "string",
    "departureFlightTime": "string",
    "departureFlightNumber": "string",
    "departureFlightCompany": "string",
    "departureDestinationAirport": "string",
    "departureComments": "string",
    "departurePickupDate": "string",
    "departurePickupTime": "string"
  }
]
```

<h3 id="ingesttransfers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[TransferRQ](#schematransferrq)|false|List of transfers requests|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}
```

<h3 id="ingesttransfers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[TransfersIngestionRS](#schematransfersingestionrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAirports

<a id="opIdgetAirports"></a>

`GET /{authtoken}/transfer/airports`

*Get airports list*

Use this method to get all available airports

<h3 id="getairports-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "airports": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getairports-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAirportsRS](#schemagetairportsrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getDestinationsForAirport

<a id="opIdgetDestinationsForAirport"></a>

`GET /{authtoken}/transfer/airports/{airportId}/destinations`

*Get destinations for airport*

Use this method to get all available destinations from an airport key

<h3 id="getdestinationsforairport-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|airportId|path|string|true|The airport key to get destinations|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "destination": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getdestinationsforairport-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetDestinationRS](#schemagetdestinationrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getAvailabeTransfers

<a id="opIdgetAvailabeTransfers"></a>

`GET /{authtoken}/transfer/available`

*Get available transfers*

Use this method to know which transfers are available and their prices

<h3 id="getavailabetransfers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|from|query|string|false|Transfer origin, as got in the getportfolio response|
|to|query|string|false|Transfer destination, as got in the getportfolio response|
|pax|query|integer(int32)|false|Number of pax|
|bikes|query|integer(int32)|false|Number of bikes|
|golfs|query|integer(int32)|false|Number of golf baggages|
|skis|query|integer(int32)|false|Number of skis|
|bigs|query|integer(int32)|false|Number of big luggages not bikes neither golf baggages|
|wheelchairs|query|integer(int32)|false|Number of wheel chairs|
|incomingdate|query|integer(int32)|false|Locale date for the incoming side of the transfer, in YYYYMMDD format|
|outgoingdate|query|integer(int32)|false|Locale date for the outgoing / return side of the transfer, in YYYYMMDD format|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableTransfers": [
    {
      "key": "string",
      "type": "string",
      "vehicle": "string",
      "description": "string",
      "image": "string",
      "total": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false
    }
  ]
}
```

<h3 id="getavailabetransfers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableTransfersRS](#schemagetavailabletransfersrs)|

<aside class="success">
This operation does not require authentication
</aside>

## bookTransfer

<a id="opIdbookTransfer"></a>

`POST /{authtoken}/transfer/booking`

*Confirm transfer booking*

Use this method to confirm a transfer service booking

> Body parameter

```json
{
  "fileId": "string",
  "key": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "incomingFlightNumber": "string",
  "incomingFlightTime": 0,
  "incomingFlightOrigin": "string",
  "outgoingFlightNumber": "string",
  "outgoingFlightTime": 0,
  "outgoingFlightDestination": "string",
  "contactPhone": "string",
  "email": "string",
  "bike": 0,
  "golf": 0,
  "ski": 0,
  "wheelchair": 0,
  "bigLuggages": 0,
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "promoCode": "string",
  "mailingUnwanted": false
}
```

<h3 id="booktransfer-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|body|body|[BookTransferRQ](#schemabooktransferrq)|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}
```

<h3 id="booktransfer-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[BookTransferRS](#schemabooktransferrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getDestinations

<a id="opIdgetDestinations"></a>

`GET /{authtoken}/transfer/destinations`

*Get all destinations*

Use this method to get all available destinations from an airport key

<h3 id="getdestinations-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "destination": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}
```

<h3 id="getdestinations-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetDestinationRS](#schemagetdestinationrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getFilteredTransfers

<a id="opIdgetFilteredTransfers"></a>

`GET /{authtoken}/transfer/filter`

*Aget available transfers filtered*

Use this method to filter transfers wich are available and their prices

<h3 id="getfilteredtransfers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|from|query|string|false|Transfer origin, as got in the getportfolio response|
|to|query|string|false|Transfer destination, as got in the getportfolio response|
|pax|query|integer(int32)|false|Number of pax|
|bikes|query|integer(int32)|false|Number of bikes|
|golfs|query|integer(int32)|false|Number of golf baggages|
|skis|query|integer(int32)|false|Number of skis|
|bigs|query|integer(int32)|false|Number of big luggages not bikes neither golf baggages|
|wheelchairs|query|integer(int32)|false|Number of wheel chairs|
|incomingdate|query|integer(int32)|false|Locale date for the incoming side of the transfer, in YYYYMMDD format|
|outgoingdate|query|integer(int32)|false|Locale date for the outgoing / return side of the transfer, in YYYYMMDD format|
|transfertype|query|string|false|none|
|minprice|query|number(double)|false|Min price range to filter|
|maxprice|query|number(double)|false|Max price range to filter|
|language|query|string|false|none|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableTransfers": [
    {
      "key": "string",
      "type": "string",
      "vehicle": "string",
      "description": "string",
      "image": "string",
      "total": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false
    }
  ]
}
```

<h3 id="getfilteredtransfers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetAvailableTransfersRS](#schemagetavailabletransfersrs)|

<aside class="success">
This operation does not require authentication
</aside>

## getTransferPriceDetails

<a id="opIdgetTransferPriceDetails"></a>

`GET /{authtoken}/transfer/pricedetails/{key}`

*Get transfer price details*

Use this method to guess cancellation costs and important remarks

<h3 id="gettransferpricedetails-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|authtoken|path|string|true|Auth token provided by your partner, and possibly renewed by using the /commons/newtoken method|
|key|path|string|true|The hotel price key, as provided in the /transfer/available step|
|language|query|string|false|none|
|supplements|query|string|false|none|
|promoCode|query|string|false|Discount coupons|

> Example responses

> 200 Response

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "availableSupplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "arrivalInstructions": "string",
  "departureInstructions": "string",
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}
```

<h3 id="gettransferpricedetails-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[GetTransferPriceDetailsRS](#schemagettransferpricedetailsrs)|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_GetFileRS">GetFileRS</h2>
<!-- backwards compatibility -->
<a id="schemagetfilers"></a>
<a id="schema_GetFileRS"></a>
<a id="tocSgetfilers"></a>
<a id="tocsgetfilers"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "file": {
    "fileId": "string",
    "bookings": [
      {
        "bookingId": "string",
        "created": "string",
        "createdBy": "string",
        "modified": "string",
        "serviceType": "string",
        "serviceDescription": "string",
        "start": "string",
        "end": "string",
        "status": "string",
        "leadName": "string",
        "retail": 0,
        "net": 0,
        "currencyIsoCode": "string",
        "cancellationCost": [
          {
            "retail": 0,
            "net": 0,
            "gmttime": "string"
          }
        ],
        "commentsToProvider": "string",
        "privateComments": "string"
      }
    ],
    "totalPrice": {
      "currencyIsoCode": "string",
      "value": 0
    },
    "leadName": "string",
    "email": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string"
  }
}

```

Container for the get files response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|file|[File](#schemafile)|false|none|none|

<h2 id="tocS_HotelsIngestionRS">HotelsIngestionRS</h2>
<!-- backwards compatibility -->
<a id="schemahotelsingestionrs"></a>
<a id="schema_HotelsIngestionRS"></a>
<a id="tocShotelsingestionrs"></a>
<a id="tocshotelsingestionrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

Response for the transfer ingestion request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_GetAvailableFlightsRS">GetAvailableFlightsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailableflightsrs"></a>
<a id="schema_GetAvailableFlightsRS"></a>
<a id="tocSgetavailableflightsrs"></a>
<a id="tocsgetavailableflightsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "currency": "string",
  "departureBestPrices": [
    {
      "formattedDate": "string",
      "date": "string",
      "price": 0,
      "current": false
    }
  ],
  "departureFlights": [
    {
      "economyKey": "string",
      "businessKey": "string",
      "origin": "string",
      "destination": "string",
      "company": "string",
      "companyLogo": "string",
      "departureDate": "string",
      "departureTime": "string",
      "arrivalDate": "string",
      "arrivalTime": "string",
      "duration": "string",
      "operatedBy": "string",
      "economyPrice": 0,
      "businessPrice": 0,
      "segments": [
        {
          "originId": "string",
          "originDescription": "string",
          "destinationId": "string",
          "destinationDescription": "string",
          "company": "string",
          "companyLogo": "string",
          "flightNumber": "string",
          "airplane": "string",
          "departureDate": "string",
          "departureTime": "string",
          "arrivalDate": "string",
          "arrivalTime": "string",
          "duration": "string"
        }
      ]
    }
  ],
  "returnBestPrices": [
    {
      "formattedDate": "string",
      "date": "string",
      "price": 0,
      "current": false
    }
  ],
  "returnFlights": [
    {
      "economyKey": "string",
      "businessKey": "string",
      "origin": "string",
      "destination": "string",
      "company": "string",
      "companyLogo": "string",
      "departureDate": "string",
      "departureTime": "string",
      "arrivalDate": "string",
      "arrivalTime": "string",
      "duration": "string",
      "operatedBy": "string",
      "economyPrice": 0,
      "businessPrice": 0,
      "segments": [
        {
          "originId": "string",
          "originDescription": "string",
          "destinationId": "string",
          "destinationDescription": "string",
          "company": "string",
          "companyLogo": "string",
          "flightNumber": "string",
          "airplane": "string",
          "departureDate": "string",
          "departureTime": "string",
          "arrivalDate": "string",
          "arrivalTime": "string",
          "duration": "string"
        }
      ]
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|currency|string|false|none|none|
|departureBestPrices|[[FlightBestPrice](#schemaflightbestprice)]|false|none|none|
|departureFlights|[[AvailableFlight](#schemaavailableflight)]|false|none|none|
|returnBestPrices|[[FlightBestPrice](#schemaflightbestprice)]|false|none|none|
|returnFlights|[[AvailableFlight](#schemaavailableflight)]|false|none|none|

<h2 id="tocS_PriceLine">PriceLine</h2>
<!-- backwards compatibility -->
<a id="schemapriceline"></a>
<a id="schema_PriceLine"></a>
<a id="tocSpriceline"></a>
<a id="tocspriceline"></a>

```json
{
  "description": "string",
  "total": 0
}

```

holder for a price detail line

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|description|string|false|none|Price line description|
|total|number(double)|false|none|Price line total|

<h2 id="tocS_Payments">Payments</h2>
<!-- backwards compatibility -->
<a id="schemapayments"></a>
<a id="schema_Payments"></a>
<a id="tocSpayments"></a>
<a id="tocspayments"></a>

```json
{
  "amount": "string",
  "paymentMethod": {
    "key": "string",
    "name": "string",
    "currencyIsoCode": "string"
  },
  "currency": {
    "name": "string",
    "value": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|amount|string|false|none|none|
|paymentMethod|[PaymentMethod](#schemapaymentmethod)|false|none|none|
|currency|[CurrencyChange](#schemacurrencychange)|false|none|none|

<h2 id="tocS_Remark">Remark</h2>
<!-- backwards compatibility -->
<a id="schemaremark"></a>
<a id="schema_Remark"></a>
<a id="tocSremark"></a>
<a id="tocsremark"></a>

```json
{
  "type": "string",
  "text": "string"
}

```

A remoark is some important information which 

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|false|none|Type of remark. Possible values are IMPORTANT, NORMAL|
|text|string|false|none|Text which should be visible for the customer|

<h2 id="tocS_ActivityAvailabilityCalendarDay">ActivityAvailabilityCalendarDay</h2>
<!-- backwards compatibility -->
<a id="schemaactivityavailabilitycalendarday"></a>
<a id="schema_ActivityAvailabilityCalendarDay"></a>
<a id="tocSactivityavailabilitycalendarday"></a>
<a id="tocsactivityavailabilitycalendarday"></a>

```json
{
  "id": 0,
  "posInWeek": 0,
  "day": 0,
  "date": "string",
  "styleName": "string",
  "blank": false
}

```

A calendar day

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int32)|false|none|none|
|posInWeek|integer(int32)|false|none|none|
|day|integer(int32)|false|none|none|
|date|string|false|none|none|
|styleName|string|false|none|none|
|blank|boolean|false|none|none|

<h2 id="tocS_GetTransferPriceDetailsRS">GetTransferPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagettransferpricedetailsrs"></a>
<a id="schema_GetTransferPriceDetailsRS"></a>
<a id="tocSgettransferpricedetailsrs"></a>
<a id="tocsgettransferpricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "availableSupplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "arrivalInstructions": "string",
  "departureInstructions": "string",
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}

```

Holder for the transfer price details response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|priceBreakdown|[[PriceLine](#schemapriceline)]|false|none|Price detail, in form of lines|
|total|[Price](#schemaprice)|false|none|Holder for price|
|availableSupplements|[[Supplement](#schemasupplement)]|false|none|Available supplements|
|arrivalInstructions|string|false|none|Arrival instructions|
|departureInstructions|string|false|none|Departure instructions|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs for this activity|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|terms|string|false|none|Text for terms and conditions|
|mailingUnwantedText|string|false|none|Text for rejecting or acepting mailing|
|cancellationFreeDate|string|false|none|No cancellation costs until this date, in yyyy-MM-dd format|

<h2 id="tocS_EventCheckItem">EventCheckItem</h2>
<!-- backwards compatibility -->
<a id="schemaeventcheckitem"></a>
<a id="schema_EventCheckItem"></a>
<a id="tocSeventcheckitem"></a>
<a id="tocseventcheckitem"></a>

```json
{
  "id": "string",
  "name": "string",
  "activityId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|activityId|string|false|none|none|

<h2 id="tocS_GetProductionCentersListRS">GetProductionCentersListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetproductioncenterslistrs"></a>
<a id="schema_GetProductionCentersListRS"></a>
<a id="tocSgetproductioncenterslistrs"></a>
<a id="tocsgetproductioncenterslistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "productionCenters": [
    {
      "id": "string",
      "name": "string",
      "hotelName": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|productionCenters|[[ProductionCenter](#schemaproductioncenter)]|false|none|none|

<h2 id="tocS_GetLocatorRS">GetLocatorRS</h2>
<!-- backwards compatibility -->
<a id="schemagetlocatorrs"></a>
<a id="schema_GetLocatorRS"></a>
<a id="tocSgetlocatorrs"></a>
<a id="tocsgetlocatorrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "leadName": "string",
  "email": "string",
  "destination": "string",
  "destinationName": "string",
  "checkin": 0,
  "checkout": 0,
  "occupation": "string",
  "pax": 0,
  "origen": "string",
  "origenName": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|leadName|string|false|none|none|
|email|string|false|none|none|
|destination|string|false|none|none|
|destinationName|string|false|none|none|
|checkin|integer(int32)|false|none|none|
|checkout|integer(int32)|false|none|none|
|occupation|string|false|none|none|
|pax|integer(int32)|false|none|none|
|origen|string|false|none|none|
|origenName|string|false|none|none|

<h2 id="tocS_AvailableHotel">AvailableHotel</h2>
<!-- backwards compatibility -->
<a id="schemaavailablehotel"></a>
<a id="schema_AvailableHotel"></a>
<a id="tocSavailablehotel"></a>
<a id="tocsavailablehotel"></a>

```json
{
  "hotelId": "string",
  "hotelName": "string",
  "hotelCategoryId": "string",
  "hotelCategoryName": "string",
  "stars": 0,
  "keys": 0,
  "longitude": "string",
  "latitude": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "address": "string",
  "mainImage": "string"
}

```

An available hotel, including prices

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|hotelId|string|false|none|The hotel id|
|hotelName|string|false|none|The hotel name|
|hotelCategoryId|string|false|none|The hotel category id|
|hotelCategoryName|string|false|none|The hotel category name|
|stars|integer(int32)|false|none|The hotel number of stars|
|keys|integer(int32)|false|none|The hotel number of keys|
|longitude|string|false|none|Google longitude|
|latitude|string|false|none|Google latitude|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|address|string|false|none|The hotel address.|
|mainImage|string|false|none|Main image from hotel.|

<h2 id="tocS_GetInitialConfigRS">GetInitialConfigRS</h2>
<!-- backwards compatibility -->
<a id="schemagetinitialconfigrs"></a>
<a id="schema_GetInitialConfigRS"></a>
<a id="tocSgetinitialconfigrs"></a>
<a id="tocsgetinitialconfigrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "contactEmail": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|contactEmail|string|false|none|none|

<h2 id="tocS_BookTransferRS">BookTransferRS</h2>
<!-- backwards compatibility -->
<a id="schemabooktransferrs"></a>
<a id="schema_BookTransferRS"></a>
<a id="tocSbooktransferrs"></a>
<a id="tocsbooktransferrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

Container for the tranfer booking confirmation response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|fileId|string|false|none|none|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_GetBookingsRS">GetBookingsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetbookingsrs"></a>
<a id="schema_GetBookingsRS"></a>
<a id="tocSgetbookingsrs"></a>
<a id="tocsgetbookingsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookings": [
    {
      "bookingId": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string",
      "serviceType": "string",
      "serviceDescription": "string",
      "start": "string",
      "end": "string",
      "status": "string",
      "leadName": "string",
      "retail": 0,
      "net": 0,
      "currencyIsoCode": "string",
      "cancellationCost": [
        {
          "retail": 0,
          "net": 0,
          "gmttime": "string"
        }
      ],
      "commentsToProvider": "string",
      "privateComments": "string"
    }
  ]
}

```

Container for the getbookings response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookings|[[Booking](#schemabooking)]|false|none|The list of bookings|

<h2 id="tocS_BookTransferRQ">BookTransferRQ</h2>
<!-- backwards compatibility -->
<a id="schemabooktransferrq"></a>
<a id="schema_BookTransferRQ"></a>
<a id="tocSbooktransferrq"></a>
<a id="tocsbooktransferrq"></a>

```json
{
  "fileId": "string",
  "key": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "incomingFlightNumber": "string",
  "incomingFlightTime": 0,
  "incomingFlightOrigin": "string",
  "outgoingFlightNumber": "string",
  "outgoingFlightTime": 0,
  "outgoingFlightDestination": "string",
  "contactPhone": "string",
  "email": "string",
  "bike": 0,
  "golf": 0,
  "ski": 0,
  "wheelchair": 0,
  "bigLuggages": 0,
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "promoCode": "string",
  "mailingUnwanted": false
}

```

Container for the transfer service confirmation request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|key|string|false|none|The price id, as we got it when we asked for available transfer|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the activity provider|
|privateComments|string|false|none|Your comments for us. They will not be visible to the customer neither to the activity provider|
|incomingFlightNumber|string|false|none|Incoming flight number|
|incomingFlightTime|integer(int32)|false|none|Locale incoming flight time in YYYYMMDDHHMM format|
|incomingFlightOrigin|string|false|none|Incoming flight origin|
|outgoingFlightNumber|string|false|none|Outgoing flight number|
|outgoingFlightTime|integer(int32)|false|none|Locale outgoing flight time in YYYYMMDDHHMM format|
|outgoingFlightDestination|string|false|none|Outgoing flight origin|
|contactPhone|string|false|none|Contact telephone number|
|email|string|false|none|User Email. Used to locate your bookings|
|bike|integer(int32)|false|none|Number of bike|
|golf|integer(int32)|false|none|Number of golf baggage|
|ski|integer(int32)|false|none|Number of ski|
|wheelchair|integer(int32)|false|none|Number of wheelchair|
|bigLuggages|integer(int32)|false|none|Number of bigLuggages|
|captchaToken|string|false|none|Token for server validation captcha|
|language|string|false|none|User language|
|supplements|string|false|none|Booking extras|
|promoCode|string|false|none|Booking promo code for discount|
|mailingUnwanted|boolean|false|none|none|

<h2 id="tocS_CurrencyChange">CurrencyChange</h2>
<!-- backwards compatibility -->
<a id="schemacurrencychange"></a>
<a id="schema_CurrencyChange"></a>
<a id="tocScurrencychange"></a>
<a id="tocscurrencychange"></a>

```json
{
  "name": "string",
  "value": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|none|
|value|number(float)|false|none|none|

<h2 id="tocS_AvailableFlight">AvailableFlight</h2>
<!-- backwards compatibility -->
<a id="schemaavailableflight"></a>
<a id="schema_AvailableFlight"></a>
<a id="tocSavailableflight"></a>
<a id="tocsavailableflight"></a>

```json
{
  "economyKey": "string",
  "businessKey": "string",
  "origin": "string",
  "destination": "string",
  "company": "string",
  "companyLogo": "string",
  "departureDate": "string",
  "departureTime": "string",
  "arrivalDate": "string",
  "arrivalTime": "string",
  "duration": "string",
  "operatedBy": "string",
  "economyPrice": 0,
  "businessPrice": 0,
  "segments": [
    {
      "originId": "string",
      "originDescription": "string",
      "destinationId": "string",
      "destinationDescription": "string",
      "company": "string",
      "companyLogo": "string",
      "flightNumber": "string",
      "airplane": "string",
      "departureDate": "string",
      "departureTime": "string",
      "arrivalDate": "string",
      "arrivalTime": "string",
      "duration": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|economyKey|string|false|none|none|
|businessKey|string|false|none|none|
|origin|string|false|none|none|
|destination|string|false|none|none|
|company|string|false|none|none|
|companyLogo|string|false|none|none|
|departureDate|string|false|none|none|
|departureTime|string|false|none|none|
|arrivalDate|string|false|none|none|
|arrivalTime|string|false|none|none|
|duration|string|false|none|none|
|operatedBy|string|false|none|none|
|economyPrice|number(double)|false|none|none|
|businessPrice|number(double)|false|none|none|
|segments|[[FlightSegment](#schemaflightsegment)]|false|none|none|

<h2 id="tocS_TransfersIngestionRS">TransfersIngestionRS</h2>
<!-- backwards compatibility -->
<a id="schematransfersingestionrs"></a>
<a id="schema_TransfersIngestionRS"></a>
<a id="tocStransfersingestionrs"></a>
<a id="tocstransfersingestionrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

Response for the transfer ingestion request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_Booking">Booking</h2>
<!-- backwards compatibility -->
<a id="schemabooking"></a>
<a id="schema_Booking"></a>
<a id="tocSbooking"></a>
<a id="tocsbooking"></a>

```json
{
  "bookingId": "string",
  "created": "string",
  "createdBy": "string",
  "modified": "string",
  "serviceType": "string",
  "serviceDescription": "string",
  "start": "string",
  "end": "string",
  "status": "string",
  "leadName": "string",
  "retail": 0,
  "net": 0,
  "currencyIsoCode": "string",
  "cancellationCost": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "commentsToProvider": "string",
  "privateComments": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bookingId|string|false|none|The booking id|
|created|string|false|none|When this service was created. In ISO8651 format|
|createdBy|string|false|none|Who created this service booking|
|modified|string|false|none|Last modification date for this service in ISO8651 format|
|serviceType|string|false|none|Type of service. Intended to be HOTEL, TRANSFER, ACTIVITY, ...|
|serviceDescription|string|false|none|Description of the service|
|start|string|false|none|When this service starts using locale. In YYYYMMDD format|
|end|string|false|none|When this service ends using locale. In YYYYMMDD format|
|status|string|false|none|Status for this service. E.g. OK, ONREQUEST, CANCELLED, ...|
|leadName|string|false|none|This service lead name|
|retail|number(double)|false|none|none|
|net|number(double)|false|none|none|
|currencyIsoCode|string|false|none|none|
|cancellationCost|[[CancellationCost](#schemacancellationcost)]|false|none|none|
|commentsToProvider|string|false|none|Comments from the customer|
|privateComments|string|false|none|Comments for you. Not to be shown to the customer|

<h2 id="tocS_GetCircuitRatesRS">GetCircuitRatesRS</h2>
<!-- backwards compatibility -->
<a id="schemagetcircuitratesrs"></a>
<a id="schema_GetCircuitRatesRS"></a>
<a id="tocSgetcircuitratesrs"></a>
<a id="tocsgetcircuitratesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ]
}

```

Container for the circuit price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|variants|[[ActivityVariant](#schemaactivityvariant)]|false|none|none|

<h2 id="tocS_AdditionalServiceLink">AdditionalServiceLink</h2>
<!-- backwards compatibility -->
<a id="schemaadditionalservicelink"></a>
<a id="schema_AdditionalServiceLink"></a>
<a id="tocSadditionalservicelink"></a>
<a id="tocsadditionalservicelink"></a>

```json
{
  "type": "string",
  "uri": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|type|string|false|none|none|
|uri|string|false|none|none|

<h2 id="tocS_GetActivityPriceDetailsRS">GetActivityPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetactivitypricedetailsrs"></a>
<a id="schema_GetActivityPriceDetailsRS"></a>
<a id="tocSgetactivitypricedetailsrs"></a>
<a id="tocsgetactivitypricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "cancellationFreeDate": "string",
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string"
}

```

Container for the activity price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|key|string|false|none|none|
|supplements|[[Supplement](#schemasupplement)]|false|none|none|
|priceLines|[[PriceLine](#schemapriceline)]|false|none|[holder for a price detail line]|
|total|[Price](#schemaprice)|false|none|Holder for price|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs for this activity|
|cancellationFreeDate|string|false|none|none|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|paymentMethods|[[PaymentMethod](#schemapaymentmethod)]|false|none|none|
|terms|string|false|none|none|
|mailingUnwantedText|string|false|none|none|

<h2 id="tocS_GetTermsRS">GetTermsRS</h2>
<!-- backwards compatibility -->
<a id="schemagettermsrs"></a>
<a id="schema_GetTermsRS"></a>
<a id="tocSgettermsrs"></a>
<a id="tocsgettermsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "terms": "string",
  "unmailing": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|terms|string|false|none|none|
|unmailing|string|false|none|none|

<h2 id="tocS_GetFlightPriceDetailsRS">GetFlightPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetflightpricedetailsrs"></a>
<a id="schema_GetFlightPriceDetailsRS"></a>
<a id="tocSgetflightpricedetailsrs"></a>
<a id="tocsgetflightpricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "availableSupplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "arrivalInstructions": "string",
  "departureInstructions": "string",
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|priceBreakdown|[[PriceLine](#schemapriceline)]|false|none|Price detail, in form of lines|
|total|[Price](#schemaprice)|false|none|Holder for price|
|availableSupplements|[[Supplement](#schemasupplement)]|false|none|Available supplements|
|arrivalInstructions|string|false|none|Arrival instructions|
|departureInstructions|string|false|none|Departure instructions|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs for this activity|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|terms|string|false|none|Text for terms and conditions|
|mailingUnwantedText|string|false|none|Text for rejecting or acepting mailing|
|cancellationFreeDate|string|false|none|No cancellation costs until this date, in yyyy-MM-dd format|

<h2 id="tocS_GetHotelAvailabilityCalendarRS">GetHotelAvailabilityCalendarRS</h2>
<!-- backwards compatibility -->
<a id="schemagethotelavailabilitycalendarrs"></a>
<a id="schema_GetHotelAvailabilityCalendarRS"></a>
<a id="tocSgethotelavailabilitycalendarrs"></a>
<a id="tocsgethotelavailabilitycalendarrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}

```

Container for the getavailability response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|months|[[HotelAvailabilityCalendarMonth](#schemahotelavailabilitycalendarmonth)]|false|none|List of available hotels, including prices|

<h2 id="tocS_Country">Country</h2>
<!-- backwards compatibility -->
<a id="schemacountry"></a>
<a id="schema_Country"></a>
<a id="tocScountry"></a>
<a id="tocscountry"></a>

```json
{
  "resourceId": "string",
  "name": {
    "property1": "string",
    "property2": "string"
  },
  "urlFriendlyName": "string",
  "states": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "urlFriendlyName": "string",
      "cities": [
        {
          "resourceId": "string",
          "name": {
            "property1": "string",
            "property2": "string"
          },
          "urlFriendlyName": "string",
          "resources": [
            {
              "resourceId": "string",
              "name": {
                "property1": "string",
                "property2": "string"
              },
              "type": "string",
              "longitude": "string",
              "latitude": "string",
              "description": {
                "property1": "string",
                "property2": "string"
              }
            }
          ]
        }
      ]
    }
  ]
}

```

A country inside our portfolio. The first level in our product hierarchy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|resourceId|string|false|none|This country resource id|
|name|object|false|none|This country name|
|» **additionalProperties**|string|false|none|none|
|urlFriendlyName|string|false|none|The name in a url friendly manner|
|states|[[State](#schemastate)]|false|none|List of contained states|

<h2 id="tocS_BookCMSRQ">BookCMSRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookcmsrq"></a>
<a id="schema_BookCMSRQ"></a>
<a id="tocSbookcmsrq"></a>
<a id="tocsbookcmsrq"></a>

```json
{
  "bookings": [
    {
      "property1": {},
      "property2": {}
    }
  ],
  "captchaToken": "string",
  "language": "string",
  "mailingUnwanted": false,
  "travelAssuranceId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bookings|[object]|false|none|none|
|» **additionalProperties**|object|false|none|none|
|captchaToken|string|false|none|Token for server validation captcha|
|language|string|false|none|User language|
|mailingUnwanted|boolean|false|none|none|
|travelAssuranceId|string|false|none|none|

<h2 id="tocS_GenericVariant">GenericVariant</h2>
<!-- backwards compatibility -->
<a id="schemagenericvariant"></a>
<a id="schema_GenericVariant"></a>
<a id="tocSgenericvariant"></a>
<a id="tocsgenericvariant"></a>

```json
{
  "key": "string",
  "name": "string",
  "description": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "pricePer": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|pricePer|string|false|none|none|

<h2 id="tocS_CheckCircuitRS">CheckCircuitRS</h2>
<!-- backwards compatibility -->
<a id="schemacheckcircuitrs"></a>
<a id="schema_CheckCircuitRS"></a>
<a id="tocScheckcircuitrs"></a>
<a id="tocscheckcircuitrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|available|boolean|false|none|none|
|value|[Amount](#schemaamount)|false|none|A currency - value pair|
|key|string|false|none|none|

<h2 id="tocS_AvailableGeneric">AvailableGeneric</h2>
<!-- backwards compatibility -->
<a id="schemaavailablegeneric"></a>
<a id="schema_AvailableGeneric"></a>
<a id="tocSavailablegeneric"></a>
<a id="tocsavailablegeneric"></a>

```json
{
  "genericId": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "type": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}

```

An available Generic product

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|genericId|string|false|none|This product ID|
|name|string|false|none|The name of this product. Usually multi-language|
|description|string|false|none|The description of this product. Usually multi-language|
|image|string|false|none|The main image for this product|
|type|string|false|none|The type of product|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|labels|[[Label](#schemalabel)]|false|none|none|

<h2 id="tocS_CheckGenericRS">CheckGenericRS</h2>
<!-- backwards compatibility -->
<a id="schemacheckgenericrs"></a>
<a id="schema_CheckGenericRS"></a>
<a id="tocScheckgenericrs"></a>
<a id="tocscheckgenericrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|available|boolean|false|none|none|
|value|[Amount](#schemaamount)|false|none|A currency - value pair|
|key|string|false|none|none|

<h2 id="tocS_CancellationCost">CancellationCost</h2>
<!-- backwards compatibility -->
<a id="schemacancellationcost"></a>
<a id="schema_CancellationCost"></a>
<a id="tocScancellationcost"></a>
<a id="tocscancellationcost"></a>

```json
{
  "retail": 0,
  "net": 0,
  "gmttime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|retail|number(double)|false|none|none|
|net|number(double)|false|none|none|
|gmttime|string|false|none|none|

<h2 id="tocS_AvailableCircuit">AvailableCircuit</h2>
<!-- backwards compatibility -->
<a id="schemaavailablecircuit"></a>
<a id="schema_AvailableCircuit"></a>
<a id="tocSavailablecircuit"></a>
<a id="tocsavailablecircuit"></a>

```json
{
  "circuitId": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}

```

An available circuit

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|circuitId|string|false|none|This circuit ID|
|name|string|false|none|The name of this circuit. Usually multi-language|
|description|string|false|none|The description of this circuit. Usually multi-language|
|image|string|false|none|The main image for this circuit|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|labels|[[Label](#schemalabel)]|false|none|none|

<h2 id="tocS_BookCMSRS">BookCMSRS</h2>
<!-- backwards compatibility -->
<a id="schemabookcmsrs"></a>
<a id="schema_BookCMSRS"></a>
<a id="tocSbookcmsrs"></a>
<a id="tocsbookcmsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

Response for the shopping cart booking confirmation

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_UpdateRS">UpdateRS</h2>
<!-- backwards compatibility -->
<a id="schemaupdaters"></a>
<a id="schema_UpdateRS"></a>
<a id="tocSupdaters"></a>
<a id="tocsupdaters"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

Container for the update method response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_ConfirmServicesRQ">ConfirmServicesRQ</h2>
<!-- backwards compatibility -->
<a id="schemaconfirmservicesrq"></a>
<a id="schema_ConfirmServicesRQ"></a>
<a id="tocSconfirmservicesrq"></a>
<a id="tocsconfirmservicesrq"></a>

```json
{
  "serviceConfirmations": [
    {
      "bookingId": "string",
      "confirmed": false,
      "comments": "string"
    }
  ]
}

```

Container for the confirm services request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|serviceConfirmations|[[ServiceConfirmation](#schemaserviceconfirmation)]|false|none|List of service confirmations (or rejections)|

<h2 id="tocS_UpdateRQ">UpdateRQ</h2>
<!-- backwards compatibility -->
<a id="schemaupdaterq"></a>
<a id="schema_UpdateRQ"></a>
<a id="tocSupdaterq"></a>
<a id="tocsupdaterq"></a>

```json
{
  "operations": [
    {
      "hotelId": "string",
      "roomId": "string",
      "action": "string",
      "startDate": 0,
      "endDate": 0,
      "newValue": "string"
    }
  ]
}

```

Container for the update request parameters

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|operations|[[UpdateOperation](#schemaupdateoperation)]|false|none|List of operations you want to perform on hote inventories|

<h2 id="tocS_ConfirmServicesRS">ConfirmServicesRS</h2>
<!-- backwards compatibility -->
<a id="schemaconfirmservicesrs"></a>
<a id="schema_ConfirmServicesRS"></a>
<a id="tocSconfirmservicesrs"></a>
<a id="tocsconfirmservicesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

Container for the service confirmation response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_OptionBoardPrice">OptionBoardPrice</h2>
<!-- backwards compatibility -->
<a id="schemaoptionboardprice"></a>
<a id="schema_OptionBoardPrice"></a>
<a id="tocSoptionboardprice"></a>
<a id="tocsoptionboardprice"></a>

```json
{
  "boardBasisId": "string",
  "boardBasisName": "string",
  "retailPrice": 0,
  "netPrice": 0,
  "offer": false,
  "offerText": "string",
  "onRequest": false,
  "onRequestText": "string",
  "nonRefundable": false,
  "rateId": "string"
}

```

An availabe board basis and its price

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|boardBasisId|string|false|none|Board basis id|
|boardBasisName|string|false|none|Board basis name|
|retailPrice|number(double)|false|none|Retail price|
|netPrice|number(double)|false|none|Net price|
|offer|boolean|false|none|A flag to state that this price is an offer|
|offerText|string|false|none|The offer description, if this is an offer price|
|onRequest|boolean|false|none|A flag to state that this price is only available on request|
|onRequestText|string|false|none|Describes why this price is on request|
|nonRefundable|boolean|false|none|A flag to state that this price is not refundable. No cancellation is allowed|
|rateId|string|false|none|Rate id|

<h2 id="tocS_RoomId">RoomId</h2>
<!-- backwards compatibility -->
<a id="schemaroomid"></a>
<a id="schema_RoomId"></a>
<a id="tocSroomid"></a>
<a id="tocsroomid"></a>

```json
{
  "id": "string",
  "description": "string"
}

```

Room data to be used by the channel manager

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|This room id|
|description|string|false|none|This room description|

<h2 id="tocS_GetFilesRS">GetFilesRS</h2>
<!-- backwards compatibility -->
<a id="schemagetfilesrs"></a>
<a id="schema_GetFilesRS"></a>
<a id="tocSgetfilesrs"></a>
<a id="tocsgetfilesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "files": [
    {
      "fileId": "string",
      "bookings": [
        {
          "bookingId": "string",
          "created": "string",
          "createdBy": "string",
          "modified": "string",
          "serviceType": "string",
          "serviceDescription": "string",
          "start": "string",
          "end": "string",
          "status": "string",
          "leadName": "string",
          "retail": 0,
          "net": 0,
          "currencyIsoCode": "string",
          "cancellationCost": [
            {
              "retail": 0,
              "net": 0,
              "gmttime": "string"
            }
          ],
          "commentsToProvider": "string",
          "privateComments": "string"
        }
      ],
      "totalPrice": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "leadName": "string",
      "email": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string"
    }
  ]
}

```

Container for the get files response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|files|[[File](#schemafile)]|false|none|The list of files|

<h2 id="tocS_CheckTicketRS">CheckTicketRS</h2>
<!-- backwards compatibility -->
<a id="schemacheckticketrs"></a>
<a id="schema_CheckTicketRS"></a>
<a id="tocScheckticketrs"></a>
<a id="tocscheckticketrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "ticket": {
    "id": "string",
    "qrcode": "string",
    "leadname": "string",
    "pax": 0,
    "checkedDate": 0,
    "checkedTime": 0,
    "checked": false,
    "comments": "string"
  },
  "validationMessage": "string",
  "valid": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|ticket|[TicketCheckItem](#schematicketcheckitem)|false|none|none|
|validationMessage|string|false|none|none|
|valid|boolean|false|none|none|

<h2 id="tocS_ActivityVariant">ActivityVariant</h2>
<!-- backwards compatibility -->
<a id="schemaactivityvariant"></a>
<a id="schema_ActivityVariant"></a>
<a id="tocSactivityvariant"></a>
<a id="tocsactivityvariant"></a>

```json
{
  "key": "string",
  "name": "string",
  "description": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "pricePer": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|pricePer|string|false|none|none|

<h2 id="tocS_GetDestinationRS">GetDestinationRS</h2>
<!-- backwards compatibility -->
<a id="schemagetdestinationrs"></a>
<a id="schema_GetDestinationRS"></a>
<a id="tocSgetdestinationrs"></a>
<a id="tocsgetdestinationrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "destination": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|destination|[[Resource](#schemaresource)]|false|none|List of destination.|

<h2 id="tocS_FlightSegment">FlightSegment</h2>
<!-- backwards compatibility -->
<a id="schemaflightsegment"></a>
<a id="schema_FlightSegment"></a>
<a id="tocSflightsegment"></a>
<a id="tocsflightsegment"></a>

```json
{
  "originId": "string",
  "originDescription": "string",
  "destinationId": "string",
  "destinationDescription": "string",
  "company": "string",
  "companyLogo": "string",
  "flightNumber": "string",
  "airplane": "string",
  "departureDate": "string",
  "departureTime": "string",
  "arrivalDate": "string",
  "arrivalTime": "string",
  "duration": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|originId|string|false|none|none|
|originDescription|string|false|none|none|
|destinationId|string|false|none|none|
|destinationDescription|string|false|none|none|
|company|string|false|none|none|
|companyLogo|string|false|none|none|
|flightNumber|string|false|none|none|
|airplane|string|false|none|none|
|departureDate|string|false|none|none|
|departureTime|string|false|none|none|
|arrivalDate|string|false|none|none|
|arrivalTime|string|false|none|none|
|duration|string|false|none|none|

<h2 id="tocS_GetLoginRS">GetLoginRS</h2>
<!-- backwards compatibility -->
<a id="schemagetloginrs"></a>
<a id="schema_GetLoginRS"></a>
<a id="tocSgetloginrs"></a>
<a id="tocsgetloginrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "authUser": "string",
  "message": "string",
  "logged": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|authUser|string|false|none|none|
|message|string|false|none|none|
|logged|boolean|false|none|none|

<h2 id="tocS_GetLoginRQ">GetLoginRQ</h2>
<!-- backwards compatibility -->
<a id="schemagetloginrq"></a>
<a id="schema_GetLoginRQ"></a>
<a id="tocSgetloginrq"></a>
<a id="tocsgetloginrq"></a>

```json
{
  "user": "string",
  "password": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user|string|false|none|none|
|password|string|false|none|none|

<h2 id="tocS_TransferRQ">TransferRQ</h2>
<!-- backwards compatibility -->
<a id="schematransferrq"></a>
<a id="schema_TransferRQ"></a>
<a id="tocStransferrq"></a>
<a id="tocstransferrq"></a>

```json
{
  "agencyId": "string",
  "agencyReference": "string",
  "currency": "string",
  "value": 0,
  "serviceType": "string",
  "vehicle": "string",
  "passengerName": "string",
  "phone": "string",
  "email": "string",
  "adults": 0,
  "children": 0,
  "babies": 0,
  "extras": 0,
  "comments": "string",
  "arrivalStatus": "string",
  "arrivalAirport": "string",
  "arrivalZone": "string",
  "arrivalAddress": "string",
  "arrivalFlightDate": "string",
  "arrivalFlightTime": "string",
  "arrivalFlightNumber": "string",
  "arrivalFlightCompany": "string",
  "arrivalOriginAirport": "string",
  "arrivalComments": "string",
  "arrivalPickupDate": "string",
  "arrivalPickupTime": "string",
  "departureStatus": "string",
  "departureAirport": "string",
  "departureZone": "string",
  "departureAddress": "string",
  "departureFlightDate": "string",
  "departureFlightTime": "string",
  "departureFlightNumber": "string",
  "departureFlightCompany": "string",
  "departureDestinationAirport": "string",
  "departureComments": "string",
  "departurePickupDate": "string",
  "departurePickupTime": "string"
}

```

Transfer request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|agencyId|string|false|none|none|
|agencyReference|string|false|none|none|
|currency|string|false|none|none|
|value|number(double)|false|none|none|
|serviceType|string|false|none|none|
|vehicle|string|false|none|none|
|passengerName|string|false|none|none|
|phone|string|false|none|none|
|email|string|false|none|none|
|adults|integer(int32)|false|none|none|
|children|integer(int32)|false|none|none|
|babies|integer(int32)|false|none|none|
|extras|integer(int32)|false|none|none|
|comments|string|false|none|none|
|arrivalStatus|string|false|none|none|
|arrivalAirport|string|false|none|none|
|arrivalZone|string|false|none|none|
|arrivalAddress|string|false|none|none|
|arrivalFlightDate|string|false|none|none|
|arrivalFlightTime|string|false|none|none|
|arrivalFlightNumber|string|false|none|none|
|arrivalFlightCompany|string|false|none|none|
|arrivalOriginAirport|string|false|none|none|
|arrivalComments|string|false|none|none|
|arrivalPickupDate|string|false|none|none|
|arrivalPickupTime|string|false|none|none|
|departureStatus|string|false|none|none|
|departureAirport|string|false|none|none|
|departureZone|string|false|none|none|
|departureAddress|string|false|none|none|
|departureFlightDate|string|false|none|none|
|departureFlightTime|string|false|none|none|
|departureFlightNumber|string|false|none|none|
|departureFlightCompany|string|false|none|none|
|departureDestinationAirport|string|false|none|none|
|departureComments|string|false|none|none|
|departurePickupDate|string|false|none|none|
|departurePickupTime|string|false|none|none|

<h2 id="tocS_GetUpdatedTicketsRQ">GetUpdatedTicketsRQ</h2>
<!-- backwards compatibility -->
<a id="schemagetupdatedticketsrq"></a>
<a id="schema_GetUpdatedTicketsRQ"></a>
<a id="tocSgetupdatedticketsrq"></a>
<a id="tocsgetupdatedticketsrq"></a>

```json
{
  "userId": "string",
  "tickets": [
    {
      "id": "string",
      "qrcode": "string",
      "leadname": "string",
      "pax": 0,
      "checkedDate": 0,
      "checkedTime": 0,
      "checked": false,
      "comments": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|userId|string|false|none|none|
|tickets|[[TicketCheckItem](#schematicketcheckitem)]|false|none|none|

<h2 id="tocS_GetAvailableCircuitsRS">GetAvailableCircuitsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailablecircuitsrs"></a>
<a id="schema_GetAvailableCircuitsRS"></a>
<a id="tocSgetavailablecircuitsrs"></a>
<a id="tocsgetavailablecircuitsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableCircuits": [
    {
      "circuitId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}

```

Response with the list of available circuit

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|labels|[[Label](#schemalabel)]|false|none|none|
|minPrice|number(double)|false|none|none|
|maxPrice|number(double)|false|none|none|
|availableCircuits|[[AvailableCircuit](#schemaavailablecircuit)]|false|none|List of the available circuits for that resort and dates|

<h2 id="tocS_HotelBooking">HotelBooking</h2>
<!-- backwards compatibility -->
<a id="schemahotelbooking"></a>
<a id="schema_HotelBooking"></a>
<a id="tocShotelbooking"></a>
<a id="tocshotelbooking"></a>

```json
{
  "bookingId": "string",
  "created": "string",
  "createdBy": "string",
  "modified": "string",
  "serviceType": "string",
  "serviceDescription": "string",
  "start": "string",
  "end": "string",
  "status": "string",
  "leadName": "string",
  "retailValue": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "netValue": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "commentsToProvider": "string",
  "privateComments": "string",
  "stays": [
    {
      "start": 0,
      "end": 0,
      "roomId": "string",
      "roomName": "string",
      "boardBasisId": "string",
      "boardBasisName": "string",
      "numberOfRooms": 0,
      "paxPerRoom": 0,
      "ages": [
        0
      ]
    }
  ]
}

```

A booking service

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bookingId|string|false|none|The booking id|
|created|string|false|none|When this service was created. In ISO8651 format|
|createdBy|string|false|none|Who created this service booking|
|modified|string|false|none|Last modification date for this service in ISO8651 format|
|serviceType|string|false|none|Type of service. Intended to be HOTEL, TRANSFER, ACTIVITY, ...|
|serviceDescription|string|false|none|Description of the service|
|start|string|false|none|When this service starts using locale. In YYYYMMDD format|
|end|string|false|none|When this service ends using locale. In YYYYMMDD format|
|status|string|false|none|Status for this service. E.g. OK, ONREQUEST, CANCELLED, ...|
|leadName|string|false|none|This service lead name|
|retailValue|[Amount](#schemaamount)|false|none|A currency - value pair|
|netValue|[Amount](#schemaamount)|false|none|A currency - value pair|
|commentsToProvider|string|false|none|Comments from the customer|
|privateComments|string|false|none|Comments for you. Not to be shown to the customer|
|stays|[[HotelStay](#schemahotelstay)]|false|none|List of stays (rooms, occupation and boards)|

<h2 id="tocS_Stay">Stay</h2>
<!-- backwards compatibility -->
<a id="schemastay"></a>
<a id="schema_Stay"></a>
<a id="tocSstay"></a>
<a id="tocsstay"></a>

```json
{
  "occupancy": "string",
  "roomId": "string",
  "boardId": "string",
  "rateId": "string",
  "supplements": "string",
  "pax": [
    {
      "firstName": "string",
      "surname": "string",
      "age": 0,
      "birthDate": 0,
      "type": "string",
      "documentType": "string",
      "documentId": "string",
      "groupId": "string"
    }
  ]
}

```

One instance for each occupancy (number of rooms - pax - ages)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|occupancy|string|false|none|Occupancy you need in <nr of rooms>x<pax>[-<age>]* format. E.g.: 2x4-10-6-2 2 rooms occupied by 4 pax where 3 of them are 10, 6 and 2 years old|
|roomId|string|false|none|Desired room id|
|boardId|string|false|none|Desired board id|
|rateId|string|false|none|Desired rate id|
|supplements|string|false|none|Semicolon separated list of desired supplements in format id#qty;id#qty;id#qty|
|pax|[[PaxDetails](#schemapaxdetails)]|false|none|Passengers info. Applies only when confirming|

<h2 id="tocS_Cart">Cart</h2>
<!-- backwards compatibility -->
<a id="schemacart"></a>
<a id="schema_Cart"></a>
<a id="tocScart"></a>
<a id="tocscart"></a>

```json
{
  "precio": "string",
  "img": "string",
  "qty": "string",
  "id": "string",
  "nombre": "string",
  "nombreHtml": "string",
  "qrCode": "string",
  "groupReference": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|precio|string|false|none|none|
|img|string|false|none|none|
|qty|string|false|none|none|
|id|string|false|none|none|
|nombre|string|false|none|none|
|nombreHtml|string|false|none|none|
|qrCode|string|false|none|none|
|groupReference|string|false|none|none|

<h2 id="tocS_GetAvailableActivitiesRS">GetAvailableActivitiesRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailableactivitiesrs"></a>
<a id="schema_GetAvailableActivitiesRS"></a>
<a id="tocSgetavailableactivitiesrs"></a>
<a id="tocsgetavailableactivitiesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableActivities": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}

```

Response with the list of available activities

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|labels|[[Label](#schemalabel)]|false|none|none|
|minPrice|number(double)|false|none|none|
|maxPrice|number(double)|false|none|none|
|availableActivities|[[AvailableActivity](#schemaavailableactivity)]|false|none|List of the available activities for that resort and dates|

<h2 id="tocS_AvailableActivity">AvailableActivity</h2>
<!-- backwards compatibility -->
<a id="schemaavailableactivity"></a>
<a id="schema_AvailableActivity"></a>
<a id="tocSavailableactivity"></a>
<a id="tocsavailableactivity"></a>

```json
{
  "activityId": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "bestDeal": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}

```

An available activity

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|activityId|string|false|none|This activity ID|
|name|string|false|none|The name of this activity. Usually multi-language|
|description|string|false|none|The description of this activity. Usually multi-language|
|image|string|false|none|The main image for this activity|
|bestDeal|[Price](#schemaprice)|false|none|Holder for price|
|labels|[[Label](#schemalabel)]|false|none|none|

<h2 id="tocS_ServiceConfirmation">ServiceConfirmation</h2>
<!-- backwards compatibility -->
<a id="schemaserviceconfirmation"></a>
<a id="schema_ServiceConfirmation"></a>
<a id="tocSserviceconfirmation"></a>
<a id="tocsserviceconfirmation"></a>

```json
{
  "bookingId": "string",
  "confirmed": false,
  "comments": "string"
}

```

Service confirmation data

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bookingId|string|false|none|Service booking id, as provided by the getroominglist method|
|confirmed|boolean|false|none|True if this service is OK. False if this service is not accepted|
|comments|string|false|none|Comments you want to supply. E.g. the reason to reject the service request|

<h2 id="tocS_Amount">Amount</h2>
<!-- backwards compatibility -->
<a id="schemaamount"></a>
<a id="schema_Amount"></a>
<a id="tocSamount"></a>
<a id="tocsamount"></a>

```json
{
  "currencyIsoCode": "string",
  "value": 0
}

```

A currency - value pair

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|currencyIsoCode|string|false|none|The currency ISO code|
|value|number(double)|false|none|The amount value, expressed in this currency|

<h2 id="tocS_CancelFileRS">CancelFileRS</h2>
<!-- backwards compatibility -->
<a id="schemacancelfilers"></a>
<a id="schema_CancelFileRS"></a>
<a id="tocScancelfilers"></a>
<a id="tocscancelfilers"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_GetGenericPriceDetailsRS">GetGenericPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetgenericpricedetailsrs"></a>
<a id="schema_GetGenericPriceDetailsRS"></a>
<a id="tocSgetgenericpricedetailsrs"></a>
<a id="tocsgetgenericpricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "couponMsg": "string",
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|key|string|false|none|none|
|supplements|[[Supplement](#schemasupplement)]|false|none|none|
|priceLines|[[PriceLine](#schemapriceline)]|false|none|[holder for a price detail line]|
|total|[Price](#schemaprice)|false|none|Holder for price|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs for this activity|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|couponMsg|string|false|none|Response message from discount coupon applicated|
|paymentMethods|[[PaymentMethod](#schemapaymentmethod)]|false|none|none|
|terms|string|false|none|none|
|mailingUnwantedText|string|false|none|none|
|cancellationFreeDate|string|false|none|none|

<h2 id="tocS_CartCompletionRQ">CartCompletionRQ</h2>
<!-- backwards compatibility -->
<a id="schemacartcompletionrq"></a>
<a id="schema_CartCompletionRQ"></a>
<a id="tocScartcompletionrq"></a>
<a id="tocscartcompletionrq"></a>

```json
{
  "bookings": [
    {
      "property1": {},
      "property2": {}
    }
  ],
  "captchaToken": "string",
  "language": "string",
  "mailingUnwanted": false,
  "travelAssuranceId": "string",
  "geoLoc": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bookings|[object]|false|none|none|
|» **additionalProperties**|object|false|none|none|
|captchaToken|string|false|none|Token for server validation captcha|
|language|string|false|none|User language|
|mailingUnwanted|boolean|false|none|none|
|travelAssuranceId|string|false|none|none|
|geoLoc|string|false|none|none|

<h2 id="tocS_Personaldata">Personaldata</h2>
<!-- backwards compatibility -->
<a id="schemapersonaldata"></a>
<a id="schema_Personaldata"></a>
<a id="tocSpersonaldata"></a>
<a id="tocspersonaldata"></a>

```json
{
  "hotel": "string",
  "telefono": "string",
  "titular": "string",
  "email": "string",
  "habitacion": "string",
  "comments": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|hotel|string|false|none|none|
|telefono|string|false|none|none|
|titular|string|false|none|none|
|email|string|false|none|none|
|habitacion|string|false|none|none|
|comments|string|false|none|none|

<h2 id="tocS_ActivityAvailabilityCalendarWeek">ActivityAvailabilityCalendarWeek</h2>
<!-- backwards compatibility -->
<a id="schemaactivityavailabilitycalendarweek"></a>
<a id="schema_ActivityAvailabilityCalendarWeek"></a>
<a id="tocSactivityavailabilitycalendarweek"></a>
<a id="tocsactivityavailabilitycalendarweek"></a>

```json
{
  "days": [
    {
      "id": 0,
      "posInWeek": 0,
      "day": 0,
      "date": "string",
      "styleName": "string",
      "blank": false
    }
  ]
}

```

A calendar week

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|days|[[ActivityAvailabilityCalendarDay](#schemaactivityavailabilitycalendarday)]|false|none|[A calendar day]|

<h2 id="tocS_PlainActivityItem">PlainActivityItem</h2>
<!-- backwards compatibility -->
<a id="schemaplainactivityitem"></a>
<a id="schema_PlainActivityItem"></a>
<a id="tocSplainactivityitem"></a>
<a id="tocsplainactivityitem"></a>

```json
{
  "id": "string",
  "description": "string",
  "htmlDescription": "string",
  "activityId": "string",
  "retailPrice": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "groupReference": "string",
  "groupDescription": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|description|string|false|none|none|
|htmlDescription|string|false|none|none|
|activityId|string|false|none|none|
|retailPrice|[Amount](#schemaamount)|false|none|A currency - value pair|
|groupReference|string|false|none|none|
|groupDescription|string|false|none|none|

<h2 id="tocS_CartCompletionRS">CartCompletionRS</h2>
<!-- backwards compatibility -->
<a id="schemacartcompletionrs"></a>
<a id="schema_CartCompletionRS"></a>
<a id="tocScartcompletionrs"></a>
<a id="tocscartcompletionrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "additionalServicesLinks": [
    {
      "type": "string",
      "uri": "string"
    }
  ],
  "travelInsurance": {
    "id": "string",
    "name": "string",
    "description": "string",
    "icon": "string",
    "value": 0,
    "currency": "string",
    "totalIfIncluded": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|additionalServicesLinks|[[AdditionalServiceLink](#schemaadditionalservicelink)]|false|none|none|
|travelInsurance|[TravelInsuranceData](#schematravelinsurancedata)|false|none|none|

<h2 id="tocS_HotelRQ">HotelRQ</h2>
<!-- backwards compatibility -->
<a id="schemahotelrq"></a>
<a id="schema_HotelRQ"></a>
<a id="tocShotelrq"></a>
<a id="tocshotelrq"></a>

```json
{
  "agencyId": "string",
  "agencyReference": "string",
  "additional": false,
  "currency": "string",
  "value": 0,
  "passengerName": "string",
  "phone": "string",
  "email": "string",
  "adults": 0,
  "children": 0,
  "babies": 0,
  "extras": 0,
  "ages": "string",
  "comments": "string",
  "hotel": "string",
  "hotelCountry": "string",
  "hotelDestination": "string",
  "hotelZone": "string",
  "hotelName": "string",
  "hotelAddress": "string",
  "numberOfRooms": 0,
  "room": "string",
  "board": "string",
  "serviceType": "string",
  "vehicle": "string",
  "arrivalStatus": "string",
  "arrivalAirport": "string",
  "arrivalFlightDate": "string",
  "arrivalFlightTime": "string",
  "arrivalFlightNumber": "string",
  "arrivalFlightCompany": "string",
  "arrivalOriginAirport": "string",
  "arrivalComments": "string",
  "arrivalPickupDate": "string",
  "arrivalPickupTime": "string",
  "departureStatus": "string",
  "departureAirport": "string",
  "departureFlightDate": "string",
  "departureFlightTime": "string",
  "departureFlightNumber": "string",
  "departureFlightCompany": "string",
  "departureDestinationAirport": "string",
  "departureComments": "string",
  "departurePickupDate": "string",
  "departurePickupTime": "string"
}

```

Hotel request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|agencyId|string|false|none|none|
|agencyReference|string|false|none|none|
|additional|boolean|false|none|none|
|currency|string|false|none|none|
|value|number(double)|false|none|none|
|passengerName|string|false|none|none|
|phone|string|false|none|none|
|email|string|false|none|none|
|adults|integer(int32)|false|none|none|
|children|integer(int32)|false|none|none|
|babies|integer(int32)|false|none|none|
|extras|integer(int32)|false|none|none|
|ages|string|false|none|none|
|comments|string|false|none|none|
|hotel|string|false|none|none|
|hotelCountry|string|false|none|none|
|hotelDestination|string|false|none|none|
|hotelZone|string|false|none|none|
|hotelName|string|false|none|none|
|hotelAddress|string|false|none|none|
|numberOfRooms|integer(int32)|false|none|none|
|room|string|false|none|none|
|board|string|false|none|none|
|serviceType|string|false|none|none|
|vehicle|string|false|none|none|
|arrivalStatus|string|false|none|none|
|arrivalAirport|string|false|none|none|
|arrivalFlightDate|string|false|none|none|
|arrivalFlightTime|string|false|none|none|
|arrivalFlightNumber|string|false|none|none|
|arrivalFlightCompany|string|false|none|none|
|arrivalOriginAirport|string|false|none|none|
|arrivalComments|string|false|none|none|
|arrivalPickupDate|string|false|none|none|
|arrivalPickupTime|string|false|none|none|
|departureStatus|string|false|none|none|
|departureAirport|string|false|none|none|
|departureFlightDate|string|false|none|none|
|departureFlightTime|string|false|none|none|
|departureFlightNumber|string|false|none|none|
|departureFlightCompany|string|false|none|none|
|departureDestinationAirport|string|false|none|none|
|departureComments|string|false|none|none|
|departurePickupDate|string|false|none|none|
|departurePickupTime|string|false|none|none|

<h2 id="tocS_PaymentLine">PaymentLine</h2>
<!-- backwards compatibility -->
<a id="schemapaymentline"></a>
<a id="schema_PaymentLine"></a>
<a id="tocSpaymentline"></a>
<a id="tocspaymentline"></a>

```json
{
  "paymentMethod": "string",
  "date": "string",
  "amount": {
    "currencyIsoCode": "string",
    "value": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|paymentMethod|string|false|none|none|
|date|string|false|none|none|
|amount|[Amount](#schemaamount)|false|none|A currency - value pair|

<h2 id="tocS_ActivityAvailabilityCalendarMonth">ActivityAvailabilityCalendarMonth</h2>
<!-- backwards compatibility -->
<a id="schemaactivityavailabilitycalendarmonth"></a>
<a id="schema_ActivityAvailabilityCalendarMonth"></a>
<a id="tocSactivityavailabilitycalendarmonth"></a>
<a id="tocsactivityavailabilitycalendarmonth"></a>

```json
{
  "title": "string",
  "year": 0,
  "month": 0,
  "weeks": [
    {
      "days": [
        {
          "id": 0,
          "posInWeek": 0,
          "day": 0,
          "date": "string",
          "styleName": "string",
          "blank": false
        }
      ]
    }
  ]
}

```

A calendar month

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|title|string|false|none|none|
|year|integer(int32)|false|none|none|
|month|integer(int32)|false|none|none|
|weeks|[[ActivityAvailabilityCalendarWeek](#schemaactivityavailabilitycalendarweek)]|false|none|[A calendar week]|

<h2 id="tocS_GetTicketCheckListRS">GetTicketCheckListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetticketchecklistrs"></a>
<a id="schema_GetTicketCheckListRS"></a>
<a id="tocSgetticketchecklistrs"></a>
<a id="tocsgetticketchecklistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "ticket": {
    "ticket": [
      {
        "id": "string",
        "qrcode": "string",
        "leadname": "string",
        "pax": 0,
        "checkedDate": 0,
        "checkedTime": 0,
        "checked": false,
        "comments": "string"
      }
    ],
    "totalTickets": 0,
    "checkedTickets": 0,
    "remainingTickets": 0,
    "totalPax": 0,
    "checkedPax": 0,
    "remainingPax": 0,
    "eventId": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|ticket|[TicketListItem](#schematicketlistitem)|false|none|none|

<h2 id="tocS_BookGenericRS">BookGenericRS</h2>
<!-- backwards compatibility -->
<a id="schemabookgenericrs"></a>
<a id="schema_BookGenericRS"></a>
<a id="tocSbookgenericrs"></a>
<a id="tocsbookgenericrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|fileId|string|false|none|none|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_BookGenericRQ">BookGenericRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookgenericrq"></a>
<a id="schema_BookGenericRQ"></a>
<a id="tocSbookgenericrq"></a>
<a id="tocsbookgenericrq"></a>

```json
{
  "fileId": "string",
  "key": "string",
  "supplementIds": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "coupon": "string",
  "mailingUnwanted": false
}

```

Parameters needed to confirm an generic product booking

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|key|string|false|none|none|
|supplementIds|string|false|none|none|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the activity provider|
|phoneNumber|string|false|none|Your phone number to contact with you|
|email|string|false|none|User Email. Used to locate your bookings|
|captchaToken|string|false|none|Token for server validation captcha|
|language|string|false|none|User language|
|supplements|string|false|none|Booking extras|
|coupon|string|false|none|Booking coupon discount|
|mailingUnwanted|boolean|false|none|none|

<h2 id="tocS_ActivityCheckItem">ActivityCheckItem</h2>
<!-- backwards compatibility -->
<a id="schemaactivitycheckitem"></a>
<a id="schema_ActivityCheckItem"></a>
<a id="tocSactivitycheckitem"></a>
<a id="tocsactivitycheckitem"></a>

```json
{
  "activityId": "string",
  "name": "string",
  "description": "string",
  "image": "string",
  "date": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|activityId|string|false|none|This activity ID|
|name|string|false|none|The name of this activity.|
|description|string|false|none|The description of this activity.|
|image|string|false|none|The main image for this activity|
|date|integer(int32)|false|none|Date for this activity|

<h2 id="tocS_TravelInsuranceData">TravelInsuranceData</h2>
<!-- backwards compatibility -->
<a id="schematravelinsurancedata"></a>
<a id="schema_TravelInsuranceData"></a>
<a id="tocStravelinsurancedata"></a>
<a id="tocstravelinsurancedata"></a>

```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "icon": "string",
  "value": 0,
  "currency": "string",
  "totalIfIncluded": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|description|string|false|none|none|
|icon|string|false|none|none|
|value|number(double)|false|none|none|
|currency|string|false|none|none|
|totalIfIncluded|number(double)|false|none|none|

<h2 id="tocS_FlightBestPrice">FlightBestPrice</h2>
<!-- backwards compatibility -->
<a id="schemaflightbestprice"></a>
<a id="schema_FlightBestPrice"></a>
<a id="tocSflightbestprice"></a>
<a id="tocsflightbestprice"></a>

```json
{
  "formattedDate": "string",
  "date": "string",
  "price": 0,
  "current": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|formattedDate|string|false|none|none|
|date|string|false|none|none|
|price|number(double)|false|none|none|
|current|boolean|false|none|none|

<h2 id="tocS_AvailableTransfer">AvailableTransfer</h2>
<!-- backwards compatibility -->
<a id="schemaavailabletransfer"></a>
<a id="schema_AvailableTransfer"></a>
<a id="tocSavailabletransfer"></a>
<a id="tocsavailabletransfer"></a>

```json
{
  "key": "string",
  "type": "string",
  "vehicle": "string",
  "description": "string",
  "image": "string",
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "offer": false,
  "offerText": "string",
  "onRequest": false,
  "onRequestText": "string",
  "nonRefundable": false
}

```

An available transfer

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|Identifier for this transfer price. You will use it in next steps|
|type|string|false|none|Type of transfer. E.G. SHUTTLE, PRIVATE|
|vehicle|string|false|none|Vehicle|
|description|string|false|none|Description of the service|
|image|string|false|none|Main image from transfer.|
|total|[Price](#schemaprice)|false|none|Holder for price|
|offer|boolean|false|none|A flag to state that this price is an offer|
|offerText|string|false|none|The offer description, if this is an offer price|
|onRequest|boolean|false|none|A flag to state that this price is only available on request|
|onRequestText|string|false|none|Describes why this price is on request|
|nonRefundable|boolean|false|none|A flag to state that this price is not refundable. No cancellation is allowed|

<h2 id="tocS_MealPlan">MealPlan</h2>
<!-- backwards compatibility -->
<a id="schemamealplan"></a>
<a id="schema_MealPlan"></a>
<a id="tocSmealplan"></a>
<a id="tocsmealplan"></a>

```json
{
  "id": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|The meal plan id|
|name|string|false|none|The meal plan name|

<h2 id="tocS_PricedStay">PricedStay</h2>
<!-- backwards compatibility -->
<a id="schemapricedstay"></a>
<a id="schema_PricedStay"></a>
<a id="tocSpricedstay"></a>
<a id="tocspricedstay"></a>

```json
{
  "occupancy": "string",
  "roomId": "string",
  "roomName": "string",
  "boardId": "string",
  "boardName": "string",
  "rateId": "string",
  "supplements": "string",
  "pax": [
    {
      "firstName": "string",
      "surname": "string",
      "age": 0,
      "birthDate": 0,
      "type": "string",
      "documentType": "string",
      "documentId": "string",
      "groupId": "string"
    }
  ],
  "retailPrice": 0,
  "netPrice": 0,
  "offer": false,
  "offerText": "string",
  "onRequest": false,
  "onRequestText": "string",
  "nonRefundable": false,
  "availableSupplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ]
}

```

One instance for each occupancy (number of rooms - pax - ages)

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|occupancy|string|false|none|Occupancy you need in <nr of rooms>x<pax>[-<age>]* format. E.g.: 2x4-10-6-2 2 rooms occupied by 4 pax where 3 of them are 10, 6 and 2 years old|
|roomId|string|false|none|Desired room id|
|roomName|string|false|none|Desired room name|
|boardId|string|false|none|Desired board id|
|boardName|string|false|none|Desired board name|
|rateId|string|false|none|Desired rate id|
|supplements|string|false|none|Semicolon separated list of desired supplements in format id#qty;id#qty;id#qty|
|pax|[[PaxDetails](#schemapaxdetails)]|false|none|Passengers info. Applies only when confirming|
|retailPrice|number(double)|false|none|Retail price|
|netPrice|number(double)|false|none|Net price|
|offer|boolean|false|none|A flag to state that this price is an offer|
|offerText|string|false|none|The offer description, if this is an offer price|
|onRequest|boolean|false|none|A flag to state that this price is only available on request|
|onRequestText|string|false|none|Describes why this price is on request|
|nonRefundable|boolean|false|none|A flag to state that this price is not refundable. No cancellation is allowed|
|availableSupplements|[[Supplement](#schemasupplement)]|false|none|List of available optional supplements|

<h2 id="tocS_Label">Label</h2>
<!-- backwards compatibility -->
<a id="schemalabel"></a>
<a id="schema_Label"></a>
<a id="tocSlabel"></a>
<a id="tocslabel"></a>

```json
{
  "id": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocS_GetAvailableGenericsRS">GetAvailableGenericsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailablegenericsrs"></a>
<a id="schema_GetAvailableGenericsRS"></a>
<a id="tocSgetavailablegenericsrs"></a>
<a id="tocsgetavailablegenericsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableGenerics": [
    {
      "genericId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "type": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "labels": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}

```

Response with the list of available products

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|labels|[[Label](#schemalabel)]|false|none|none|
|minPrice|number(double)|false|none|none|
|maxPrice|number(double)|false|none|none|
|availableGenerics|[[AvailableGeneric](#schemaavailablegeneric)]|false|none|List of the available products|

<h2 id="tocS_HotelAvailabilityCalendarMonth">HotelAvailabilityCalendarMonth</h2>
<!-- backwards compatibility -->
<a id="schemahotelavailabilitycalendarmonth"></a>
<a id="schema_HotelAvailabilityCalendarMonth"></a>
<a id="tocShotelavailabilitycalendarmonth"></a>
<a id="tocshotelavailabilitycalendarmonth"></a>

```json
{
  "title": "string",
  "year": 0,
  "month": 0,
  "weeks": [
    {
      "days": [
        {
          "id": 0,
          "posInWeek": 0,
          "day": 0,
          "date": "string",
          "styleName": "string",
          "blank": false
        }
      ]
    }
  ]
}

```

A calendar month

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|title|string|false|none|none|
|year|integer(int32)|false|none|none|
|month|integer(int32)|false|none|none|
|weeks|[[HotelAvailabilityCalendarWeek](#schemahotelavailabilitycalendarweek)]|false|none|[A calendar week]|

<h2 id="tocS_GetCircuitPriceDetailsRS">GetCircuitPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetcircuitpricedetailsrs"></a>
<a id="schema_GetCircuitPriceDetailsRS"></a>
<a id="tocSgetcircuitpricedetailsrs"></a>
<a id="tocsgetcircuitpricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "key": "string",
  "supplements": [
    {
      "id": "string",
      "description": "string",
      "price": 0
    }
  ],
  "priceLines": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "terms": "string",
  "mailingUnwantedText": "string",
  "cancellationFreeDate": "string"
}

```

Container for the circuit price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|key|string|false|none|none|
|supplements|[[Supplement](#schemasupplement)]|false|none|none|
|priceLines|[[PriceLine](#schemapriceline)]|false|none|[holder for a price detail line]|
|total|[Price](#schemaprice)|false|none|Holder for price|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs for this circuit|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|paymentMethods|[[PaymentMethod](#schemapaymentmethod)]|false|none|none|
|terms|string|false|none|none|
|mailingUnwantedText|string|false|none|none|
|cancellationFreeDate|string|false|none|none|

<h2 id="tocS_GetGenericRatesRS">GetGenericRatesRS</h2>
<!-- backwards compatibility -->
<a id="schemagetgenericratesrs"></a>
<a id="schema_GetGenericRatesRS"></a>
<a id="tocSgetgenericratesrs"></a>
<a id="tocsgetgenericratesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "dateDependant": false,
  "datesRangeDependant": false,
  "unitsDependant": false,
  "adultsDependant": false,
  "childrenDependant": false,
  "variantDependant": false,
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ]
}

```

Container for the activity price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|dateDependant|boolean|false|none|none|
|datesRangeDependant|boolean|false|none|none|
|unitsDependant|boolean|false|none|none|
|adultsDependant|boolean|false|none|none|
|childrenDependant|boolean|false|none|none|
|variantDependant|boolean|false|none|none|
|variants|[[GenericVariant](#schemagenericvariant)]|false|none|none|

<h2 id="tocS_GetOfflineCheckListRS">GetOfflineCheckListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetofflinechecklistrs"></a>
<a id="schema_GetOfflineCheckListRS"></a>
<a id="tocSgetofflinechecklistrs"></a>
<a id="tocsgetofflinechecklistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ],
  "event": [
    {
      "id": "string",
      "name": "string",
      "activityId": "string"
    }
  ],
  "ticketList": [
    {
      "ticket": [
        {
          "id": "string",
          "qrcode": "string",
          "leadname": "string",
          "pax": 0,
          "checkedDate": 0,
          "checkedTime": 0,
          "checked": false,
          "comments": "string"
        }
      ],
      "totalTickets": 0,
      "checkedTickets": 0,
      "remainingTickets": 0,
      "totalPax": 0,
      "checkedPax": 0,
      "remainingPax": 0,
      "eventId": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|activity|[[ActivityCheckItem](#schemaactivitycheckitem)]|false|none|List of available excursions, to check|
|event|[[EventCheckItem](#schemaeventcheckitem)]|false|none|List of available events in an excursions, to check|
|ticketList|[[TicketListItem](#schematicketlistitem)]|false|none|List of available events in an excursions, to check|

<h2 id="tocS_GetActivityAvailabilityCalendarRS">GetActivityAvailabilityCalendarRS</h2>
<!-- backwards compatibility -->
<a id="schemagetactivityavailabilitycalendarrs"></a>
<a id="schema_GetActivityAvailabilityCalendarRS"></a>
<a id="tocSgetactivityavailabilitycalendarrs"></a>
<a id="tocsgetactivityavailabilitycalendarrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "months": [
    {
      "title": "string",
      "year": 0,
      "month": 0,
      "weeks": [
        {
          "days": [
            {
              "id": 0,
              "posInWeek": 0,
              "day": 0,
              "date": "string",
              "styleName": "string",
              "blank": false
            }
          ]
        }
      ]
    }
  ]
}

```

Container for the getavailability response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|months|[[ActivityAvailabilityCalendarMonth](#schemaactivityavailabilitycalendarmonth)]|false|none|List of available hotels, including prices|

<h2 id="tocS_Resource">Resource</h2>
<!-- backwards compatibility -->
<a id="schemaresource"></a>
<a id="schema_Resource"></a>
<a id="tocSresource"></a>
<a id="tocsresource"></a>

```json
{
  "resourceId": "string",
  "name": {
    "property1": "string",
    "property2": "string"
  },
  "type": "string",
  "longitude": "string",
  "latitude": "string",
  "description": {
    "property1": "string",
    "property2": "string"
  }
}

```

A resource inside our portfolio. E.g. a hotel, an activity, a car rental office, ...

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|resourceId|string|false|none|This resouce id|
|name|object|false|none|This resource name|
|» **additionalProperties**|string|false|none|none|
|type|string|false|none|Type of resource. E.g. HOTEL, ACTIVITY, TICKET, CARRENTALOFFICE, ...|
|longitude|string|false|none|Resource longitude accorging to google maps|
|latitude|string|false|none|Resource latitude accorging to google maps|
|description|object|false|none|Resource description|
|» **additionalProperties**|string|false|none|none|

<h2 id="tocS_HotelStay">HotelStay</h2>
<!-- backwards compatibility -->
<a id="schemahotelstay"></a>
<a id="schema_HotelStay"></a>
<a id="tocShotelstay"></a>
<a id="tocshotelstay"></a>

```json
{
  "start": 0,
  "end": 0,
  "roomId": "string",
  "roomName": "string",
  "boardBasisId": "string",
  "boardBasisName": "string",
  "numberOfRooms": 0,
  "paxPerRoom": 0,
  "ages": [
    0
  ]
}

```

A stay line inside a hotel booking service

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|start|integer(int32)|false|none|When this stay starts in locale. In YYYYMMDD format|
|end|integer(int32)|false|none|When this stay ends in locale. In YYYYMMDD format|
|roomId|string|false|none|The room id|
|roomName|string|false|none|The room name|
|boardBasisId|string|false|none|The board basis id|
|boardBasisName|string|false|none|The board basis name|
|numberOfRooms|integer(int32)|false|none|The number of rooms for this line|
|paxPerRoom|integer(int32)|false|none|How many pax will stay per room for this line|
|ages|[integer]|false|none|Ages for the pax. If ommited pax will be assumed to be an adult|

<h2 id="tocS_City">City</h2>
<!-- backwards compatibility -->
<a id="schemacity"></a>
<a id="schema_City"></a>
<a id="tocScity"></a>
<a id="tocscity"></a>

```json
{
  "resourceId": "string",
  "name": {
    "property1": "string",
    "property2": "string"
  },
  "urlFriendlyName": "string",
  "resources": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}

```

A city inside our portfolio. This is the third and last level in our product hierarchy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|resourceId|string|false|none|This city resource id|
|name|object|false|none|This city name|
|» **additionalProperties**|string|false|none|none|
|urlFriendlyName|string|false|none|The name in a url friendly manner|
|resources|[[Resource](#schemaresource)]|false|none|List of resources available inside this city. E.g. hotels, activities, car rental offices, ...|

<h2 id="tocS_CompanyData">CompanyData</h2>
<!-- backwards compatibility -->
<a id="schemacompanydata"></a>
<a id="schema_CompanyData"></a>
<a id="tocScompanydata"></a>
<a id="tocscompanydata"></a>

```json
{
  "name": "string",
  "legalText": "string",
  "contactPhone": "string",
  "contactEmail": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|none|
|legalText|string|false|none|none|
|contactPhone|string|false|none|none|
|contactEmail|string|false|none|none|

<h2 id="tocS_GetAirportsRS">GetAirportsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetairportsrs"></a>
<a id="schema_GetAirportsRS"></a>
<a id="tocSgetairportsrs"></a>
<a id="tocsgetairportsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "airports": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "type": "string",
      "longitude": "string",
      "latitude": "string",
      "description": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}

```

Container for the Airports response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|airports|[[Resource](#schemaresource)]|false|none|List of Airports.|

<h2 id="tocS_HotelAvailabilityCalendarWeek">HotelAvailabilityCalendarWeek</h2>
<!-- backwards compatibility -->
<a id="schemahotelavailabilitycalendarweek"></a>
<a id="schema_HotelAvailabilityCalendarWeek"></a>
<a id="tocShotelavailabilitycalendarweek"></a>
<a id="tocshotelavailabilitycalendarweek"></a>

```json
{
  "days": [
    {
      "id": 0,
      "posInWeek": 0,
      "day": 0,
      "date": "string",
      "styleName": "string",
      "blank": false
    }
  ]
}

```

A calendar week

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|days|[[HotelAvailabilityCalendarDay](#schemahotelavailabilitycalendarday)]|false|none|[A calendar day]|

<h2 id="tocS_Price">Price</h2>
<!-- backwards compatibility -->
<a id="schemaprice"></a>
<a id="schema_Price"></a>
<a id="tocSprice"></a>
<a id="tocsprice"></a>

```json
{
  "currencyIsoCode": "string",
  "retail": 0,
  "net": 0,
  "offer": false,
  "offerText": "string",
  "beforeOffer": 0
}

```

Holder for price

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|currencyIsoCode|string|false|none|Currency iso code for all prices|
|retail|number(double)|false|none|Retail price|
|net|number(double)|false|none|Net price|
|offer|boolean|false|none|True if this an offer price|
|offerText|string|false|none|Offer title, if available|
|beforeOffer|number(double)|false|none|Price before offer. Applies to retail price if present|

<h2 id="tocS_State">State</h2>
<!-- backwards compatibility -->
<a id="schemastate"></a>
<a id="schema_State"></a>
<a id="tocSstate"></a>
<a id="tocsstate"></a>

```json
{
  "resourceId": "string",
  "name": {
    "property1": "string",
    "property2": "string"
  },
  "urlFriendlyName": "string",
  "cities": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "urlFriendlyName": "string",
      "resources": [
        {
          "resourceId": "string",
          "name": {
            "property1": "string",
            "property2": "string"
          },
          "type": "string",
          "longitude": "string",
          "latitude": "string",
          "description": {
            "property1": "string",
            "property2": "string"
          }
        }
      ]
    }
  ]
}

```

An state inside our portfolio. This is the second level in our product hierarchy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|resourceId|string|false|none|This state resource id|
|name|object|false|none|This state name|
|» **additionalProperties**|string|false|none|none|
|urlFriendlyName|string|false|none|The name in a url friendly manner|
|cities|[[City](#schemacity)]|false|none|List of cities included in this state|

<h2 id="tocS_GetHotelPriceDetailsRS">GetHotelPriceDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagethotelpricedetailsrs"></a>
<a id="schema_GetHotelPriceDetailsRS"></a>
<a id="tocSgethotelpricedetailsrs"></a>
<a id="tocsgethotelpricedetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "status": "string",
  "total": {
    "currencyIsoCode": "string",
    "retail": 0,
    "net": 0,
    "offer": false,
    "offerText": "string",
    "beforeOffer": 0
  },
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "roomName": "string",
      "boardId": "string",
      "boardName": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ],
      "retailPrice": 0,
      "netPrice": 0,
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false,
      "availableSupplements": [
        {
          "id": "string",
          "description": "string",
          "price": 0
        }
      ]
    }
  ],
  "priceBreakdown": [
    {
      "description": "string",
      "total": 0
    }
  ],
  "cancellationCosts": [
    {
      "retail": 0,
      "net": 0,
      "gmttime": "string"
    }
  ],
  "cancellationFreeDate": "string",
  "remarks": [
    {
      "type": "string",
      "text": "string"
    }
  ],
  "paymentLines": [
    {
      "paymentMethod": "string",
      "date": "string",
      "amount": {
        "currencyIsoCode": "string",
        "value": 0
      }
    }
  ],
  "promoCodeMsg": "string",
  "terms": "string",
  "mailingUnwantedText": "string"
}

```

Container for the hotel price details response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|status|string|false|none|Status. Possible values are OK and ON REQUEST|
|total|[Price](#schemaprice)|false|none|Holder for price|
|stays|[[PricedStay](#schemapricedstay)]|false|none|List of stays (occupancies with desired room and board)|
|priceBreakdown|[[PriceLine](#schemapriceline)]|false|none|Price detail, in form of lines|
|cancellationCosts|[[CancellationCost](#schemacancellationcost)]|false|none|Cancellation costs|
|cancellationFreeDate|string|false|none|No cancellation cost until this date, yyyy-MM-dd formatted|
|remarks|[[Remark](#schemaremark)]|false|none|Remarks which should be visible for the customer|
|paymentLines|[[PaymentLine](#schemapaymentline)]|false|none|Detailed Payment lines|
|promoCodeMsg|string|false|none|Promo code application result|
|terms|string|false|none|Terms and conditions text. For website usage only|
|mailingUnwantedText|string|false|none|Mailing unwanted text. For website usage only|

<h2 id="tocS_Airport">Airport</h2>
<!-- backwards compatibility -->
<a id="schemaairport"></a>
<a id="schema_Airport"></a>
<a id="tocSairport"></a>
<a id="tocsairport"></a>

```json
{
  "id": "string",
  "name": "string",
  "city": "string",
  "state": "string",
  "country": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|city|string|false|none|none|
|state|string|false|none|none|
|country|string|false|none|none|

<h2 id="tocS_GetDataSheetRS">GetDataSheetRS</h2>
<!-- backwards compatibility -->
<a id="schemagetdatasheetrs"></a>
<a id="schema_GetDataSheetRS"></a>
<a id="tocSgetdatasheetrs"></a>
<a id="tocsgetdatasheetrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "values": [
    {
      "key": "string",
      "value": "string"
    }
  ]
}

```

Container for the getdatasheet response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|values|[[Pair](#schemapair)]|false|none|List of data associated with this resource, in a flatten manner|

<h2 id="tocS_GetBookingRS">GetBookingRS</h2>
<!-- backwards compatibility -->
<a id="schemagetbookingrs"></a>
<a id="schema_GetBookingRS"></a>
<a id="tocSgetbookingrs"></a>
<a id="tocsgetbookingrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "booking": {
    "bookingId": "string",
    "created": "string",
    "createdBy": "string",
    "modified": "string",
    "serviceType": "string",
    "serviceDescription": "string",
    "start": "string",
    "end": "string",
    "status": "string",
    "leadName": "string",
    "retail": 0,
    "net": 0,
    "currencyIsoCode": "string",
    "cancellationCost": [
      {
        "retail": 0,
        "net": 0,
        "gmttime": "string"
      }
    ],
    "commentsToProvider": "string",
    "privateComments": "string"
  }
}

```

Container for the getbookings response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|booking|[Booking](#schemabooking)|false|none|none|

<h2 id="tocS_GetPlainListRS">GetPlainListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetplainlistrs"></a>
<a id="schema_GetPlainListRS"></a>
<a id="tocSgetplainlistrs"></a>
<a id="tocsgetplainlistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ],
  "plainActivities": [
    {
      "id": "string",
      "description": "string",
      "htmlDescription": "string",
      "activityId": "string",
      "retailPrice": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "groupReference": "string",
      "groupDescription": "string"
    }
  ],
  "paymentMethods": [
    {
      "key": "string",
      "name": "string",
      "currencyIsoCode": "string"
    }
  ],
  "currencies": [
    {
      "name": "string",
      "value": 0
    }
  ],
  "companyData": {
    "name": "string",
    "legalText": "string",
    "contactPhone": "string",
    "contactEmail": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|activity|[[ActivityCheckItem](#schemaactivitycheckitem)]|false|none|List of available excursions, to check|
|plainActivities|[[PlainActivityItem](#schemaplainactivityitem)]|false|none|none|
|paymentMethods|[[PaymentMethod](#schemapaymentmethod)]|false|none|none|
|currencies|[[CurrencyChange](#schemacurrencychange)]|false|none|none|
|companyData|[CompanyData](#schemacompanydata)|false|none|none|

<h2 id="tocS_Supplement">Supplement</h2>
<!-- backwards compatibility -->
<a id="schemasupplement"></a>
<a id="schema_Supplement"></a>
<a id="tocSsupplement"></a>
<a id="tocssupplement"></a>

```json
{
  "id": "string",
  "description": "string",
  "price": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|description|string|false|none|none|
|price|number(double)|false|none|none|

<h2 id="tocS_CancelBookingRS">CancelBookingRS</h2>
<!-- backwards compatibility -->
<a id="schemacancelbookingrs"></a>
<a id="schema_CancelBookingRS"></a>
<a id="tocScancelbookingrs"></a>
<a id="tocscancelbookingrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_GetHotelPriceDetailsRQ">GetHotelPriceDetailsRQ</h2>
<!-- backwards compatibility -->
<a id="schemagethotelpricedetailsrq"></a>
<a id="schema_GetHotelPriceDetailsRQ"></a>
<a id="tocSgethotelpricedetailsrq"></a>
<a id="tocsgethotelpricedetailsrq"></a>

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "boardId": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ]
    }
  ],
  "promoCode": "string"
}

```

Rq to get hotel price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|language|string|false|none|2 char language iso code|
|hotelId|string|false|none|hotel id, as retrieved from hote available hotels response|
|checkin|integer(int32)|false|none|The locale checkin date in YYYYMMDD format|
|checkout|integer(int32)|false|none|The locale checkout date in YYYYMMDD format|
|stays|[[Stay](#schemastay)]|false|none|List of stays (occupancies with desired room and board)|
|promoCode|string|false|none|Promo code|

<h2 id="tocS_PaymentMethod">PaymentMethod</h2>
<!-- backwards compatibility -->
<a id="schemapaymentmethod"></a>
<a id="schema_PaymentMethod"></a>
<a id="tocSpaymentmethod"></a>
<a id="tocspaymentmethod"></a>

```json
{
  "key": "string",
  "name": "string",
  "currencyIsoCode": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|none|
|name|string|false|none|none|
|currencyIsoCode|string|false|none|none|

<h2 id="tocS_Option">Option</h2>
<!-- backwards compatibility -->
<a id="schemaoption"></a>
<a id="schema_Option"></a>
<a id="tocSoption"></a>
<a id="tocsoption"></a>

```json
{
  "roomId": "string",
  "roomName": "string",
  "roomDescription": "string",
  "image": "string",
  "prices": [
    {
      "boardBasisId": "string",
      "boardBasisName": "string",
      "retailPrice": 0,
      "netPrice": 0,
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false,
      "rateId": "string"
    }
  ],
  "allotment": 0
}

```

An available room and board combination the fits your occupancy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|roomId|string|false|none|This room type id|
|roomName|string|false|none|This room type name|
|roomDescription|string|false|none|This room description|
|image|string|false|none|This room main image|
|prices|[[OptionBoardPrice](#schemaoptionboardprice)]|false|none|List of available board basis and prices for each board|
|allotment|integer(int32)|false|none|Number of available rooms. Check if you plan to use the same room several times|

<h2 id="tocS_ActivityLanguage">ActivityLanguage</h2>
<!-- backwards compatibility -->
<a id="schemaactivitylanguage"></a>
<a id="schema_ActivityLanguage"></a>
<a id="tocSactivitylanguage"></a>
<a id="tocsactivitylanguage"></a>

```json
{
  "id": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocS_GetAvailableHotelsRS">GetAvailableHotelsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailablehotelsrs"></a>
<a id="schema_GetAvailableHotelsRS"></a>
<a id="tocSgetavailablehotelsrs"></a>
<a id="tocsgetavailablehotelsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "hotels": [
    {
      "hotelId": "string",
      "hotelName": "string",
      "hotelCategoryId": "string",
      "hotelCategoryName": "string",
      "stars": 0,
      "keys": 0,
      "longitude": "string",
      "latitude": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "address": "string",
      "mainImage": "string"
    }
  ],
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0
}

```

Container for the getavailability response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|hotels|[[AvailableHotel](#schemaavailablehotel)]|false|none|List of available hotels, including prices|
|labels|[[Label](#schemalabel)]|false|none|List of labels found in all the available hotels|
|minPrice|number(double)|false|none|Min price found|
|maxPrice|number(double)|false|none|Max price found|

<h2 id="tocS_ActivityShift">ActivityShift</h2>
<!-- backwards compatibility -->
<a id="schemaactivityshift"></a>
<a id="schema_ActivityShift"></a>
<a id="tocSactivityshift"></a>
<a id="tocsactivityshift"></a>

```json
{
  "id": "string",
  "name": "string",
  "languages": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "pickups": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|languages|[[ActivityLanguage](#schemaactivitylanguage)]|false|none|none|
|pickups|[[ActivityPickupPoint](#schemaactivitypickuppoint)]|false|none|none|

<h2 id="tocS_File">File</h2>
<!-- backwards compatibility -->
<a id="schemafile"></a>
<a id="schema_File"></a>
<a id="tocSfile"></a>
<a id="tocsfile"></a>

```json
{
  "fileId": "string",
  "bookings": [
    {
      "bookingId": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string",
      "serviceType": "string",
      "serviceDescription": "string",
      "start": "string",
      "end": "string",
      "status": "string",
      "leadName": "string",
      "retail": 0,
      "net": 0,
      "currencyIsoCode": "string",
      "cancellationCost": [
        {
          "retail": 0,
          "net": 0,
          "gmttime": "string"
        }
      ],
      "commentsToProvider": "string",
      "privateComments": "string"
    }
  ],
  "totalPrice": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "leadName": "string",
  "email": "string",
  "created": "string",
  "createdBy": "string",
  "modified": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|The File id|
|bookings|[[Booking](#schemabooking)]|false|none|File´s bookings list|
|totalPrice|[Amount](#schemaamount)|false|none|A currency - value pair|
|leadName|string|false|none|This service lead name|
|email|string|false|none|This service lead email|
|created|string|false|none|When this service was created. In ISO8651 format|
|createdBy|string|false|none|Who created this service booking|
|modified|string|false|none|Last modification date for this service in ISO8651 format|

<h2 id="tocS_GetPortfolioRS">GetPortfolioRS</h2>
<!-- backwards compatibility -->
<a id="schemagetportfoliors"></a>
<a id="schema_GetPortfolioRS"></a>
<a id="tocSgetportfoliors"></a>
<a id="tocsgetportfoliors"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "countries": [
    {
      "resourceId": "string",
      "name": {
        "property1": "string",
        "property2": "string"
      },
      "urlFriendlyName": "string",
      "states": [
        {
          "resourceId": "string",
          "name": {
            "property1": "string",
            "property2": "string"
          },
          "urlFriendlyName": "string",
          "cities": [
            {
              "resourceId": "string",
              "name": {
                "property1": "string",
                "property2": "string"
              },
              "urlFriendlyName": "string",
              "resources": [
                {
                  "resourceId": "string",
                  "name": {
                    "property1": "string",
                    "property2": "string"
                  },
                  "type": "string",
                  "longitude": "string",
                  "latitude": "string",
                  "description": {
                    "property1": "string",
                    "property2": "string"
                  }
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}

```

Container for the getportfolio response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|countries|[[Country](#schemacountry)]|false|none|List of countries. This is the first level in the portfolio hierarchy|

<h2 id="tocS_GetActivityCheckListRS">GetActivityCheckListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetactivitychecklistrs"></a>
<a id="schema_GetActivityCheckListRS"></a>
<a id="tocSgetactivitychecklistrs"></a>
<a id="tocsgetactivitychecklistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "activity": [
    {
      "activityId": "string",
      "name": "string",
      "description": "string",
      "image": "string",
      "date": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|activity|[[ActivityCheckItem](#schemaactivitycheckitem)]|false|none|List of available excursions, to check|

<h2 id="tocS_CartList">CartList</h2>
<!-- backwards compatibility -->
<a id="schemacartlist"></a>
<a id="schema_CartList"></a>
<a id="tocScartlist"></a>
<a id="tocscartlist"></a>

```json
{
  "fileId": "string",
  "agencyReference": "string",
  "productionCenterId": "string",
  "date": "string",
  "personaldata": {
    "hotel": "string",
    "telefono": "string",
    "titular": "string",
    "email": "string",
    "habitacion": "string",
    "comments": "string"
  },
  "total": "string",
  "payments": [
    {
      "amount": "string",
      "paymentMethod": {
        "key": "string",
        "name": "string",
        "currencyIsoCode": "string"
      },
      "currency": {
        "name": "string",
        "value": 0
      }
    }
  ],
  "cart": [
    {
      "precio": "string",
      "img": "string",
      "qty": "string",
      "id": "string",
      "nombre": "string",
      "nombreHtml": "string",
      "qrCode": "string",
      "groupReference": "string"
    }
  ],
  "status": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|agencyReference|string|false|none|none|
|productionCenterId|string|false|none|none|
|date|string|false|none|none|
|personaldata|[Personaldata](#schemapersonaldata)|false|none|none|
|total|string|false|none|none|
|payments|[[Payments](#schemapayments)]|false|none|none|
|cart|[[Cart](#schemacart)]|false|none|none|
|status|string|false|none|none|

<h2 id="tocS_GetRoomingListRS">GetRoomingListRS</h2>
<!-- backwards compatibility -->
<a id="schemagetroominglistrs"></a>
<a id="schema_GetRoomingListRS"></a>
<a id="tocSgetroominglistrs"></a>
<a id="tocsgetroominglistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookings": [
    {
      "bookingId": "string",
      "created": "string",
      "createdBy": "string",
      "modified": "string",
      "serviceType": "string",
      "serviceDescription": "string",
      "start": "string",
      "end": "string",
      "status": "string",
      "leadName": "string",
      "retailValue": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "netValue": {
        "currencyIsoCode": "string",
        "value": 0
      },
      "commentsToProvider": "string",
      "privateComments": "string",
      "stays": [
        {
          "start": 0,
          "end": 0,
          "roomId": "string",
          "roomName": "string",
          "boardBasisId": "string",
          "boardBasisName": "string",
          "numberOfRooms": 0,
          "paxPerRoom": 0,
          "ages": [
            0
          ]
        }
      ]
    }
  ]
}

```

Container for the getroominglist response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookings|[[HotelBooking](#schemahotelbooking)]|false|none|List of hotel bookings|

<h2 id="tocS_PaxDetails">PaxDetails</h2>
<!-- backwards compatibility -->
<a id="schemapaxdetails"></a>
<a id="schema_PaxDetails"></a>
<a id="tocSpaxdetails"></a>
<a id="tocspaxdetails"></a>

```json
{
  "firstName": "string",
  "surname": "string",
  "age": 0,
  "birthDate": 0,
  "type": "string",
  "documentType": "string",
  "documentId": "string",
  "groupId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|firstName|string|false|none|Passenger first name|
|surname|string|false|none|Passenger surname|
|age|integer(int32)|false|none|Passenger age|
|birthDate|integer(int32)|false|none|Passenger birth date|
|type|string|false|none|Passenger type. Possible values are: AD for adult and CH for child|
|documentType|string|false|none|Document type. Possible values are: DNI for DNI and PASS for passport|
|documentId|string|false|none|Passenger document id|
|groupId|string|false|none|E.g.: room number, vehicle, .... For presentation purposes only|

<h2 id="tocS_GeUpdatedTicketsRS">GeUpdatedTicketsRS</h2>
<!-- backwards compatibility -->
<a id="schemageupdatedticketsrs"></a>
<a id="schema_GeUpdatedTicketsRS"></a>
<a id="tocSgeupdatedticketsrs"></a>
<a id="tocsgeupdatedticketsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_ProductionCenter">ProductionCenter</h2>
<!-- backwards compatibility -->
<a id="schemaproductioncenter"></a>
<a id="schema_ProductionCenter"></a>
<a id="tocSproductioncenter"></a>
<a id="tocsproductioncenter"></a>

```json
{
  "id": "string",
  "name": "string",
  "hotelName": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|
|hotelName|string|false|none|none|

<h2 id="tocS_ActivityPickupPoint">ActivityPickupPoint</h2>
<!-- backwards compatibility -->
<a id="schemaactivitypickuppoint"></a>
<a id="schema_ActivityPickupPoint"></a>
<a id="tocSactivitypickuppoint"></a>
<a id="tocsactivitypickuppoint"></a>

```json
{
  "id": "string",
  "name": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|name|string|false|none|none|

<h2 id="tocS_GetPassengerDetailsRS">GetPassengerDetailsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetpassengerdetailsrs"></a>
<a id="schema_GetPassengerDetailsRS"></a>
<a id="tocSgetpassengerdetailsrs"></a>
<a id="tocsgetpassengerdetailsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "found": false,
  "agency": "string",
  "fileId": "string",
  "leadName": "string",
  "comments": "string",
  "prodCenterId": "string",
  "hotelName": "string",
  "roomNumber": "string",
  "telephone": "string",
  "email": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|found|boolean|false|none|none|
|agency|string|false|none|none|
|fileId|string|false|none|none|
|leadName|string|false|none|none|
|comments|string|false|none|none|
|prodCenterId|string|false|none|none|
|hotelName|string|false|none|none|
|roomNumber|string|false|none|none|
|telephone|string|false|none|none|
|email|string|false|none|none|

<h2 id="tocS_TicketListItem">TicketListItem</h2>
<!-- backwards compatibility -->
<a id="schematicketlistitem"></a>
<a id="schema_TicketListItem"></a>
<a id="tocSticketlistitem"></a>
<a id="tocsticketlistitem"></a>

```json
{
  "ticket": [
    {
      "id": "string",
      "qrcode": "string",
      "leadname": "string",
      "pax": 0,
      "checkedDate": 0,
      "checkedTime": 0,
      "checked": false,
      "comments": "string"
    }
  ],
  "totalTickets": 0,
  "checkedTickets": 0,
  "remainingTickets": 0,
  "totalPax": 0,
  "checkedPax": 0,
  "remainingPax": 0,
  "eventId": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|ticket|[[TicketCheckItem](#schematicketcheckitem)]|false|none|List of available events in an excursions, to check|
|totalTickets|integer(int32)|false|none|none|
|checkedTickets|integer(int32)|false|none|none|
|remainingTickets|integer(int32)|false|none|none|
|totalPax|integer(int32)|false|none|none|
|checkedPax|integer(int32)|false|none|none|
|remainingPax|integer(int32)|false|none|none|
|eventId|string|false|none|none|

<h2 id="tocS_Match">Match</h2>
<!-- backwards compatibility -->
<a id="schemamatch"></a>
<a id="schema_Match"></a>
<a id="tocSmatch"></a>
<a id="tocsmatch"></a>

```json
{
  "resourceId": "string",
  "name": "string",
  "description": "string",
  "metadata": {
    "property1": "string",
    "property2": "string"
  }
}

```

Container for a portfolio match

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|resourceId|string|false|none|Id to use in the availability search|
|name|string|false|none|Name for this resource|
|description|string|false|none|Description for this resource|
|metadata|object|false|none|Metadata for this resource|
|» **additionalProperties**|string|false|none|none|

<h2 id="tocS_MealPlansListRS">MealPlansListRS</h2>
<!-- backwards compatibility -->
<a id="schemamealplanslistrs"></a>
<a id="schema_MealPlansListRS"></a>
<a id="tocSmealplanslistrs"></a>
<a id="tocsmealplanslistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "mealPlans": [
    {
      "id": "string",
      "name": "string"
    }
  ]
}

```

Container for the getboards response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|mealPlans|[[MealPlan](#schemamealplan)]|false|none|The list of board basis|

<h2 id="tocS_Allocation">Allocation</h2>
<!-- backwards compatibility -->
<a id="schemaallocation"></a>
<a id="schema_Allocation"></a>
<a id="tocSallocation"></a>
<a id="tocsallocation"></a>

```json
{
  "numberOfRooms": 0,
  "paxPerRoom": 0,
  "ages": [
    0
  ],
  "options": [
    {
      "roomId": "string",
      "roomName": "string",
      "roomDescription": "string",
      "image": "string",
      "prices": [
        {
          "boardBasisId": "string",
          "boardBasisName": "string",
          "retailPrice": 0,
          "netPrice": 0,
          "offer": false,
          "offerText": "string",
          "onRequest": false,
          "onRequestText": "string",
          "nonRefundable": false,
          "rateId": "string"
        }
      ],
      "allotment": 0
    }
  ]
}

```

Matches one of your requested occupancies

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|numberOfRooms|integer(int32)|false|none|Number of rooms|
|paxPerRoom|integer(int32)|false|none|Pax per room|
|ages|[integer]|false|none|Ages. If not present we will assume the pax is an adult|
|options|[[Option](#schemaoption)]|false|none|List of available rooms and board basis with prices and available optional supplements|

<h2 id="tocS_UpdateBookingRS">UpdateBookingRS</h2>
<!-- backwards compatibility -->
<a id="schemaupdatebookingrs"></a>
<a id="schema_UpdateBookingRS"></a>
<a id="tocSupdatebookingrs"></a>
<a id="tocsupdatebookingrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|

<h2 id="tocS_GetEventCheckListRS">GetEventCheckListRS</h2>
<!-- backwards compatibility -->
<a id="schemageteventchecklistrs"></a>
<a id="schema_GetEventCheckListRS"></a>
<a id="tocSgeteventchecklistrs"></a>
<a id="tocsgeteventchecklistrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "event": [
    {
      "id": "string",
      "name": "string",
      "activityId": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|event|[[EventCheckItem](#schemaeventcheckitem)]|false|none|List of available events in an excursions, to check|

<h2 id="tocS_SearchPortfolioRS">SearchPortfolioRS</h2>
<!-- backwards compatibility -->
<a id="schemasearchportfoliors"></a>
<a id="schema_SearchPortfolioRS"></a>
<a id="tocSsearchportfoliors"></a>
<a id="tocssearchportfoliors"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "matches": [
    {
      "resourceId": "string",
      "name": "string",
      "description": "string",
      "metadata": {
        "property1": "string",
        "property2": "string"
      }
    }
  ]
}

```

Container for the searchportfolio response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|matches|[[Match](#schemamatch)]|false|none|List of matches|

<h2 id="tocS_BookCircuitRQ">BookCircuitRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookcircuitrq"></a>
<a id="schema_BookCircuitRQ"></a>
<a id="tocSbookcircuitrq"></a>
<a id="tocsbookcircuitrq"></a>

```json
{
  "fileId": "string",
  "key": "string",
  "date": 0,
  "language": "string",
  "shiftId": "string",
  "variantId": "string",
  "adults": 0,
  "children": 0,
  "infants": 0,
  "mailingUnwanted": false,
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "supplements": "string",
  "coupon": "string"
}

```

Parameters needed to confirm an circuit booking

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|key|string|false|none|none|
|date|integer(int32)|false|none|none|
|language|string|false|none|none|
|shiftId|string|false|none|none|
|variantId|string|false|none|none|
|adults|integer(int32)|false|none|none|
|children|integer(int32)|false|none|none|
|infants|integer(int32)|false|none|none|
|mailingUnwanted|boolean|false|none|none|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the circuit provider|
|privateComments|string|false|none|Your comments for us. They will not be visible to the customer neither to the circuit provider|
|phoneNumber|string|false|none|Your phone number to contact with you|
|email|string|false|none|User Email. Used to locate your bookings|
|captchaToken|string|false|none|Token for server validation captcha|
|supplements|string|false|none|Booking extras|
|coupon|string|false|none|Booking coupon discount|

<h2 id="tocS_GetGrantedHotelsRS">GetGrantedHotelsRS</h2>
<!-- backwards compatibility -->
<a id="schemagetgrantedhotelsrs"></a>
<a id="schema_GetGrantedHotelsRS"></a>
<a id="tocSgetgrantedhotelsrs"></a>
<a id="tocsgetgrantedhotelsrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "grantedHotels": [
    {
      "hotelId": "string",
      "hotelName": "string",
      "roomIds": [
        {
          "id": "string",
          "description": "string"
        }
      ]
    }
  ]
}

```

Container for the getgrantedhotels response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|grantedHotels|[[GrantedHotel](#schemagrantedhotel)]|false|none|List of the granted hotels (and room ids, board basis ids, ...)|

<h2 id="tocS_GrantedHotel">GrantedHotel</h2>
<!-- backwards compatibility -->
<a id="schemagrantedhotel"></a>
<a id="schema_GrantedHotel"></a>
<a id="tocSgrantedhotel"></a>
<a id="tocsgrantedhotel"></a>

```json
{
  "hotelId": "string",
  "hotelName": "string",
  "roomIds": [
    {
      "id": "string",
      "description": "string"
    }
  ]
}

```

Contains hotel information like rooms ids, etc

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|hotelId|string|false|none|Thid hotel id|
|hotelName|string|false|none|This hotel name|
|roomIds|[[RoomId](#schemaroomid)]|false|none|List of room ids valid for this hotel|

<h2 id="tocS_Pair">Pair</h2>
<!-- backwards compatibility -->
<a id="schemapair"></a>
<a id="schema_Pair"></a>
<a id="tocSpair"></a>
<a id="tocspair"></a>

```json
{
  "key": "string",
  "value": "string"
}

```

Pair name-value container

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|key|string|false|none|The name of this property|
|value|string|false|none|The associated value|

<h2 id="tocS_GetHotelRatesRS">GetHotelRatesRS</h2>
<!-- backwards compatibility -->
<a id="schemagethotelratesrs"></a>
<a id="schema_GetHotelRatesRS"></a>
<a id="tocSgethotelratesrs"></a>
<a id="tocsgethotelratesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "currencyIsoCode": "string",
  "rates": [
    {
      "numberOfRooms": 0,
      "paxPerRoom": 0,
      "ages": [
        0
      ],
      "options": [
        {
          "roomId": "string",
          "roomName": "string",
          "roomDescription": "string",
          "image": "string",
          "prices": [
            {
              "boardBasisId": "string",
              "boardBasisName": "string",
              "retailPrice": 0,
              "netPrice": 0,
              "offer": false,
              "offerText": "string",
              "onRequest": false,
              "onRequestText": "string",
              "nonRefundable": false,
              "rateId": "string"
            }
          ],
          "allotment": 0
        }
      ]
    }
  ]
}

```

Container for the getavailability response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|currencyIsoCode|string|false|none|Currency iso code for all rates|
|rates|[[Allocation](#schemaallocation)]|false|none|List of occupancies with available rates and supplements|

<h2 id="tocS_GetHotelRatesRQ">GetHotelRatesRQ</h2>
<!-- backwards compatibility -->
<a id="schemagethotelratesrq"></a>
<a id="schema_GetHotelRatesRQ"></a>
<a id="tocSgethotelratesrq"></a>
<a id="tocsgethotelratesrq"></a>

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "occupancies": "string"
}

```

Rq to get available hotel rates for each occupancy

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|language|string|false|none|2 char language iso code|
|hotelId|string|false|none|hotel id, as retrieved from hote available hotels response|
|checkin|integer(int32)|false|none|The locale checkin date in YYYYMMDD format|
|checkout|integer(int32)|false|none|The locale checkout date in YYYYMMDD format|
|occupancies|string|false|none|Same as passed to the availability request. List comma separated list of occupancies you need in <nr of rooms>x<pax>[-<age>]* format. E.g.: 2x4-10-6-2,1x2 means 2 rooms occupied by 4 pax where 3 of them are 10, 6 and 2 years old and 1 room occupied by 2 pax|

<h2 id="tocS_BookCircuitRS">BookCircuitRS</h2>
<!-- backwards compatibility -->
<a id="schemabookcircuitrs"></a>
<a id="schema_BookCircuitRS"></a>
<a id="tocSbookcircuitrs"></a>
<a id="tocsbookcircuitrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

Response for the circuit booking confirmation

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|fileId|string|false|none|none|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_BookActivityRS">BookActivityRS</h2>
<!-- backwards compatibility -->
<a id="schemabookactivityrs"></a>
<a id="schema_BookActivityRS"></a>
<a id="tocSbookactivityrs"></a>
<a id="tocsbookactivityrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

Response for the activity booking confirmation

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|fileId|string|false|none|none|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_GetAvailableTransfersRS">GetAvailableTransfersRS</h2>
<!-- backwards compatibility -->
<a id="schemagetavailabletransfersrs"></a>
<a id="schema_GetAvailableTransfersRS"></a>
<a id="tocSgetavailabletransfersrs"></a>
<a id="tocsgetavailabletransfersrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "labels": [
    {
      "id": "string",
      "name": "string"
    }
  ],
  "minPrice": 0,
  "maxPrice": 0,
  "availableTransfers": [
    {
      "key": "string",
      "type": "string",
      "vehicle": "string",
      "description": "string",
      "image": "string",
      "total": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "offer": false,
      "offerText": "string",
      "onRequest": false,
      "onRequestText": "string",
      "nonRefundable": false
    }
  ]
}

```

Container for the getavailabletransfers response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|labels|[[Label](#schemalabel)]|false|none|none|
|minPrice|number(double)|false|none|none|
|maxPrice|number(double)|false|none|none|
|availableTransfers|[[AvailableTransfer](#schemaavailabletransfer)]|false|none|List of available transfers and their prices|

<h2 id="tocS_GetUpdatedCartsRQ">GetUpdatedCartsRQ</h2>
<!-- backwards compatibility -->
<a id="schemagetupdatedcartsrq"></a>
<a id="schema_GetUpdatedCartsRQ"></a>
<a id="tocSgetupdatedcartsrq"></a>
<a id="tocsgetupdatedcartsrq"></a>

```json
{
  "userId": "string",
  "cartList": [
    {
      "fileId": "string",
      "agencyReference": "string",
      "productionCenterId": "string",
      "date": "string",
      "personaldata": {
        "hotel": "string",
        "telefono": "string",
        "titular": "string",
        "email": "string",
        "habitacion": "string",
        "comments": "string"
      },
      "total": "string",
      "payments": [
        {
          "amount": "string",
          "paymentMethod": {
            "key": "string",
            "name": "string",
            "currencyIsoCode": "string"
          },
          "currency": {
            "name": "string",
            "value": 0
          }
        }
      ],
      "cart": [
        {
          "precio": "string",
          "img": "string",
          "qty": "string",
          "id": "string",
          "nombre": "string",
          "nombreHtml": "string",
          "qrCode": "string",
          "groupReference": "string"
        }
      ],
      "status": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|userId|string|false|none|none|
|cartList|[[CartList](#schemacartlist)]|false|none|none|

<h2 id="tocS_GetActivityRatesRS">GetActivityRatesRS</h2>
<!-- backwards compatibility -->
<a id="schemagetactivityratesrs"></a>
<a id="schema_GetActivityRatesRS"></a>
<a id="tocSgetactivityratesrs"></a>
<a id="tocsgetactivityratesrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "variants": [
    {
      "key": "string",
      "name": "string",
      "description": "string",
      "bestDeal": {
        "currencyIsoCode": "string",
        "retail": 0,
        "net": 0,
        "offer": false,
        "offerText": "string",
        "beforeOffer": 0
      },
      "pricePer": "string"
    }
  ],
  "shifts": [
    {
      "id": "string",
      "name": "string",
      "languages": [
        {
          "id": "string",
          "name": "string"
        }
      ],
      "pickups": [
        {
          "id": "string",
          "name": "string"
        }
      ]
    }
  ]
}

```

Container for the activity price details

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|variants|[[ActivityVariant](#schemaactivityvariant)]|false|none|none|
|shifts|[[ActivityShift](#schemaactivityshift)]|false|none|none|

<h2 id="tocS_UpdateOperation">UpdateOperation</h2>
<!-- backwards compatibility -->
<a id="schemaupdateoperation"></a>
<a id="schema_UpdateOperation"></a>
<a id="tocSupdateoperation"></a>
<a id="tocsupdateoperation"></a>

```json
{
  "hotelId": "string",
  "roomId": "string",
  "action": "string",
  "startDate": 0,
  "endDate": 0,
  "newValue": "string"
}

```

Describes an update operation, like modifying allotment, prices or stop sales

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|hotelId|string|false|none|Hotel id you got when you called the getgrantedhotels method|
|roomId|string|false|none|Room id you got when you called the getgrantedhotels method|
|action|string|false|none|Action you want to perform. E.g. STOPSALES, OPENSALES, SETPRICE, SETALLOTMENT, ...|
|startDate|integer(int32)|false|none|Locale date this data starts appliance. In format YYYMMDD|
|endDate|integer(int32)|false|none|Locale date this data ends appliance. In format YYYMMDD|
|newValue|string|false|none|New value to be set|

<h2 id="tocS_CheckActivityRS">CheckActivityRS</h2>
<!-- backwards compatibility -->
<a id="schemacheckactivityrs"></a>
<a id="schema_CheckActivityRS"></a>
<a id="tocScheckactivityrs"></a>
<a id="tocscheckactivityrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "available": false,
  "value": {
    "currencyIsoCode": "string",
    "value": 0
  },
  "key": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|available|boolean|false|none|none|
|value|[Amount](#schemaamount)|false|none|A currency - value pair|
|key|string|false|none|none|

<h2 id="tocS_BookHotelRS">BookHotelRS</h2>
<!-- backwards compatibility -->
<a id="schemabookhotelrs"></a>
<a id="schema_BookHotelRS"></a>
<a id="tocSbookhotelrs"></a>
<a id="tocsbookhotelrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

Container for the hotel booking confirmation response

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The booking id|
|fileId|string|false|none|The file id|
|availableServices|[string]|false|none|Available services for upselling|
|paymentUrl|string|false|none|Generated URL to pay|

<h2 id="tocS_HotelAvailabilityCalendarDay">HotelAvailabilityCalendarDay</h2>
<!-- backwards compatibility -->
<a id="schemahotelavailabilitycalendarday"></a>
<a id="schema_HotelAvailabilityCalendarDay"></a>
<a id="tocShotelavailabilitycalendarday"></a>
<a id="tocshotelavailabilitycalendarday"></a>

```json
{
  "id": 0,
  "posInWeek": 0,
  "day": 0,
  "date": "string",
  "styleName": "string",
  "blank": false
}

```

A calendar day

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int32)|false|none|none|
|posInWeek|integer(int32)|false|none|none|
|day|integer(int32)|false|none|none|
|date|string|false|none|none|
|styleName|string|false|none|none|
|blank|boolean|false|none|none|

<h2 id="tocS_TicketCheckItem">TicketCheckItem</h2>
<!-- backwards compatibility -->
<a id="schematicketcheckitem"></a>
<a id="schema_TicketCheckItem"></a>
<a id="tocSticketcheckitem"></a>
<a id="tocsticketcheckitem"></a>

```json
{
  "id": "string",
  "qrcode": "string",
  "leadname": "string",
  "pax": 0,
  "checkedDate": 0,
  "checkedTime": 0,
  "checked": false,
  "comments": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|string|false|none|none|
|qrcode|string|false|none|none|
|leadname|string|false|none|none|
|pax|integer(int32)|false|none|none|
|checkedDate|integer(int32)|false|none|none|
|checkedTime|integer(int32)|false|none|none|
|checked|boolean|false|none|none|
|comments|string|false|none|none|

<h2 id="tocS_BookFlightRQ">BookFlightRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookflightrq"></a>
<a id="schema_BookFlightRQ"></a>
<a id="tocSbookflightrq"></a>
<a id="tocsbookflightrq"></a>

```json
{
  "fileId": "string",
  "departureKey": "string",
  "returnKey": "string",
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "contactPhone": "string",
  "email": "string",
  "captchaToken": "string",
  "language": "string",
  "supplements": "string",
  "promoCode": "string",
  "mailingUnwanted": false,
  "pax": [
    {
      "firstName": "string",
      "surname": "string",
      "age": 0,
      "birthDate": 0,
      "type": "string",
      "documentType": "string",
      "documentId": "string",
      "groupId": "string"
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|departureKey|string|false|none|none|
|returnKey|string|false|none|none|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the activity provider|
|privateComments|string|false|none|Your comments for us. They will not be visible to the customer neither to the activity provider|
|contactPhone|string|false|none|Contact telephone number|
|email|string|false|none|User Email. Used to locate your bookings|
|captchaToken|string|false|none|Token for server validation captcha|
|language|string|false|none|User language|
|supplements|string|false|none|Booking extras|
|promoCode|string|false|none|Booking promo code for discount|
|mailingUnwanted|boolean|false|none|none|
|pax|[[PaxDetails](#schemapaxdetails)]|false|none|Passengers info. Applies only when confirming|

<h2 id="tocS_BookHotelRQ">BookHotelRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookhotelrq"></a>
<a id="schema_BookHotelRQ"></a>
<a id="tocSbookhotelrq"></a>
<a id="tocsbookhotelrq"></a>

```json
{
  "language": "string",
  "hotelId": "string",
  "checkin": 0,
  "checkout": 0,
  "stays": [
    {
      "occupancy": "string",
      "roomId": "string",
      "boardId": "string",
      "rateId": "string",
      "supplements": "string",
      "pax": [
        {
          "firstName": "string",
          "surname": "string",
          "age": 0,
          "birthDate": 0,
          "type": "string",
          "documentType": "string",
          "documentId": "string",
          "groupId": "string"
        }
      ]
    }
  ],
  "promoCode": "string",
  "fileId": "string",
  "bookingReference": "string",
  "leadName": "string",
  "email": "string",
  "phoneNumber": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "captchaToken": "string",
  "mailingUnwanted": false
}

```

Container for the hotel booking confirmation request

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|language|string|false|none|2 char language iso code|
|hotelId|string|false|none|hotel id, as retrieved from hote available hotels response|
|checkin|integer(int32)|false|none|The locale checkin date in YYYYMMDD format|
|checkout|integer(int32)|false|none|The locale checkout date in YYYYMMDD format|
|stays|[[Stay](#schemastay)]|false|none|List of stays (occupancies with desired room and board)|
|promoCode|string|false|none|Promo code|
|fileId|string|false|none|none|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|email|string|false|none|User Email. Used to locate your bookings|
|phoneNumber|string|false|none|Your phone number to contact with you|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the activity provider|
|privateComments|string|false|none|Your comments for us. They will not be visible to the customer neither to the activity provider|
|captchaToken|string|false|none|Token for server validation captcha|
|mailingUnwanted|boolean|false|none|Set to true if the customer does not want to receive publicity and info emails|

<h2 id="tocS_BookActivityRQ">BookActivityRQ</h2>
<!-- backwards compatibility -->
<a id="schemabookactivityrq"></a>
<a id="schema_BookActivityRQ"></a>
<a id="tocSbookactivityrq"></a>
<a id="tocsbookactivityrq"></a>

```json
{
  "fileId": "string",
  "key": "string",
  "pickup": "string",
  "date": 0,
  "language": "string",
  "activityLanguage": "string",
  "shiftId": "string",
  "adults": 0,
  "children": 0,
  "infants": 0,
  "supplementIds": "string",
  "mailingUnwanted": false,
  "bookingReference": "string",
  "leadName": "string",
  "commentsToProvider": "string",
  "privateComments": "string",
  "roomNumber": "string",
  "phoneNumber": "string",
  "email": "string",
  "captchaToken": "string",
  "supplements": "string",
  "coupon": "string"
}

```

Parameters needed to confirm an activity booking

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|fileId|string|false|none|none|
|key|string|false|none|none|
|pickup|string|false|none|none|
|date|integer(int32)|false|none|none|
|language|string|false|none|none|
|activityLanguage|string|false|none|none|
|shiftId|string|false|none|none|
|adults|integer(int32)|false|none|none|
|children|integer(int32)|false|none|none|
|infants|integer(int32)|false|none|none|
|supplementIds|string|false|none|none|
|mailingUnwanted|boolean|false|none|none|
|bookingReference|string|false|none|A free text reference you want to appear in the final invoice, so you can match it when validating our invoices|
|leadName|string|false|none|The lead name|
|commentsToProvider|string|false|none|Comments from the customer which should arrive to the activity provider|
|privateComments|string|false|none|Your comments for us. They will not be visible to the customer neither to the activity provider|
|roomNumber|string|false|none|Your room number to contact with you|
|phoneNumber|string|false|none|Your phone number to contact with you|
|email|string|false|none|Your email to contact with tou|
|captchaToken|string|false|none|Token for server validation captcha|
|supplements|string|false|none|Booking extras|
|coupon|string|false|none|Booking coupon discount|

<h2 id="tocS_BookFlightRS">BookFlightRS</h2>
<!-- backwards compatibility -->
<a id="schemabookflightrs"></a>
<a id="schema_BookFlightRS"></a>
<a id="tocSbookflightrs"></a>
<a id="tocsbookflightrs"></a>

```json
{
  "statusCode": 0,
  "msg": "string",
  "systemTime": "string",
  "bookingId": "string",
  "fileId": "string",
  "availableServices": [
    "string"
  ],
  "paymentUrl": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|statusCode|integer(int32)|false|none|status code for the operation. It will be 200 if it was OK and any other value if something went wrong. Provider dependant|
|msg|string|false|none|error message, if needed|
|systemTime|string|false|none|System time in ISO8651 format. Useful for bug resolution|
|bookingId|string|false|none|The resultant booking id. You will use it to later cancel the service, if you need to|
|fileId|string|false|none|none|
|availableServices|[string]|false|none|Available services to upsale your booking|
|paymentUrl|string|false|none|Generated URL to pay|

