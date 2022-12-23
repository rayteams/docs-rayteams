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

RAYTeams Open API에서는 Project와 Order를 별개의 Resource로 관리하고 있습니다.

다만, Order는 Project에 의해 파생된 부가 정보입니다.

즉, Order는 Project 없이 생성될 수 없습니다. 이에 대한 자세한 정보를 설명합니다.

## Project

### 주요 정보

- Project는 데이터를 공유하는 기본 단위입니다.
- Project는 File과 Meta 정보로 구성됩니다.
- File & Meta 정보는 Project Type 별로 그 구조가 다릅니다. ( [Z.6 Appendix - Project file types](https://www.notion.so/Z-6-Appendix-Project-file-types-33fd7fe8e45e456eb8e14524671a6d85) )
- 1개의 Project는 여러개의 Order를 가질 수 있습니다.

### ProjectId

- Project를 식별할 수 있는 UUID입니다.

## Order

### 주요 정보

- Order는 Project 정보를 기반으로 하여 생성되는 주문을 말합니다.
- Project와 Order의 관계는 1 : 0~n 관계 입니다.
- 단순 데이터 공유 목적으로 사용되는 Project에는 Order가 존재하지 않습니다.
- Order는 해당 Project를 공유하고 있는 Group이외의 Group이 관여할 수 없습니다.

### OrderId

- Order를 식별할 수 있는 String value입니다.
- OrderId는 ProjectId와 Order 생성 시점의 timestamp를 조합하여 사용합니다.

```
334c972a-5756-45f7-8eb1-f3f84bedd525 //Project Id
334c972a-5756-45f7-8eb1-f3f84bedd525-1669345121504 //Order Id #A
334c972a-5756-45f7-8eb1-f3f84bedd525-1669346270408 //Order Id #B
```