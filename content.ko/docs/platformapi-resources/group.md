---
title: "4.2 Group"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.2.1 Get my group information

### Summary

로그인된 사용자가 소속된 Group의 정보를 전달합니다.

### Resource Information

```
GET /mygroup
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

*None*

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "countryCode": "KR",
    "created": 1661256104649,
    "address": "서울시 광진구 자양동 자양로 15길",
    "grouptype": [],
    "name": "구의 치과",
    "hasMember": true,
    "updated": 1664328222035,
    "_id": "62dfdb179a4e3409ba649869",
    "tel": "",
    "coords": [
      127.0802384,
      37.5349614
    ],
    "sk": "info",
    "region": "ap-northeast-2",
    "relatedGroups": [],
    "extra": []
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Group의 고유 ID |
| countryCode | String | 국가 코드 - https://www.notion.so/Z-6-Appendix-Deprecate-APIs-7f616a941fd34246885715264c9ac852 참고 |
| region | String | Group의 Region - https://www.notion.so/Z-1-Appendix-Region-ca1f16cea87e466a89833656be63e180 참고 |
| name | String | Group의 이름 |
| address | String | Group의 주소 |
| grouptype | Array | Group의 Type |
| hasMember | Boolean | Group에 사용자가 존재하는지의 여부 |
| tel | String | 전화 번호 |
| coords | Array | 위도/경도 정보 |
| relatedGroups | Array | Contract 관계의 Group |
| extra | Array | Group의 추가 정보들 |
| sk | String | “info” 로 값 고정 |
| created | Number | 사용자의 Type(user, manager) |
| updated | Number | 사용자의 고유 ID |

## 4.2.2 Get group information

### Summary

특정 Group에 대한 정보를 전달합니다.

### Resource Information

```
GET /group/{_id}
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
| _id | String | Group의 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "countryCode": "KR",
    "created": 1661256104649,
    "address": "서울시 광진구 자양동 자양로 15길",
    "grouptype": [],
    "name": "구의 치과",
    "hasMember": true,
    "updated": 1664328222035,
    "_id": "62dfdb179a4e3409ba649869",
    "tel": "",
    "coords": [
      127.0802384,
      37.5349614
    ],
    "sk": "info",
    "region": "ap-northeast-2",
    "relatedGroups": [],
    "extra": []
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Group의 고유 ID |
| countryCode | String | 국가 코드 - https://www.notion.so/Z-6-Appendix-Deprecate-APIs-7f616a941fd34246885715264c9ac852 참고 |
| region | String | Group의 Region - https://www.notion.so/Z-1-Appendix-Region-ca1f16cea87e466a89833656be63e180 참고 |
| name | String | Group의 이름 |
| address | String | Group의 주소 |
| grouptype | Array | Group의 Type |
| hasMember | Boolean | Group에 사용자가 존재하는지의 여부 |
| tel | String | 전화 번호 |
| coords | Array | 위도/경도 정보 |
| relatedGroups | Array | Contract 관계의 Group |
| extra | Array | Group의 추가 정보들 |
| sk | String | “info” 로 값 고정 |
| created | Number | 사용자의 Type(user, manager) |
| updated | Number | 사용자의 고유 ID |

**Fail** (Not exist)

```
{
  "status": "success"
}
```

## 4.2.3 Get groups by country code

### Summary

특정 국가에 존재하는 그룹 목록을 가져옵니다.

### Resource Information

```
POST /groupbycountrycode
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | USER |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

*None*

### Request Body Structure

```
{
  "data": {
    "countryCode": "KR"
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| countryCode | String | 사용자가 소속된 Group의 활동 Region |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
	    "countryCode": "KR",
	    "created": 1661256104649,
	    "address": "서울시 광진구 자양동 자양로 15길",
	    "grouptype": [],
	    "name": "구의 치과",
	    "hasMember": true,
	    "updated": 1664328222035,
	    "_id": "4b6f3137-87ce-443c-b9e6-bd6a4009c928",
	    "tel": "",
	    "coords": [
	      127.0802384,
	      37.5349614
	    ],
	    "sk": "info",
	    "region": "ap-northeast-2",
	    "relatedGroups": [],
	    "extra": []
		},
		{
	    "countryCode": "KR",
	    "created": 1661154130280,
      "address": "서울시 광진구 자양동 자양로 13가길 8 303",
	    "grouptype": [],
      "name": "테스트 치과",
	    "hasMember": true,
	    "updated": 1661154130280,
	    "_id": "fd6ede0f-8bce-4316-a54c-38ae893964a3",
	    "tel": "",
	    "coords": [
        127.0814971,
        37.5346789
	    ],
	    "sk": "info",
	    "region": "ap-northeast-2",
	    "relatedGroups": [],
	    "extra": []
		}
  }
}
```

<aside>
💡 [](https://www.notion.so/4929db1e0121472a8cef6f737662c560) 의 Response 정보가 Array로 나열됨

</aside>

**Fail** (Not exist)

```
{
  "status": "success",
  "data": []
}
```

## 4.2.4 Search group(s)

### Summary

그룹 이름으로 그룹을 검색한 결과를 전달합니다.

### Resource Information

```
POST /groupbyname
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
    "name": "test",
    "allowEmptyMember": true
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| name | String | Group의 이름 |
| allowEmptyMember | Boolean | (Optional) Group에 사용자가 존재하는지의 여부 |

<aside>
💡 `name` 의 값으로 group의 `name`을 like 검색합니다.

</aside>

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "countryCode": "KR",
      "created": 1661151334960,
      "address": "경기 성남시 분당구 판교로 332 ECO Hub 3층 SK D&D",
      "grouptype": [],
      "name": "test group",
      "hasMember": true,
      "zipcode": "1231232",
      "updated": 1661428030071,
      "tel": "",
      "_id": "7481e933-c42e-4684-a982-92239d414f00",
      "coords": [
        127.1103627,
        37.4026874
      ],
	    "sk": "info",
	    "region": "ap-northeast-2",
	    "relatedGroups": [],
	    "extra": []
		},
    {
      "countryCode": "KR",
      "created": 1662340572380,
      "address": "동대문운동장역",
      "grouptype": [],
      "name": "test002020",
      "hasMember": true,
      "zipcode": "323232",
      "updated": 1662340575743,
      "tel": "",
      "_id": "8cb843e0-24a9-4db7-95f8-df340f48fe94",
      "coords": [
        127.008953,
        37.565682
      ],
	    "sk": "info",
	    "region": "ap-northeast-2",
	    "relatedGroups": [],
	    "extra": []
		}
  }
}
```

<aside>
💡 [](https://www.notion.so/4929db1e0121472a8cef6f737662c560) 의 Response 정보가 Array로 나열됨

</aside>

**Fail** (Not exist)

```
{
  "status": "success",
  "data": []
}
```