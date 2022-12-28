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

All services and data in RAYTeams are isolated by Region.

Data and services are isolated and stored and operated by Region. Region information is added to the authentication information.

## List

|Region value | Region Information | Country |
| --- | --- | --- |
| ap-northeast-1 | Asia Pacific (Tokyo) | japan, JP |
| ap-northeast-2 | Asia Pacific (Seoul) | korea, KR |
| us-east-1 | Eastern United States (Northern Virginia) | United States of America, US |
| ap-south-1 | Asia Pacific (Mumbai) | India, IN |
| ap-southeast-1 | Asia Pacific (Singapore) | Singapore, SG |
| ap-southeast-2 | Asia Pacific (Sydney) | Australia, AU |
| ca-central-1 | Canada (Central) | Canada, CA |
| eu-central-1 | Europe (Frankfurt) | germany, DE |
| eu-west-1 | Europe (Ireland) | Ireland, IE |
| eu-west-2 | Europe (London) | England, GB |
| eu-west-3 | Europe (Paris) | France, FR |
| eu-north-1 | Europe (Stockholm) | Sweden, SE |
| sa-east-1 | South America (Sao Paulo) | brazil, BR |

The ap-east-1 region can only be used in China/Hong Kong.

## Basic policy

### Decision

All groups belong to a particular country.The country is automatically determined by the nearest Region from the standard state of the above region.

### Update

Once determined, the Region information of the group cannot be changed.

If Group is operated global, you can create and operate Group's Branch by Region.