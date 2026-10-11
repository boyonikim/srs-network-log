---
uid: SRS-UID-a0579b1efdb0
id: SRS-SomeIP-ServiceDiscovery-0027
cb_id: 40438681
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Publication Stop on StopOfferService
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0024
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider로부터 StopOfferService를 수신하거나, OfferService TTL 만료 또는 service provider와의 전송 계층 연결 종료를 감지한 경우 해당 EventGroup notification 수신 처리가 중단되도록 해당 service의 EventGroup subscription을 해제하여야 한다.

## Notes
