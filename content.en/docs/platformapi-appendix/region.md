---
title: "Z.1 Region"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## Summary

RAYTeams의 모든 서비스와 데이터는 Region별로 격리되어 제공됩니다.

데이터와 서비스는 Region별로 격리되어 저장되고 운영됩니다. Region 정보는 인증 정보에 추가되어있습니다.

## List

| 리전 값 | 리전 정보 | 기준 국가 정보 |
| --- | --- | --- |
| ap-northeast-1 | 아시아 태평양(도쿄) | 일본, JP |
| ap-northeast-2 | 아시아 태평양(서울) | 대한민국, KR |
| us-east-1 | 미국 동부(버지니아 북부) | 미국, US |
| ap-south-1 | 아시아 태평양(뭄바이) | 인도, IN |
| ap-southeast-1 | 아시아 태평양(싱가포르) | 싱가포르, SG |
| ap-southeast-2 | 아시아 태평양(시드니) | 오스트레일리아, AU |
| ca-central-1 | 캐나다(중부) | 캐나다, CA |
| eu-central-1 | 유럽(프랑크푸르트) | 독일, DE |
| eu-west-1 | 유럽(아일랜드) | 아일랜드, IE |
| eu-west-2 | 유럽(런던) | 영국, GB |
| eu-west-3 | 유럽(파리) | 프랑스, FR |
| eu-north-1 | 유럽(스톡홀름) | 스웨덴, SE |
| sa-east-1 | 남아메리카(상파울루) | 브라질, BR |

<aside>
💡 ap-east-1 region은 중국/홍콩에서만 사용이 가능합니다.

</aside>

## 기본 정책

### 결정

모든 Group은 특정 국가에 소속되어집니다. 해당 국가는 위의 Region의 기준 국가로부터 가장 가까운 Region으로 자동 결정됩니다.

### 변경

한번 결정된 Group의 Region 정보는 변경이 불가합니다.

Group이 Global하게 운영된다면, Region 별로 Group의 Branch를 만들어서 운영할 수 있습니다.