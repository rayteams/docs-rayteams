---
title: "Z.2 Custom Data Type"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Summary

RAYTeams의 특정 Object(Project, Group 등)은 정보를 분산하여 보관하고 있습니다.

예를들어, 1개의 Project에 대한 첨부파일은 Project 정보에 포함되어 있지 않고, 별도의 정보로 관리됩니다.

이에 이 페이지에서는 Scope 별 Custom Data Type에 대해서 소개합니다.

## Project

| sk | 내용 | Project : Rows |
| --- | --- | --- |
| project | Project의 기본 정보 | 1 : 1 |
| attachments: | Project에 첨부된 첨부파일 정보 | 1 : 0~N |
| his: | Project에 변경 이력 | 1 : 0~N |
| memo: | Project에 Memo 목록 | 1 : 0~N |
| project:institute: | Project에 관계된 Group 정보 | 1 : 2~N |
| order: | Project에서 발생한 주문 정보 | 1 : 0~N |

##