---
uid: SRS-UID-cfc2aa18135b
id: SRS-SomeIP-ServiceDiscovery-0057
cb_id: 40438671
domain: someip
parent: SRS-UID-88c1c630dd53
title: StopOfferService Completion for Sleep Preparation
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0056
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider의 sleep 진입 준비 절차에서 모든 활성 service에 대한 StopOfferService 중 마지막 message의 송신 완료를 전송 계층으로부터 통지받은 시점(`StopOfferService 전송 완료 시점`)에 application에 StopOfferService 전송 완료 사실을 통지하여야 한다.

## Notes
