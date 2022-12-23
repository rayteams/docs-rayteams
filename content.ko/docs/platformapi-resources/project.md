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

Project의 정보는 나누어져 있습니다. 이를 한번에 모두 전달 받을 수 있는 API 입니다.

즉, 개별 정보들을 모아서 한번에 리턴합니다.

| API | Description | Link |
| --- | --- | --- |
| /project/{_id}/info | 기본 정보를 보여줍니다. | https://www.notion.so/5-Object-Array-8e9fb2c6afa74245b1b20a6d99d382a6  |
| /project/{_id}/memo | Comment 목록 보여줍니다. |  |
| /project/{_id}/attachments | 첨부 파일 목록을 보여줍니다. |  |
| /project/{_id}/histories | 변경 이력을 보여줍니다. |  |
| /project/{_id}/orders | Orders를 보여줍니다. |  |
| /project/{_id}/groups | 연관된 Group 정보를 보여줍니다.  |  |

위의 Project의 Custom Data Type에 대해서는 [Project](https://www.notion.so/Project-3be717595dfb4f44ba226f79a06fcc53) 뮨서를 참고

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
| _id | String | 프로젝트의 고유 ID |

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

아래의 5가지 정보들이 Object Array 형태로 저장됩니다.

아래 4.3.2 ~ 4.3.6 참고

## 4.3.2 Get project information

### Summary

Project의 기본정보만을 가져옵니다.

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
| _id | String | Project 고유 ID |

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
| _id | String | 프로젝트의 고유 ID |
| sk | String | “project”로 고정, 정보의 Type |
| region | String | 프로젝트의 Region 정보 |
| name | Number | 프로젝트의 이름(Alias) |
| patientId | String | 프로젝트의 Patient ID |
| projecttype | String | 프로젝트의 타입 |
| size | Number | 프로젝트의 총 크기 |
| count | Boolean | 프로젝트내의 파일 개순 |
| ownerGroupId | String | 프로젝트를 생성한 사용자의 Group ID |
| labId | String | 프로젝트를 공유 받은 Group ID |
| lastUpdateGroupId | String | 마지막으로 프로젝트를 업데이트한 Group ID |
| status | Object | Project의 Status |
|   code | String | 변경하려면 “custom”으로 고정 |
|   text | String | Status Title |
| subject | Object | Project의 Subject(Title) |
|   name | String | Project의 대상 이름 |
|   birth | String | Project의 대상 생년월일 |
| istrash | String | 프로젝트의 삭제 여부(휴지통) |
| isarchive | Boolean | Archive 여부 |
| created | Number | 프로젝트가 생성된 일시 |
| updated | Number | 프로젝트의 최근 업데이트 시각 |

## 4.3.3 Get project memo

### Summary

Project의 Memo 정보들을 가져옵니다. 

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
| _id | String | Project 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [{
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
| _id | String | 프로젝트의 고유 ID |
| sk | String | “memo:TIMESTAMP”, 정보의 Type = memo:~ |
| comments | Object Array | 1-depth 만 지원, https://www.notion.so/Comment-Object-Structures-1773436d78864ffbbb8dbaec623ecd59 참고 |
| isarchive | Boolean | 아카이브 보관 여부 |
| created | String | Memo 작성 기각 |
| groupId | String | 작성한 사용자의 Group ID |

**Comment Object Structures**

| Field | Type | Description |
| --- | --- | --- |
| contents | String | HTML format |
| created | String | Comment 작성 기각 |
| groupId | String | 작성한 사용자의 Group ID |

## 4.3.4 Get project attachments

### Summary

Project에 첨부된 첨부파일들을 가져옵니다.

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
| _id | String | Project 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [{
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
| _id | String | 프로젝트의 고유 ID |
| sk | String | “attachments:~”, 정보의 Type = attachments:~ |
| filetype | String | 첨부된 file type |
| name | String | 첨부된 파일 이름 |
| size | Number | 첨부된 파일의 크기(Byte) |
| created | Number | 첨부 파일의 생성일시 |

## 4.3.5 Get project histories

### Summary

Project의 변경 이력을 전달합니다.

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
| _id | String | Project 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
  "data": [{
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

Project에서 생성된 Order 정보를 전달합니다.

개별 Order의 Object 정보는 문서를 참고해주시기 바랍니다.

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
| _id | String | Project 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
	"data": [{
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
| _id | String | 프로젝트의 고유 ID |
| sk | String | “order:~”, 정보의 Type = order:~ |

<aside>
❓ Order Fields 정보는 문서를 참고

</aside>

## 4.3.7 Get project groups

### Summary

Project에 관계된 Group 정보를 전달합니다.

기본적으로 Project는 Owner Group과 Shared Group 으로 1개씩 생성됩니다.

Owner Group의 경우, `sk`의 값이 `project:institute:owner` 로 고정됩니다.

그렇지 않은 경우, `project:institute:TIMESTAMP` 형태로 저장됩니다. 이렇게 표시되는 Group 정보는 Shared Group 정보입니다.

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
| _id | String | Project 고유 ID |

### Response Body Structure

**success**

```
{
  "status": "success",
	"data": [{
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
| _id | String | 프로젝트의 고유 ID |
| sk | String | “project:institute:~”, 정보의 Type = project:institute:~ |
| group_id | String | Group의 고유 ID |
| name | String | Project 이름 |
| patientId | String | Project의 Patient ID |

## 4.3.8 Get projects

### Summary

로그인 사용자가 소속된 Group내의 모든 프로젝트를 리턴합니다.

이때 Project Object는 Custom Data Type이 `project` 인 것들만 전달됩니다.

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

<aside>
💡 [4.3.2 Get project information](https://www.notion.so/4-3-2-Get-project-information-87fefb3fb7b14d21a733d6f1b0458a6d) 정보들이 나열됩니다.

</aside>

## 4.3.9 Add attachment

### Summary

특정 Project에 첨부을 등록할 수 있습니다.

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
| _id | String | 프로젝트의 고유 ID |

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

<aside>
💡 [아래의 5가지 정보들이 Object Array 형태로 저장됩니다.](https://www.notion.so/5-Object-Array-8e9fb2c6afa74245b1b20a6d99d382a6) Response 정보가 나열됩니다.

</aside>

## 4.3.10 Get download attachment link

### Summary

특정 첨부파일을 다운로드 받을 수 있는 임시 Link를 전달합니다.

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
| _id | String | 프로젝트의 고유 ID |
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

<aside>
💡 보안상의 이유로 임시 Download Link만 제공합니다.
[Response Body Structure](https://www.notion.so/Response-Body-Structure-9e441ba9273a42d4abbf2142a6d95842) 의 개별 Attachment Object에 `downloadLink` 항목이 추가되어 전달됩니다.

</aside>

전달 받은 Download Link로 Direct Acces하여 데이터를 Download 받을 수 있습니다.

Download Link는 30분동안만 유효합니다.