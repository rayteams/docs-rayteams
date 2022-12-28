---
title: "4.3 Project"
weight: 3
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.3.1 Get Project

### Summary

Project information is divided.This is an API that can be delivered at once.

In other words, we collect individual information and return them at once.

| API | Description | Link |
| --- | --- | --- |
| /project/{_id}/info | Show the basic information. | [Project Data Types](/docs/platformapi-appendix/custom-data-type/#project)  |
| /project/{_id}/memo | Show the list list. |  |
| /project/{_id}/attachments | Show the list of attachments. |  |
| /project/{_id}/histories | It shows a change history. |  |
| /project/{_id}/orders | Show Orders. |  |
| /project/{_id}/groups | Show the associated group information.  |  |

See the [Project](/docs/platformapi-appendix/custom-data-type/#project) for the custom data type of the above Project

### Resource Information

```
GET /project/{_id}
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {...},
    {...},
    {...},
    {...},
    {...},
    {...},
    {...}
  ]
}
```

The following five information is stored in the Object Array form.

See 4.3.2 ~ 4.3.6 below

## 4.3.2 Get project information

### Summary

Get only basic information of Project.

### Resource Information

```
GET /project/{_id}/info
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "_id": "fb3ac626-181e-4387-a9c3-c263e4e57c4e",
    "sk": "project",
    "region": "ap-northeast-2",
    "name": "project-1110201",
    "patientId": "patient-110202",
    "projecttype": "DENTALAVATAR",
    "count": 15,
    "size": 39449461,
    "ownerGroupId": "62d901cdcf70d0a2cf6c5d6e",
    "labId": "62dfdb179a4e3409ba649869",
    "lastUpdateGroupId": "62d901cdcf70d0a2cf6c5d6e",
    "status": {
      "code": "custom",
      "text": "Request Confirm"
    },
    "subject": {
      "name" : "Tester",
      "birth" : "1978-12-28"
    },
    "istrash": true,
    "isarchive": false,
    "created": 1661924655726,
    "updated": 1669373726576
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| sk | String | Fixed with “Project”, the type of information |
| region | String | Region information of the project |
| name | Number | Project name(Alias) |
| patientId | String | Project Patient ID |
| projecttype | String | Project type |
| size | Number | Total size of the project |
| count | Boolean | Number of files in the project |
| ownerGroupId | String | The group ID of the user who created the project |
| labId | String | Group ID shared with the project |
| lastUpdateGroupId | String | Finally, the group ID with the project updated |
| status | Object | Project의 Status |
|   code | String | To change, fixed with “Custom” |
|   text | String | Status Title |
| subject | Object | Project Subject(Title) |
|   name | String | Project patient name |
|   birth | String | Project patient birthday |
| istrash | String | Deletion of the project (Trash) |
| isarchive | Boolean | Whether Archive |
| created | Number | The date and time the project was created |
| updated | Number | Project's recent update time |

## 4.3.3 Get project memo

### Summary

Get the Memo information of Project.

### Resource Information

```
GET /project/{_id}/memo
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "_id": "f83ce273-f078-4454-8c34-a0cecb903e4e",
      "sk": "memo:1667454117029",
      "comments": [
        {
          "content": "<p>Test Reply</p>\n",
          "created": 1667454126923,
          "groupId": "62dfdb179a4e3409ba649869"
        }
      ],
      "content": "<p>Test Message</p>\n",
      "created": 1667454117029,
      "groupId": "62dfdb179a4e3409ba649869"
    },
    {
      "_id": "f83ce273-f078-4454-8c34-a0cecb903e4e",
      "sk": "memo:1667459525960",
      "comments": [],
      "content": "<p>First Message</p>\n",
      "created": 1667459525960,
      "groupId": "62dfdb179a4e3409ba649869"
    }
	]
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| sk | String | “memo:TIMESTAMP”, 정보의 Type = memo:~ |
| comments | Object Array | Only 1-depth support |
| isarchive | Boolean | Archive storage |
| created | String | Memo creation |
| groupId | String | Created user group ID |

**Comment Object Structures**

| Field | Type | Description |
| --- | --- | --- |
| contents | String | HTML format |
| created | String | Memo creation |
| groupId | String | Created user group ID |

## 4.3.4 Get project attachments

### Summary

Import the attached files attached to the Project.

### Resource Information

