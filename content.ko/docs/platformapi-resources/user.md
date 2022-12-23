---
title: "4.1 User"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.1.1 Get my information

### Summary

현재 로그인된 사용자의 정보를 전달합니다.

### Resource Information

```
GET /me
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

### Response Body Structure

```
{
  "status": "success",
  "data": {
    "region": "ap-northeast-2",
    "type": "manager",
    "sub": "ca640dca-d2b2-4631-a2e9-965dc789e70c",
    "groupId": "deb9c7fd-b3df-4f03-b851-5f212d25353c",
    "name": "USERNAME",
    "email": "aaa@bbb.com",
    "_id": "ca640dca-d2b2-4631-a2e9-965dc789e70c",
    "lastlogged": 1670232646500,
    "sk": "info",
    "valid": true
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| region | String | 사용자의 Group이 소속된 Region - https://www.notion.so/Z-1-Appendix-Region-ca1f16cea87e466a89833656be63e180 참고 |
| type | String | 사용자의 Type(user, manager) |
| sub | String | _id 값과 동일 |
| groupId | String | 사용자가 소속된 Group ID |
| name | String | 사용자의 이름 |
| email | String | 사용자의 Email Address |
| _id | String | 사용자의 고유 ID |
| lastlogged | Number | 마지막 로그인 시각 |
| sk | String | “info” 로 값 고정 |
| valid | Boolean | 사용자 정보가 Valid 인지 아닌지의 여부 |

## 4.1.2 Get user information by email

### Summary

Email 주소를 사용하는 특정 사용자의 정보를 전달합니다.

### Resource Information

```
POST /getuserbyemail
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

### Request Body Structure

```
{
  "email": "aaa@bbb.com"
}
```

### Response Body Structure

**Success**

```
{
  "status": "success",
  "data": {
    "region": "ap-northeast-2",
    "type": "manager",
    "sub": "ca640dca-d2b2-4631-a2e9-965dc789e70c",
    "groupId": "deb9c7fd-b3df-4f03-b851-5f212d25353c",
    "name": "USERNAME",
    "email": "aaa@bbb.com",
    "_id": "ca640dca-d2b2-4631-a2e9-965dc789e70c",
    "lastlogged": 1670232646500,
    "sk": "info",
    "valid": true
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| region | String | 사용자가 소속된 Group의 활동 Region |
| type | String | 사용자의 Type(user, manager) |
| sub | String | _id 값과 동일 |
| groupId | String | 사용자가 소속된 Group ID |
| name | String | 사용자의 이름 |
| email | String | 사용자의 Email Address |
| _id | String | 사용자의 고유 ID |
| lastlogged | Number | 마지막 로그인 시각 |
| sk | String | “info” 로 값 고정 |
| valid | Boolean | 사용자 정보가 Valid 인지 아닌지의 여부 |

**Fail**

```
{
  "status": "success",
  "data": {
    "exist": false
  }
}
```