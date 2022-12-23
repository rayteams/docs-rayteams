---
title: "3.1 Get Authorized Code"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Summary

API Request에 필요한 Access Token을 획득하기 위해서는 먼저 Authorized Code를 부여받아야 합니다.

전달된 Login URL을 호출하여 사용자에게 인증을 유도하고 인증이 성공되면 Callback URL로 Redirection 됩니다.

이때 Callback URL에 QueryString 형태로 code 라는 Parameter 의 값으로 Authorized Code를 전달합니다.

## 발급 순서

아래의 예시는 예제이기 때문에 Code나 URL을 그대로 사용하면 안됩니다.

어떻게 Authorized Code를 부여 받는지에 대한 Step을 보여주는 용도입니다.

### **Step #1. Request Login URL**

```jsx
GET https://oauth-ap-northeast-2-development.rayteams.com/oauth2/authorize
```

위의 형태로 Login URL로 사용자에게 RAYTeams Service에 로그인을 유도합니다.

웹 브라우저를 호출하여 위의 Link 정보로 브라우저에서 Load 되도록 작업이 이루어저야 합니다.

웹에서 호출할 때에는 아래와 같은 형태로 호출할 수 있습니다.

```jsx
<a href="https://oauth-ap-northeast-2-development.rayteams.com/login?client_id=37ev8rm4mvtnb65hf381l0k98b&response_type=code&redirect_uri=http://localhost/callback">RAYTeams Connect</a>
```

- `https://oauth-ap-northeast-2-development.rayteams.com/login`
    
    위의 정보는 일반적으로 development stage에서 사용하는 Endpoint URI 입니다.
    
- `client_id=37ev8rm4mvtnb65hf381l0k98b`
    
    Client ID는 사용할 App ID를 사용합니다.
    
- `response_type=code`
    
    이 Key/Value는 고정입니다. 다른 값을 사용할 수 없습니다.
    
- `redirect_uri=http://localhost/callback`
    
    해당 Client ID가 사용하는 Callback URL입니다. localhost가 아니어도 상관 없습니다. 서비스 중인 Domain을 이용할 수도 있습니다.
    
    사용자의 로그인이 성공하면 이 Callback URL로 `code` 값이 전달됩니다.
    

### **Step #2. User Login**

Login 화면에서 사용자는 자신의 계정으로 로그인을 수행합니다.

로그인 기능외에 Forgot Password 의 기능을 통해서 Password 분실에 대한 처리도 같이 진행할 수 있습니다.

사용자가 정상적으로 로그인을 하면, 해당 페이지는 Callback URL로 Redirection 됩니다.

### **Step #3. Get Authorized Code**

Callback URL에 `code` 의 값으로 Authorized Code가 전달됩니다.

아래와 같은 형태로 Web page가 이동됩니다.

```jsx
http://callback-domain/callback?code=baaca0d5-0044-424e-9311-16d3d754784f
```

이때 전달되는 `code`의 값이 Token을 획득하기 위한 Authorized Code입니다.

<aside>
💡 획득한 `Authorized code` 를 이용하여 `Access Token`을 발급 받는 방법은 [2. Get Access Token](https://www.notion.so/2-Get-Access-Token-da18aa8c48ec46799dc73a18b0a2ec24)  문서를 참고해주시기 바랍니다.

</aside>