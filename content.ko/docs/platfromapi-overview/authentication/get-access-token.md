---
title: "3.2 Get Access Token"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## **Summary**

Authorized Code를 통해서 Access Token을 획득하는 방법을 기술합니다.

Authorized Code에 대해서는 [1. Get Authorized Code](https://www.notion.so/1-Get-Authorized-Code-6c5ada2937204dc291c44f51076dbf7d) 문서를 참고해주시기 바랍니다.

## Token 정보

- Access Token은 발급 시점으로부터 1일동안 유효합니다.
- Refresh Token은 1년간 유효합니다.
- Access Token은 발급 Region별로 격리되어 있습니다.
즉, `ap-northeast-2` region에서 발급 받은 Token은 동일 Region에서만 유효합니다.

## Access Token 발급

아래와 같이 `/oauth2/token` Endpoint를 POST로 요청합니다.

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token
```

### **Request Header**

**Authorization**

클라이언트에 암호가 발급된 경우 클라이언트는 권한 부여 헤더에서 `client_secret_basic` HTTP 권한 부여로 해당 `client_id` 및 `client_secret`을 전달할 수 있습니다. 

`client_id` 와 `client_secret`의 값을 : 으로 Join하고 이 전체 String 을 Base64Ecode 한 값을 사용합니다.

```
Authorization: Basic ZGpjOTh1M2ppZWRtaTI4M2V1OTI4OmFiY2RlZjAxMjM0NTY3ODkw
```

**Content-Type**

항상 `'application/x-www-form-urlencoded'`여야 합니다.

### **Request Body**

*grant_type*

 값은 `authorization_code` 으로 고정하여 사용합니다.

*client_id*

제공되는 Client Id를 사용합니다.

*client_secret*

제공되는 Client Secret 값을 사용합니다.

*redirect_uri*

`/oauth2/authorize`에서 `authorization_code`를 얻기 위해 사용했던 `redirect_uri`와 같아야 합니다.
`grant_type`이 `authorization_code`인 경우에만 필수입니다.

*refresh_token*

사용자 세션에 대한 새 액세스 및 ID 토큰을 생성하려면 `/oauth2/token` 요청의 `refresh_token` 파라미터 값을 동일한 앱 클라이언트에서 이전에 발행된 새로 고침 토큰으로 설정하세요.

*code*

`grant_type`이 `authorization_code`인 경우 필수입니다.

*code_verifier*

증명 키입니다.
`grant_type`이 `authorization_code`이며 PKCE를 통해 권한 부여 코드가 요청된 경우 필수입니다.

### Authorized Code로 Access Token 교환

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token&
                       Content-Type='application/x-www-form-urlencoded'&
                       Authorization=Basic aSdxd892iujendek328uedj
                       
                       grant_type=authorization_code&
                       client_id=djc98u3jiedmi283eu928&
                       code=AUTHORIZATION_CODE&
                       redirect_uri=com.myclientapp://myclient/redirect
```

### Refresh Token으로 Access Token 교환

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token >
                           Content-Type='application/x-www-form-urlencoded'&
                           Authorization=Basic aSdxd892iujendek328uedj
                           
                           grant_type=refresh_token&
                           client_id=djc98u3jiedmi283eu928&
                           refresh_token=REFRESH_TOKEN
```

### Response Body

**성공시의 결과**

```
{ 
  "access_token":"eyJz9sdfsdfsdfsd", 
  "id_token":"dmcxd329ujdmkemkd349r",
  "token_type":"Bearer", 
  "expires_in":3600
 }
```

**실패시의 결과**

```
{
	"error":"invalid_request|invalid_client|invalid_grant|unauthorized_client|unsupported_grant_type|"
}
```