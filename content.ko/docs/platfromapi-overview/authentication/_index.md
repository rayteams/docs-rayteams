---
title: "3. Authentication"
weight: 3
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Region

RAYTeams OpenAPI Services는 Region 별로 격리되어 서비스를 제공하고 있습니다. Region 정보는 [Z.1 Appendix - Region](https://www.notion.so/Z-1-Appendix-Region-ca1f16cea87e466a89833656be63e180) 문서에서 확인할 수 있습니다.

특정 Region에서 인증된 정보로 다른 Region의 API를 호출하게 되면, 요청을 거부합니다.

## OAuth2.0

### Summary

RAYTeams의 대부분의 요청에는 요청에 대한 인증 처리를 맨 처음 진행합니다.

인증 방식은 ‘표준 OAuth2.0 인증 방식’을 따르고 있습니다. OAuth2.0에 대한 자세한 스펙은 [이 링크](https://oauth.net/2/)에서 확인할 수 있습니다.

### Field 정보

**Client ID**

32길이의 문자열로 구성됩니다. Authorized Code를 획득하기 위해 필수 항목입니다.

**Client Secret**

Client ID와 함께 제공되는 Secret Key입니다. Client ID와 함께 사용되는 필수 항목입니다.

**Authorization Code**

사용자의 인증 이후, 획득하는 code 입니다.

보안상의 이유로 OAuth2.0은 Access Token을 인증 이후, 바로 전달해주지 않습니다. Callback URL에 Querystring 형태로 Authorized Code를 전달합니다.

Client에서는 해당 Code를 통해서 Access Token을 획득할 수 있습니다. Callback URL은 사전에 요청하여 발급 받아야 합니다.

**Access Token**

RAYTeams OpenAPI Platform에서 사용되는 인증 정보입니다. RAYTeams API Resources 들은 요청 헤더에 Access Token을 같이 전달해야합니다.

이 Access Token은 Request Header에 `token` 이라는 key의 value로 전달해야 합니다.

**Refresh Token**

Access Token은 Expired가 존재합니다. 즉, 발급 받은 Access Token은 지정된 기간동안에만 사용이 가능합니다.

해당 유효기간이 지나면, Access Token을 발급 받은 시점에 같이 전달되는 Refresh Token을 통해서 Access Token을 신규로 발급 받을 수 있습니다.

### Scope

RAYTeams OpenAPI Service에서는 별도의 Scope을 지정하지 않습니다.

현재 버전의 OpenAPI Service에서는 Access Token을 통해서 모든 API Resources를 접근하여 사용할 수 있습니다.

<aside>
💡 추후에는 이 부분이 변경될 수 있습니다.

</aside>

## How to get Access Token