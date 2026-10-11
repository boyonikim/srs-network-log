---
uid: SRS-UID-faa6b5c06ab7
id: SRS-SomeIP-RoutingManagement-0020
cb_id: 40610563
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Discovery Resumption on Ethernet Interface Fault Clearance
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 Ethernet Fault Management 모듈로부터 Ethernet interface fault가 해제되었음을 나타내는 상태 변화 이벤트를 수신하면, 해당 link에 대해 중단되어 있던 service discovery를 재개하여 FindService 전송을 Multicast SD endpoint로 재개시하여야 한다. Service discovery 재개 완료는 해당 link에 대한 FindService 메시지가 Multicast SD endpoint로 최초 전송된 시점으로 판정한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 Multicast SD endpoint를 사용할 수 없으면 Unicast SD endpoint로 FindService 전송을 재개하고 오류를 기록하여야 한다.

## Notes
