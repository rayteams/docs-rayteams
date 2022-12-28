---
title: "4.6 Product"
weight: 6
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.6.1 Get product information

### Summary

Deliver the program information of the order.

You can agree with the terms and conditions for each product.

### Resource Information

```
GET /product/{_productId}
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | GROUP |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _productId | String | Product의 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "_id": "e40bd99e-67f2-45ea-ab64-d1cfc79f403c",
    "sk": "cid:KR",
    "currency": "USD",
    "discount": "10%",
    "originalprice": 600,
    "price": 540,
    "productname": "Product A",
    "description": "Description...",
    "terms": "Terms content",
    "link" : "https://~",
    "workflow": [
      {
        "status" : "node_1669006551533",
        "statusName" : "Confirmed",
        "statusType" : "INPROGRESS"
      },{
        "status" : "ewb-4",
        "statusName" : "Done",
        "statusType" : "CLOSED"
      },
      {...},
      ...
    ],
    "created": 1669373634943,
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |
| sk | String | Country code to be sold, [Z.5 Country Code](/docs/platformapi-appendix/country-code/) |
| currency | String | Call unit of product price |
| discount | String | Discount rate or discount price |
| originalprice | String | Basic price of product/service |
| price | String | Product/Service Price Price |
| productname | String | Name of product/service |
| description | Object | Details of the product/service |
| terms | String | Terms of service |
| link | Object | Related detailed information link |
| workflow | Object Array | Order Process |
|   status | String | Status Id |
|   statusName | String | Status Title |
|   statusType | String | Status Type ( NEW / INPROGRESS / CLOSED ) |
| created | Object | Created date |