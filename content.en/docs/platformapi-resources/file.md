---
title: "4.4 File"
weight: 4
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 4.4.1 Get project file

### Summary

Import the file that constitutes the Project.It does not deliver all data.

Only data that can be downloaded can only be 'FACE', 'Maxilla' and 'Mandible'. If you do not specify the type to download, you will receive a link that you can download.

Please refer to the [Z.6 Appendix - Project file types](/docs/platformapi-appendix/project-file-types/) document for Project File Typs.

It is different from the Attachment of Project.Please refer to [Z.4 Appendix - Files & Attachments](/docs/platformapi-appendix/project-files-and-attachements/) documentation for Attachment and File.

### Resource Information

```
GET /file/{_projectId}/{:_type}
```

| Authentication | required |
| --- | --- |
| Required OAuth Scopes | FILE |
| Data Format | JSON |

### Request Headers

| Name | Type | Constraints | Description |
| --- | --- | --- | --- |
| Authorization | String | Must not be null. |  |
| x-rayteams-client-id | String |  |  |

### Request URI Paramters

| Name | Type | Description |
| --- | --- | --- |
| _projectId | String | Project의 고유한 ID |
| _type | String | Optional, maxilla / mandible / face |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data" : {
    "_id" : "930449b1-76b4-479e-b1a7-a57e65d9d172",
    "files" : [
      {
        "filetype" : "mandible",
        "downloadLink" : "https://~",
        "downloadExpired" : 1669263126100,
        "name" : "mandible.obj",
        "size" : 25129108
      },{
        "filetype" : "face",
        "downloadLink" : "https://~",
        "downloadExpired" : 1669263332159,
        "name" : "face.obj",
        "size" : 29108
      }
    ]
  }
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | Project's unique ID |
| files | File Object Array | Required file list |
|   filetype | String | Type of files - [Project file types](/docs/platformapi-appendix/project-file-types/)  |
|   downloadLink | String | Link that can be downloaded |
|   downloadExpired | String | Downloadlink's validity period |
|   name | String | File name |
|   size | Number | File size |

fail (not exist)

```
{
  "status": "success",
  "data" : {}
}
```