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

특정 Order 정보를 전달합니다.

Project와 Order의 관계는 [Z.8 Appendix - Project & Order](https://www.notion.so/Z-8-Appendix-Project-Order-96781ed1b93a49098b6261a97dcc05b5) 문서를 참고해주시기 바랍니다.

### Resource Information

```jsx
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
| _orderId | String | Order의 고유 ID |

### Response Body Structure

**success**

```jsx
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
| _id | String | Project 고유 ID |
| sk | String | Order의 Key |
| ownerGroupId | String | Project를 생성한 Group의 고유 ID |
| labId | String | Order를 받은 Group의 고유 ID |
| status | String | Status ID |
| statusName | String | Status title |
| statusType | String | Status type ( NEW, INPROGRESS, CLOSED ) |
| product | Object | 상품의 정보 Object |
|   currency | String | 결제 통화 단위 |
|   discount | String | 할인률 또는 할인 정보 |
|   price | Number | 가격 |
|   productname | String | 상품의 이름 |
| patientId | String | 환자의 ID |
| subject | Object | 환자 정보 OBject |
|   name | String | 환자의 이름 |
|   birth | String | 환자의 생년월일 |
| memo | String | 주문에 대한 추가 코멘트 |
| medicalRecords | Object | 환자의 상태 정보 |
| treatments | Object Array | 치료 계획 |
| workflow | Object | 주문의 Flow |
| created | Number | 사용자의 Type(user, manager) |
| updated | Number | 사용자의 고유 ID |

## 4.2.2 Update order status

### Summary

Order의 Status를 변경할 수 있습니다.

변경된 이력은 모두 해당 Project의 History에 기록됩니다. [Z.2 Appendix - Custom Data Type](https://www.notion.so/Z-2-Appendix-Custom-Data-Type-fb8485fa8bd44b42a6422688947b9096) 참고

### Resource Information

```jsx
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

```jsx
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

<aside>
❓ `status`, `statusName` 값은 [4.6.1 Get product information](https://www.notion.so/4-6-1-Get-product-information-d11db68fefea430fad615312d64d83b1) 문서를 참고

</aside>

### Response Body Structure

**success**

```jsx
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

<aside>
❓ [4.5.1 Get order information](https://www.notion.so/4-5-1-Get-order-information-bcc5b2da29e24f0d98c18be3cae29413) 의 Response와 동일합니다.
즉, Update된 Order object가 그대로 전달됩니다.

</aside>

**Product & workflow**

주문은 Product에 의해서 생성됩니다. Product에 대한 기본 정보는 Order에 담겨있습니다.

또한, Product은 Workflow를 가지고 있습니다. 상품/서비스마다 주문에 대한 프로세스가 다르기 때문입니다.

관련해서는 [4.6.1 Get product information](https://www.notion.so/4-6-1-Get-product-information-d11db68fefea430fad615312d64d83b1) 정보를 확인해주시기 바랍니다.