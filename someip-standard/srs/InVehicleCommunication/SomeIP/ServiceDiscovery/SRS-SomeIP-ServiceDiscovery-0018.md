---
uid: SRS-UID-0c278137985b
id: SRS-SomeIP-ServiceDiscovery-0018
cb_id: 38285367
domain: someip
parent: SRS-UID-88c1c630dd53
title: ServiceAvailable Notification
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_ReAvailNotifyDelay
  type: uint32
  range: 0~1000
  unit: ms
  default: '100'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0002
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer가 service provider의 OfferService entry를 재수신하여 service가 재가용 상태가 된 후 {P_SD_ReAvailNotifyDelay}ms 이내에 application에 ServiceAvailable을 통지하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 consumer가 해당 service의 OfferService entry를 재수신하지 못하였거나 해당 service가 재가용 상태가 아닌 경우 application에 ServiceAvailable을 통지하지 않아야 한다.

## Notes
