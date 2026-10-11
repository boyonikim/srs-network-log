---
uid: SRS-UID-08155596f55d
id: SRS-SomeIP-RoutingManagement-0051
cb_id: 40610526
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Unavailability on OfferService TTL Expiry
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 진행 중인 OfferService의 TTL 카운터가 0에 도달하고 해당 service에 대한 재전송이 수신되지 않은 상태(TTL 만료)가 되면, 해당 service를 Service Unavailable 상태로 설정하고 해당 service의 모든 활성 subscription을 종료하여야 한다. SOME/IP Routing Management 소프트웨어는 Service Unavailable 전환 시점에 해당 service의 활성 EventGroup 구독자에게는 push 방식의 Event notification으로 Service Unavailable 전환을 통지하여야 한다.

## Notes


