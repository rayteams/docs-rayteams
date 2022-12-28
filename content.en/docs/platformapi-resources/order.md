---
title: "4.5 Order"
weight: 5
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.5.1 Get order information

### Summary

Deliver specific order information.

Please refer to the [Z.7 Appendix - Project & Order](/docs/platformapi-appendix/project-and-order/) document for the relationship between Project and Order.

### Resource Information

```
GET /order/{_orderId}
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
| _orderId | String | Order's unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
    "sk": "order:1669346270408",
    "ownerGroupId": "62dfdb179a4e3409ba649869",
    "labId": "fd6ede0f-8bce-4316-a54c-38ae893964a3",
    "status": "node_1669006551572",
    "statusName": "Wait Response",
    "statusType": "INPROGRESS",
    "product": {
      "currency": "원",
      "discount": "10",
      "price": 360000,
      "productname": "투명 교정 기본 B형",
    },
    "patientId": "NEW-0003",
    "subject": {
      "name" : "Tester",
      "birth" : "1981-12-12"
    },
    "memo": "주문 신청",
    "medicalRecords": {...},
    "treatments": [
      {...}
    ],
    "workflow": {...},
    "created": 1669346270408,
    "updated": 1669399728318,
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |
| sk | String | Order's Key |
| ownerGroupId | String | Group's unique ID that created Project |
| labId | String | Order's unique ID |
| status | String | Status ID |
| statusName | String | Status title |
| statusType | String | Status type ( NEW, INPROGRESS, CLOSED ) |
| product | Object | Product information Object |
|   currency | String | Payment unit |
|   discount | String | Discount rate or discount information |
|   price | Number | Price |
|   productname | String | Product name |
| patientId | String | Patient ID |
| subject | Object | Patient information OBject |
|   name | String | Patient name |
|   birth | String | Patient birthday |
| memo | String | Additional comments on orders |
| medicalRecords | Object | Patient status information |
| treatments | Object Array | Treatment plan |
| workflow | Object | Order Flow |
| created | Number | User Type(user, manager) |
| updated | Number | User's unique ID |

## 4.2.2 Update order status

### Summary

You can change the status of the order.

All changed history is recorded in the History of the Project. [Z.2 Appendix - Custom Data Type](/docs/platformapi-appendix/custom-data-type/)

### Resource Information

```
PUT /order/{_id}/status
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

### Request Body Structure

```
{
  "data": {
    "status": "node_1669006551533",
    "statusName": "Confirmed"
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| status | String | Status ID |
| statusName | String | Status title |

'Status', `StatusName` value refer to [4.6.1 Get product information](/docs/platformapi-resources/project/#432-get-project-information) documentation

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
    "sk": "order:1669346270408",
    "ownerGroupId": "62dfdb179a4e3409ba649869",
    "labId": "fd6ede0f-8bce-4316-a54c-38ae893964a3",
    "status": "node_1669006551533",
    "statusName": "Confirmed",
    "statusType": "INPROGRESS",
    "product": {
      "currency": "원",
      "discount": "10",
      "price": 360000,
      "productname": "투명 교정 기본 B형",
    },
    "patientId": "NEW-0003",
    "subject": {
      "name" : "Tester",
      "birth" : "1981-12-12"
    },
    "memo": "주문 신청",
    "medicalRecords": {...},
    "treatments": [
      {...}
    ],
    "workflow": {...},
    "created": 1669346270408,
    "updated": 1669399728318,
  }
}
```

Same as the response of [4.5.1 Get order information](/docs/platformapi-resources/order/#451-get-order-information).
In other words, the update order object is delivered as it is.

**Product & workflow**

The order is created by Product.Basic information about the product is contained in the order.

In addition, the product has a workflow.This is because the process of ordering is different for each product/service.

Please check the [4.6.1 Get product information](/docs/platformapi-resources/product/#461-get-product-information) information.