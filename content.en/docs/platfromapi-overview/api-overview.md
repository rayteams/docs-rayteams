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

All APIs provided by RayTeams are formatting.

All of the APIs you request are indicated as lowercase, and all of the parameter requested by GET must be `urlencoding`.

**Format**

```
https://api-[REGION]-[SCOPE].rayteams[SANDBOX].com/v[VERSION]/
```

### Item information

- REGION : RayTEAMS Region information is confirmed in the [Z.1 Appendix - Region](/docs/platformapi-appendix/region/) document.
- SCOPE : Scope is defined in [Z.3 Appendix - Scope](/docs/platformapi-appendix/scope/).
- SANDBOX
    - Sandbox information is a key used to provide an independent/isolated API environment provided to develop or verify the API based on the API.
    - Please refer to the [Z.9 Appendix - Sandbox](/docs/platformapi-appendix/sandbox/) document on the Sandbox environment for sandbox.

Example

```
https://api-ap-northeast-2-project.rayteams.com/v1.0/
```

## Version Information

### Verion

All APIs display the Version information on the URL as above.

The Version notation is marked with three octets, along with Prefix, which represents the version of `v` before.

Example

```
v1.0
```

The Deprecate API is also available unless there is a special issue.

Please refer to the [Depate API] document for the Deprecate API.

## Error Handling

### Summary

RayTears Open API Services uses standard http status response codes for all requests.

In large classifications, it is divided into three types as shown below.

- 200 : Normal processing for requests
- 4XX : It cannot be processed due to the problem of user authentication information
- 5XX : Problems arise during the process of requesting request

The information about each status codes is as follows.

| Status code | Description |
| --- | --- |
| 200 | Normally handled for requests |
| 401 | The authentication information is not correct |
| 403 | It is not a normal request, so refuses to access |
| 404 | There is no request for the request |
| 429 | Refusing requests due to too many requests |
| 500 | Errors occur while handling requests on the server |

### Custom Error

The response status code is 200, so it doesn't deliver the desired results of the request for the request.

Each resources will proceed with the validation for each process.At this time, the Custom Error will occur for the Invalid Request.

In other words, the Response Status Code is 200, but you can deliver the custom error that occurs during the request.

### Error Response Schema

Error response is delivered in two forms.

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

Custom error is mostly expressed simply.Individual custom errors can be found in individual API resourse.