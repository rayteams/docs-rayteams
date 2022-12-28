---
title: "Z.8 Sandbox"
weight: 8
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Z.8.1 Summary

It provides multiple environments that can be tested to review/verify the RAYTeams Open API.

There is a test Environment that anyone can verify and a Developing Environment that can be verified by company.

## Z.8.2 Types of features

### Z.8.2.1 Test Environment

You can use the test environment for users who have a developer account of RayTeams Service Portal(RSP).

**Main features**

- Weekly data are initialized.
- It is used as common with other companies.

### Z.8.2.1 Develop Environmet

If you want a unique verification environment among the related companies, the RayTeams Service Portal offers a separate independent environment.

To receive the above environment, it can only be used by a separate procedure.

**Comparison of the environment**

| Compare | Test | Develop |
| --- | --- | --- |
| API provided | API latest version | API latest version |
| Data | Public | Independence/isolation |
| Data Initialize | Every week initialization | Automatic deletion at the end of the environment |
| End of the Environment | No | 6 months after creation |
| Restriction of use | No |Separate procedure required |

## Z.8.3 Develop Key(Develop sandbox only)

In order to form an independent environment separately, you need to be issued a clientId / Client Secret.

ClientID / Client Secret can be issued along a separate procedure, and the information is valid for a certain period of time (6 months after creation).

### Z.8.3.1 Issuance

In the following order, you can receive a clientId / client secret value for the use of an independent environment.

1. Reguster in [Ray Service Portal](https://www.notion.so/RAYTeams-Service-Portal-b85d227c492e47de98e315a241502979)( [https://rsp.rayteams.com/](https://rsp.rayteams.com/) ) 
2. Develop key creation request and submit
3. Review and approval guide
4. Completion of issuance

**Review and approval guidance** takes about 1-3 days (business day).

## Z.8.4 API Swagger

RayTeams API Service provides test tools for API tests.

Test Tool consists of [Swagger](https://swagger.io/) and can be checked by accessing the Ray Service Portal(RSP).

When using it, you can only test it only through clientId and Client Secret for the environment.

Some APIs may not be exposed according to the environment and scope.