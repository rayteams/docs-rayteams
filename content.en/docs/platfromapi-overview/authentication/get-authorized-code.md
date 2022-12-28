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

To get the Access token required for the API Request, you must first be given an authorized code.

Call the delivered Login URL to induce authentication to the user and be redirected to the Callback URL when the authentication is successful.

At this time, the Callback URL passes the authorized code to the value of a parameter called Code in the form of queryString.

## Issuance

The example below is an example, so do not use Code or URL as it is.

It is also a way to show how to get the authorized code.

### **Step #1. Request Login URL**

```
GET https://oauth-ap-northeast-2-development.rayteams.com/oauth2/authorize
```

In the form above, Login URL induces a login to the RayTeams Service to the user.

Call the web browser and work with the above link information to be loaded in the browser.

When calling from the web, you can call in the form as shown below.

```
<a href="https://oauth-ap-northeast-2-development.rayteams.com/login?client_id=37ev8rm4mvtnb65hf381l0k98b&response_type=code&redirect_uri=http://localhost/callback">RAYTeams Connect</a>
```

- `https://oauth-ap-northeast-2-development.rayteams.com/login`
    
    The above information is usually the endpoint uri used in Development Stage.
    
- `client_id=37ev8rm4mvtnb65hf381l0k98b`
    
    The client ID uses the App ID to use.
    
- `response_type=code`
    
    This key/value is fixed. No other values are used.
    
- `redirect_uri=http://localhost/callback`
    
    Callback URL used by the corresponding Client ID.It doesn't matter if it's not localhost.You can also use the Domain in service.
    
    If the user's login is successful, the `code` value is delivered to this callback URL.
    

### **Step #2. User Login**

On the login screen, the user performs login to his account.

In addition to the login function, the FORGOT PASSWORD features can also be processed for the loss of password.

If the user logs in normally, the page is redirected to the Callback URL.

### **Step #3. Get Authorized Code**

Authorized code is transmitted to the value of `code` to the callback URL.

Web page is moved in the form as shown below.

```
http://callback-domain/callback?code=baaca0d5-0044-424e-9311-16d3d754784f
```

At this time, the value of `code` delivered is an authorized code for acquiring token.

Please refer to the [2. Get Access Token](https://www.notion.so/2-Get-Access-Token-da18aa8c48ec46799dc73a18b0a2ec24) document for how to obtain `Access Token` using the acquired `Authorized Code`.