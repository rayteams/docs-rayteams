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

RAYTeams Open API를 검토/검증하기 위해서 테스트할 수 있는 여러 환경을 제공합니다.

누구나 검증해볼 수 있는 Test Environment와 업체별 고유로 검증할 수 있는 Develop Environmet 가 존재합니다. 

## Z.8.2 종류 별 특징

### Z.8.2.1 Test Environment

RSP(RAYTeams Service Portal)의 개발자 계정이 존재하는 사용자들을 Test 환경을 사용할 수 있습니다.

**주요 특징**

- 매주 데이터는 초기화 됩니다.
- 다른 업체와 공용으로 사용됩니다.

### Z.8.2.1 Develop Environmet

관련 업체중에 고유의 검증 환경을 원하는 경우, RAYTeams Service Portal에서는 별도의 독립적인 환경을 제공합니다.

위의 환경을 제공받기 위해서는 별도의 절차에 의해서만 사용이 가능합니다.

**환경에 대한 비교**

| 비교 항목 | Test | Develop |
| --- | --- | --- |
| 제공하는 API | API 최신 버전 | API 최신 버전 |
| 데이터 | 공용 | 독립/격리 |
| 데이터 보존 기한 | 매주 초기화 | 환경 종료시에 자동 삭제 |
| 환경의 종료 | 없음 | 생성 후 6개월 |
| 사용의 제한 | 없음 | 별도의 절차 필요 |

## Z.8.3 Develop Key(Develop sandbox only)

별도로 독립적인 환경을 구성하기 위해서는 ClientID / Client Secret를 발급 받아야 합니다.

별도의 절차를 따라 ClientID / Client Secret를 발급받을 수 있고, 해당 정보는 특정 기간 동안(생성후 6개월)만 유효합니다.

### Z.8.3.1 발급 절차

아래의 순서로 독립적인 환경 사용을 위한 ClientID / Client Secret 값을 받을 수 있습니다.

1. [Ray Service Portal](https://www.notion.so/RAYTeams-Service-Portal-b85d227c492e47de98e315a241502979)에 가입( [https://rsp.rayteams.com/](https://rsp.rayteams.com/) ) 
2. Develop Key 생성 요청서 작성 및 Submit
3. 검토 및 승인 안내
4. 발급 완료

**검토 및 승인 안내**는 약 1~3일(영업일 기준) 정도 소요됩니다.

## Z.8.4 API Swagger

RAYTeams API Service에는 API 테스트를 위한 Test Tool을 제공합니다.

Test Tool은 [Swagger](https://swagger.io/)로 구성되어 있으며, [Ray Service Portal](https://www.notion.so/RAYTeams-Service-Portal-b85d227c492e47de98e315a241502979) 에 접속하여 확인할 수 있습니다.

사용할때에는 환경에 맞는 ClientID와 Client Secret을 통해서만 정상적으로 Test 할 수 있습니다.

<aside>
❓ 일부 API는 환경과 Scope에 따라 노출되지 않을 수 있습니다.

</aside>