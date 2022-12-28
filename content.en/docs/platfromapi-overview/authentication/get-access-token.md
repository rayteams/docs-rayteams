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

Describes how to acquire Access Token through Authorized Code.

Please refer to the [1. Get Authorized Code](/docs/platfromapi-overview/authentication/get-authorized-code/) document for the Authorized Code.

## Token Information

- Access token is valid for one day from the time of issuance.
- Refresh token is valid for one year.
- Access token is isolated by Region.
In other words, the token issued in the `ap-northeast-2` Region is only valid in the same region.

## Access token issuance

As shown below, request `/oauth2/token` endpoint as a POST.

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token
```

### **Request Header**

**Authorization**

If a password is issued to the client, the client can deliver the `client_id` and `client_secret` by granting `client_secret_basic` http authority in the authorized header.

JOIN with the value of `client_id` and `client_secret` uses the value of this entire string.

```
Authorization: Basic ZGpjOTh1M2ppZWRtaTI4M2V1OTI4OmFiY2RlZjAxMjM0NTY3ODkw
```

**Content-Type**

You must always be `application/X-WWW-Form-Urlencoded`.

### **Request Body**

*grant_type*

The value is fixed to `authorization_code`.

*client_id*

Use the provided Client ID.

*client_secret*

Use the provided Client Secret value.

*redirect_uri*

It should be the same as `redirect_uri` used to obtain `authorization_code` in `/oauth2/authorize`.
It is only necessary if `grant_type` is `authorization_code`.

*refresh_token*

To create new access and ID tokens for user sessions, set the `refresh_token` parameter value of `/oauth2/token` request as a refresh token issued earlier in the same app client.

*code*

If `grant_type` is `authorization_code`, it is essential.

*code_verifier*

`grant_Type` is `authorization_code` and is required if the authorization code is requested through PKCE.

### Access token exchange with Authorized Code

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token&
                       Content-Type='application/x-www-form-urlencoded'&
                       Authorization=Basic aSdxd892iujendek328uedj
                       
                       grant_type=authorization_code&
                       client_id=djc98u3jiedmi283eu928&
                       code=AUTHORIZATION_CODE&
                       redirect_uri=com.myclientapp://myclient/redirect
```

### Access token exchange with Refresh token

```
POST https://oauth-ap-northeast-2-development.rayteams.com/oauth2/token >
                           Content-Type='application/x-www-form-urlencoded'&
                           Authorization=Basic aSdxd892iujendek328uedj
                           
                           grant_type=refresh_token&
                           client_id=djc98u3jiedmi283eu928&
                           refresh_token=REFRESH_TOKEN
```

### Response Body

**The result of success**

```
{ 
  "access_token":"eyJz9sdfsdfsdfsd", 
  "id_token":"dmcxd329ujdmkemkd349r",
  "token_type":"Bearer", 
  "expires_in":3600
}
```

**The result of failure**

```
{
  "error":"invalid_request|invalid_client|invalid_grant|unauthorized_client|unsupported_grant_type|"
}
```