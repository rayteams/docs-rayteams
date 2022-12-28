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

The login user delivers the information of the group.

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
| _id | String | Group's unique ID |
| countryCode | String | Country code - [Z.5 Country Code](/docs/platformapi-appendix/country-code/) 참고 |
| region | String | Group's Region - [Z.1 Region](/docs/platformapi-appendix/region/) 참고 |
| name | String | Group name |
| address | String | Group address |
| grouptype | Array | Group's Type |
| hasMember | Boolean | Whether the user exists in the group |
| tel | String | Phone number |
| coords | Array | Latitude/hardness information |
| relatedGroups | Array | Group of Contract |
| extra | Array | Add additional information |
| sk | String | Fix the value with “INFO” |
| created | Number | User's Type (user, manager) |
| updated | Number | User's unique ID |

## 4.2.2 Get group information

### Summary

Deliver information about specific groups.

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
| _id | String | Group's unique ID |

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
| _id | String | Group's unique ID |
| countryCode | String | Country code - [Z.5 Country Code](/docs/platformapi-appendix/country-code/) 참고 |
| region | String | Group's Region - [Z.1 Region](/docs/platformapi-appendix/region/) 참고 |
| name | String | Group name |
| address | String | Group address |
| grouptype | Array | Group Type |
| hasMember | Boolean | Whether the user exists in the group |
| tel | String | phone number |
| coords | Array | Latitude/hardness information |
| relatedGroups | Array | Group of Contract |
| extra | Array | Add additional information |
| sk | String | Fix the value with “INFO” |
| created | Number | User Type(user, manager) |
| updated | Number | User's unique ID |

**Fail** (Not exist)

```
{
  "status": "success"
}
```

## 4.2.3 Get groups by country code

### Summary

Bring a list of groups in a particular country.

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
| countryCode | String | Region of Group |

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

**Fail** (Not exist)

```
{
  "status": "success",
  "data": []
}
```

## 4.2.4 Search group(s)

### Summary

It delivers the result of searching the group in the group name.

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
| name | String | Group name |
| allowEmptyMember | Boolean | (Optional) Whether the user exists in the group |

LIKE searches 'name' of Group as a value of 'name'.

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
**Fail** (Not exist)

```
{
  "status": "success",
  "data": []
}
```