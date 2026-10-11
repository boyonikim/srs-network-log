---
uid: SRS-UID-d9ab412d2ef5
id: SRS-SomeIP-ServiceDiscovery-0001
cb_id: 38285348
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Offer Start Condition
status: Define
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
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 routing management 소프트웨어로부터 SOME/IP Service Discovery 처리 및 Service Offer 전송 허용을 의미하는 routing 초기화 완료 통지를 수신하고, service provider로부터 해당 service interface의 service 등록 완료 통지를 수신한 경우에 Service Offer의 Initial Wait Phase를 시작하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 routing 초기화 완료 통지 또는 해당 service interface의 service 등록 완료 통지 중 하나라도 수신하지 못한 경우에는 Service Offer의 Initial Wait Phase를 시작하지 않아야 한다.

## Notes
