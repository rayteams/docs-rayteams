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

Deliver the current logged -in user information.

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
| region | String | Region with a user's group - [Z.1 Region](/docs/platformapi-appendix/region/) |
| type | String | 사용자의 Type(user, manager) |
| sub | String | _id value |
| groupId | String | Group ID |
| name | String | User's name |
| email | String | User email address |
| _id | String | User's unique ID |
| lastlogged | Number | Last login time |
| sk | String | Fix the value with “info” |
| valid | Boolean | Whether user information is valid or not |

## 4.1.2 Get user information by email

### Summary

Deliver information from a specific user using the email address.

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
| region | String | Group activity of group that users belong to |
| type | String | User Type(user, manager) |
| sub | String | _id value |
| groupId | String | Group ID |
| name | String | User name |
| email | String | User Email Address |
| _id | String | User's unique ID |
| lastlogged | Number | Last login time |
| sk | String | Fix the value with “info” |
| valid | Boolean | Whether user information is valid or not |

**Fail**

```
{
  "status": "success",
  "data": {
    "exist": false
  }
}
```