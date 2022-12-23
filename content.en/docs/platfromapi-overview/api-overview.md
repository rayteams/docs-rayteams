---
title: "2. API Overview"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
## URL Schema

### Summary

RAYTeams에서 제공하는 모든 API는 formatting되어 있습니다.

요청하는 API는 모두 소문자로 표기되며, GET으로 요청하는 Parameter의 경우에는 모두 `urlencoding` 되어야 합니다.

**Format**

```
https://api-[REGION]-[SCOPE].rayteams[SANDBOX].com/v[VERSION]/
```

### 항목 정보

- REGION : RAYTeams Region 정보에 대해서는 [Z.1 Appendix - Region](/docs/platformapi-appendix/region/)   문서에서 확인할
- SCOPE : Scope는 [Z.3 Appendix - Scope](/docs/platformapi-appendix/scope/)  에 정의 되어 있습니다.
- SANDBOX
    - Sandbox 정보는 허가된 업체에서 API를 토대로 개발 또는 검증하기 위해 제공되는 독립적인/격리된 API 환경을 제공할때 사용되는 Key입니다.
    - Sandbox 관련해서는 Sandbox 환경에 대한 [Z.9 Appendix - Sandbox](/docs/platformapi-appendix/sandbox/)  문서를 참고해주시기 바랍니다.

Example

```
https://api-ap-northeast-2-project.rayteams.com/v1.0/
```

## Version Information

### Verion 정보

모든 API는 URL에 위와 같이 Version 정보가 표시됩니다.

Version 표기는 앞에 `v` 라는 Version을 나타낸다는 Prefix와 함께 크게 3개의 octet으로 표기됩니다.

Example

```
v1.0
```

Deprecate API도 특별한 Issue가 없는한, 이용이 가능합니다.

Deprecate API에 대해서는 [Deprecate API]  문서를 참고해주시기 바랍니다.

## Error Handling

### Summary

RAYTeams Open API services는 모든 Request에 대하여 표준 HTTP status response codes를 사용합니다.

크게 분류하면 아래와 같이 3가지로 구분됩니다.

- 200 : 요청에 대한 처리 정상임
- 4XX : 사용자 인증 정보의 문제로 인하여 요청에 대해 처리할 수 없음
- 5XX : 요청에 대한 처리 도중에 문제가 발생함

각 Status Codes에 대한 정보는 아래와 같습니다.

| Status code | Description |
| --- | --- |
| 200 | 요청에 대해서 정상적으로 처리함 |
| 401 | 인증 정보가 올바르지 않음 |
| 403 | 정상적인 요청이 아니어서 접근을 거부 |
| 404 | 요청하는 주소가 존재하지 않음 |
| 429 | 너무 많은 요청으로 인하여 요청을 거부함 |
| 500 | 서버에서 요청을 처리하다가 오류가 발생 |

### Custom Error

Response status code가 200이라고 해서 요청에 대한 처리가 원하는 결과를 전달해주지는 않습니다.

각 Resources 마다 처리마다 요청에 대한 Validation을 진행하게 됩니다. 이때 Invalid Request에 대해서는 Custom Error를 발생하게 됩니다.

즉, Response status code 는 200이지만 요청에 대한 처리 도중에 발생하는 Custom Error를 전달 할 수 있습니다.

### Error Response Schema

Error Response는 크게 2가지 형태로 전달됩니다.

**Normal Error**

```
{
  "message" : "Unauthorized"
}
```

**Custom Error**

```
{
  "errorCode" : "NO_ITEM"
}
```

<aside>
💡 Custom Error는 대부분 간단히 표현됩니다. 개별적인 Custom Error는 개별 API Resourse에서 확인할 수 있습니다.
</aside>