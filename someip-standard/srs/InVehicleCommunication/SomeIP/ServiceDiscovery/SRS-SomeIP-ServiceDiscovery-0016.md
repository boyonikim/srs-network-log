---
uid: SRS-UID-d08443cd2e24
id: SRS-SomeIP-ServiceDiscovery-0016
cb_id: 38285354
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Loss Notification Deadline
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
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 OfferService SD entry의 TTL 만료를 감지하면 해당 service의 제공 유효기간이 종료된 것으로 판단하고, {P_SD_FindMaxRecoveryTime}ms 이내에 application에 service 유실을 통지하여야 한다. 해당 시간 내 통지가 완료되지 않으면 service 유실 통지는 기한 내 완료된 것으로 취급하여서는 안 된다.
## Notes
