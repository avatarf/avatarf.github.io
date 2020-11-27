## How to ucs endpoint

The `ucs endpoint` is a centralized system to recive orders from the netpincer and from websites hosted by the ucs company.


## Terminal endpoints


### Get netpincer orders

This endpoint retrives the orders from the givven time frame (or the last x number of orders). The returned json list's `purchases` item holds all the orders. Each of the items contains the whole order json.

Path: `/ucs_eps/v1/<token>/orders/<object_id>`
- `token` -- letters, numbers
- `object_id` -- number,the object id from the rkeeper system. It has to be registered in the endpoint server too. eg.: 109150001

Accepted params:
- `count` -- the max number of returned items (max 100!); integer
- `start_time` -- orders after this time; format 2018-07-29T14:44:30
- `end_time` -- orders before this time; format 2018-07-30T14:44:30
If the `start_time` and the `end_time` is defined, the `count` is ignored.

Request example: `/ucs_eps/v1/mynicetoken1234345/orders/1999900001` 
Example item json 👇
  
```
{
  "token": "5f373562-591a-4db9-8609-7eec7880f28d",
  "code": "n0s1-w0k1",
  "comments": {
    "customerComment": "Please hurry, I am hungry",
    "vendorComment": ""
  },
  "createdAt": "2016-03-14T17:00:00.000Z",
  "customer": {
    "email": "s188sduisddsnjknsj",
    "firstName": "food",
    "lastName": "panda",
    "mobilePhone": "+49 99999999",
    "code": "dummy_customer_code",
    "id": "dummy_customer_Id",
    "mobilePhoneCountryCode": ""
  },
  "delivery": {
    "address": {},
    "expectedDeliveryTime": "2016-03-14T17:50:00.000Z",
    "expressDelivery": false,
    "riderPickupTime": "2016-03-14T17:35:00.000Z"
  },
  "discounts": [
    {}
  ],
  "expeditionType": "pickup",
  "expiryDate": "2016-03-14T17:15:00.000Z",
  "extraParameters": {
    "property1": "string",
    "property2": "string"
  },
  "localInfo": {
    "countryCode": "de",
    "currencySymbol": "€",
    "platform": "Foodpanda",
    "platformKey": "FP_MY",
    "currencySymbolPosition": "",
    "currencySymbolSpaces": "",
    "decimalDigits": "",
    "decimalSeparator": "",
    "email": "",
    "phone": "",
    "thousandsSeparator": "",
    "website": ""
  },
  "payment": {
    "status": "online",
    "type": "paid",
    "remoteCode": "online",
    "requiredMoneyChange": "",
    "vatId": "",
    "vatName": ""
  },
  "test": false,
  "shortCode": "42",
  "preOrder": false,
  "pickup": null,
  "platformRestaurant": {
    "id": "sq-abcd"
  },
  "price": {
    "deliveryFees": [],
    "grandTotal": "25.50",
    "minimumDeliveryValue": "9.99",
    "payRestaurant": "25.50",
    "riderTip": "1.20",
    "subTotal": "19.45",
    "vatTotal": "2.50",
    "comission": "",
    "containerCharge": "",
    "deliveryFee": "12.80",
    "discountAmountTotal": "2.50",
    "deliveryFeeDiscount": "",
    "serviceFeePercent": "",
    "serviceFeeTotal": "",
    "serviceTax": 0,
    "serviceTaxValue": 0,
    "differenceToMinimumDeliveryValue": "",
    "vatVisible": true,
    "vatPercent": "string"
  },
  "products": [
    {}
  ],
  "corporateOrder": false,
  "integrationInfo": { },
  "mobileOrder": true,
  "webOrder": false,
  "vouchers": [ ]
}
```

### Get website orders

Path: `/ucs_eps/v1/<token>/d_orders/<object_id>`
- `token` -- letters, numbers
- `object_id` -- number; the object id from the rkeeper system. It has to be registered in the endpoint server too. eg.: 109150001

Accepted params:
- `count` -- the max number of returned items (max 100!), default value is 10 | integer
- `start_time` -- orders after this time; format 2018-07-29T14:44:30
- `end_time` -- orders before this time; format 2018-07-30T14:44:30
If the `start_time` and the `end_time` is defined, the `count` is ignored.


Request example: `/ucs_eps/v1/mynicetoken1234345/d_orders/1999900001` 
Example item json:

```
{
  "remoteid": "199950001",
  "objectid": "199950001",
  "delivery_time": "2020-11-27T15:50:00",
  "comment": "",
  "order_type": 1,
  "pay_type": 0,
  "pay_online_type": 0,
  "client": {
    "phone": "+36 99 999-0000",
    "ln": "Test",
    "fn": "elek",
    "email": "elek@test.com"
  },
  "address": {
    "country": "Magyarország",
    "city": "Alap varos",
    "street": "Teszt",
    "house": "83",
    "floor": "",
    "building": "",
    "entry": "",
    "apartments": "",
    "zip": "0001"
  },
  "order": [
    {
      "id": 1002026,
      "qnt": 1000,
      "type": "d",
      "items": [
        {
          "id": 1001090,
          "qnt": 1000,
          "type": "m",
          "items": []
        }
      ]
    },
    {
      "id": 1006800,
      "qnt": 1000,
      "type": "c",
      "items": [
        {
          "id": 1001132,
          "qnt": 1000,
          "type": "cc",
          "items": [
            {
              "id": 1001871,
              "qnt": 1000,
              "type": "m",
              "items": []
            },
            {
              "id": 1001874,
              "qnt": 1000,
              "type": "m",
              "items": []
            },
            {
              "id": 1001112,
              "qnt": 1000,
              "type": "m",
              "items": []
            }
          ]
        },
        {
          "id": 1001176,
          "qnt": 1000,
          "type": "cc",
          "items": []
        },
        {
          "id": 1002497,
          "qnt": 1000,
          "type": "cc",
          "items": [
            {
              "id": 1002503,
              "qnt": 1000,
              "type": "m",
              "items": []
            }
          ]
        }
      ]
    }
  ],
  "order_number": 176,
  "CreateTime": "2020-11-27T15:41:25"
}
```
