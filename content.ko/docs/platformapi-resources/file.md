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

Project를 구성하는 File을 가져옵니다. 모든 데이터를 전달하지는 않습니다.

다운로드 받을 수 있는 데이터는 `face`, `maxilla`, `mandible` 만 가능합니다. 다운로드 받을 type을 지정하지 않으면, 모든 다운로드 받을 수 있는 링크가 전달됩니다.

Project file types에 대해서는 [Z.7 Appendix - Project file types](https://www.notion.so/Z-7-Appendix-Project-file-types-33fd7fe8e45e456eb8e14524671a6d85) 문서를 참고해주시기 바랍니다.

Project의 Attachment와는 다릅니다. Attachment와 File에 대해서는 [Z.4 Appendix - Project Files & Attachments](https://www.notion.so/Z-4-Appendix-Project-Files-Attachments-bb226ac2c6b24978923d0a9b67eeab09) 문서를 참고해주시기 바랍니다.

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
			"files" : [{
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
				},
			]
		}
	}
}
```

| Field | Type | Description |
| --- | --- | --- |
| _id | String | 프로젝트의 고유 ID |
| files | File Object Array | 요청한 파일 목록 |
|   filetype | String | File의 Types - https://www.notion.so/Z-7-Appendix-Project-file-types-33fd7fe8e45e456eb8e14524671a6d85  |
|   downloadLink | String | 다운로드 받을 수 있는 링크 |
|   downloadExpired | String | downloadLink 의 유효기간 |
|   name | String | 파일 이름 |
|   size | Number | 파일의 크기 |

fail (not exist)

```
{
  "status": "success",
	"data" : {}
}
```