---
uid: SRS-UID-47c2e36f6f69
id: SRS-SomeIP-ServiceDiscovery-0104
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Loss Notification Suppression
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_FindMaxRecoveryTime
  type: uint32
  range: 100~30000
  unit: ms
  default: '5000'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0002
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---
## Description

SOME/IP Service Discovery 기능은 OfferService SD entry의 TTL 만료를 감지한 경우 해당 service를 service 유실 상태로 전이하여야 한다.
SOME/IP Service Discovery 기능은 OfferService SD entry의 TTL 만료를 감지하지 않은 경우 TTL 만료 사유의 service 유실을 통지하여서는 안 된다.

## Notes