```
GET /project/{_id}/attachments
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "attachments:1669272938428",
      "filetype": "image/png",
      "name": "file0.png",
      "size": 53899,
      "created": 1669272938428
    },
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "attachments:1669272934228",
      "filetype": "image/png",
      "name": "file1.png",
      "size": 153899,
      "created": 1669272932128
    }
  ]
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| sk | String | “attachments:~”, 정보의 Type = attachments:~ |
| filetype | String | Attached file type |
| name | String | Attached file name |
| size | Number | Size of attached files(Byte) |
| created | Number | When the date of creation of the attachment |

## 4.3.5 Get project histories

### Summary

It delivers the change history of the Project.

### Resource Information

```
GET /project/{_id}/histories
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "his:1669272896105",
      "data": {
        "content": "<p>test pos</p>\n",
        "type": "create"
      },
      "updateType": "RAY_LINK_PROJECT_ADDMEMO",
      "created": 1669272896105
    },
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "his:1669272914390",
      "data": {
        "sk": "memo:1669272894365",
        "data": {
          "content": "<p>test comment</p>\n"
        }
      },
      "updateType": "RAY_LINK_PROJECT_ADDCOMMENT",
      "created": 1669272914390
    }
  ]
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | 프로젝트의 고유 ID |
| sk | String | “his:~”, 정보의 Type = his:~ |
| data | Object | 변경을 유발한 Request의 Body |
| updateType | String | HIstory Types |
| created | Number | 이력 생성 시각 |

## 4.3.6 Get project orders

### Summary

Deliver the ORDER information generated in Project.

Please refer to the document for the object information of individual orders.

### Resource Information

```
GET /project/{_id}/orders
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "order:1669345121504",
      ...
    },
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "order:1669718221504",
      ...
    }
  ]
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| sk | String | “order:~”, 정보의 Type = order:~ |

Please refer to the document for the Order Fields information.

## 4.3.7 Get project groups

### Summary

Deliver group information related to Project.

By default, the Project is created by Owner Group and Shared Group.

For owner group, the value of `sk` is fixed to `project:institute:owner`.

Otherwise, it is stored in the form of `Project:institute:timestamp`. The group information shown in this way is shared group information.

### Resource Information

```
GET /project/{_id}/groups
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project unique ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "project:institute:owner",
      "group_id": "62dfdb179a4e3409ba649869",
      "name": "KO-0005",
      "patientId": "NEW-0003"
    },
    {
      "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
      "sk": "project:institute:1669263126159",
      "group_id": "fd6ede0f-8bce-4316-a54c-38ae893964a3",
      "name": "KO-0005",
      "patientId": "NEW-0003"
    }
  ]
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| sk | String | “project:institute:~”, Information Type = project:institute:~ |
| group_id | String | Group's unique ID |
| name | String | Project name |
| patientId | String | Project Patient ID |

## 4.3.8 Get projects

### Summary

Returns all projects in the group that login users belong to.

At this time, the Project Object is delivered only the Custom Data Type `project`.

### Resource Information

```
GET /project
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| _id | String |  |  |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [
    { ... },
    { ... }
  ]
}
```

[4.3.2 Get project information](/docs/platformapi-resources/project/#432-get-project-information) Information is listed.

## 4.3.9 Add attachment

### Summary

You can register an attachment to a specific project.

### Resource Information

```
POST /project/{_id}/attachment/add
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Content-Type | multipart/form-data |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |

### Request Body Structure

**form data**

| Name | Type | Description |
| --- | --- | --- |
| file | FILE | File Object |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": { ... }
}
```

[Object Array 형태로 저장됩니다.](/docs/platformapi-appendix/custom-data-type/#project) Response information is listed.

## 4.3.10 Get download attachment link

### Summary

Deliver a temporary link that can download a specific attachment file.

### Resource Information

```
GET /project/{_id}/attachment/download/{_attachmentId}
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | PROJECT |
| Content-Type | multipart/form-data |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| _attachmentId | String | attachment sk value(예시 : attachments:1669272938428) |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": {
    "_id": "334c972a-5756-45f7-8eb1-f3f84bedd525",
    "sk": "attachments:1669272938428",
    "filetype": "image/png",
    "name": "file0.png",
    "size": 53899,
    "created": 1669272938428,
    "downloadLink" : "https://~~~"
  }
}
```

Only temporary download links are provided for security reasons. `downloadLink` item is added to the individual Attachment Object.
You can download the data by direct accessing with the download link.

Download Link is only valid for 30 minutes.