---
uid: SRS-UID-ff645c726c4a
id: SRS-SomeIP-ServiceDiscovery-0053
cb_id: 40447520
domain: someip
parent: SRS-UID-88c1c630dd53
title: Subscriber Removal on Consumer Loss
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0051
- SRS-SomeIP-ServiceDiscovery-0052
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 활성 EventGroup subscription을 보유한 consumer에 대하여 해당 consumer와의 전송 계층 연결 종료 통지 또는 해당 consumer가 연결된 Ethernet link의 link down 통지를 수신한 시점을 해당 consumer의 통신 연결 종료 또는 Ethernet link 유실 감지 시점으로 삼아 해당 consumer의 모든 활성 EventGroup subscription을 해제하여야 한다.

## Notes
