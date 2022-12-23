---
title: "Z.4 Files & Attachements"
weight: 4
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Summary

Project의 Attachments와 Files에 대해서 소개합니다.

## Basic Concept

### Files

Project는 Meta 정보와 Files 로 구성됩니다. 

RAYTemas Open API에서는 Project를 구성하는 File Handling에는 많은 제약사항이 존재합니다.

Project Files는 최초 생성하는 Application/Service 에서 언제든 Import할 수 있는 형태로 존재해야합니다.

즉, Appliction / Service에서 호환되는 형태와 규격을 유지해야하기 때문에 Project Files를 직접적으로 수정/등록하는 API는 제한 요소가 많습니다.

### Attachments

Project를 직접적으로 구성하는 File과는 별도로 부가적인 형태로 관리되는 파일들을 말합니다.

Project Attachments는 자유롭게 등록/수정이 가능합니다.

Project Files은 Project의 구성품이라고 볼수 있다면, Project Attachments는 부가적인 첨부라고 볼 수 있습니다.