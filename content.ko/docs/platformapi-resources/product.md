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

주문의 Prouct 정보를 전달합니다.

Product 마다 이용약관을 동의 받을 수 있습니다.

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
			"workflow": [{
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
| _id | String | Project 고유 ID |
| sk | String | 판매할 국가 코드, https://www.notion.so/Z-5-Appendix-Country-Code-993bff14a0604802a364be87cde9b1ea 참고 |
| currency | String | 상품 가격의 통화 단위 |
| discount | String | 할인율 또는 할인 가격 |
| originalprice | String | 상품/서비스의 기본 가격 |
| price | String | 상품/서비스의 제공 가격 |
| productname | String | 상품/서비스의 이름 |
| description | Object | 상품/서비스의 상세 내용 |
| terms | String | 이용 약관 |
| link | Object | 관련 상세 정보 링크 |
| workflow | Object Array | 주문에 대한 Process |
|   status | String | Status Id |
|   statusName | String | Status Title |
|   statusType | String | Status Type ( NEW / INPROGRESS / CLOSED ) |
| created | Object | 상품의 생성일 |