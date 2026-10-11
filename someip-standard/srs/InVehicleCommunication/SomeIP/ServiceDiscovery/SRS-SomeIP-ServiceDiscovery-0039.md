---
uid: SRS-UID-50f6e5ad9190
id: SRS-SomeIP-ServiceDiscovery-0039
cb_id: 40438692
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Subscription Lifetime
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_Sub_TTL
  type: uint32
  range: 1~65535
  unit: s
  default: '3'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 {P_SD_Sub_TTL} 값을 TTL 필드에 설정하여 전송한 SubscribeEventGroup entry를 service provider가 수신하여 수락한 경우, 해당 entry에 포함된 TTL 필드 값 동안 해당 subscription을 유효한 상태로 유지하여야 한다.
## Notes
