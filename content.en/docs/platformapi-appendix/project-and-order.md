---
title: "Z.7 Project & Order"
weight: 7
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Summary

RayTears Open API manages Project and Order as a separate resource.

However, the order is additional information derived by Project.

In other words, the order cannot be created without a project. Explain more information about this.

## Project

### 주요 정보

- PROJECT is the basic unit of sharing data.
- PROJECT consists of file and meta information.
- File & Meta information has a different structure for each project type. ( [Z.6 Appendix - Project file types](/docs/platformapi-appendix/project-file-types/) )
- One project can have multiple orders.

### ProjectId

- UUID that can identify Project.

## Order

### 주요 정보

- ORDER is an order generated based on Project information.
- The relationship between Project and Order is 1: 0 ~ N relationship.
- There is no order in the project used for simple data sharing purposes.
- ORDER cannot be involved in groups other than group that shares the Project.

### OrderId

- String value that can identify Order.
- OrderID uses a combination of timestamp at the time point of projectID and order.

```
334c972a-5756-45f7-8eb1-f3f84bedd525 //Project Id
334c972a-5756-45f7-8eb1-f3f84bedd525-1669345121504 //Order Id #A
334c972a-5756-45f7-8eb1-f3f84bedd525-1669346270408 //Order Id #B
```