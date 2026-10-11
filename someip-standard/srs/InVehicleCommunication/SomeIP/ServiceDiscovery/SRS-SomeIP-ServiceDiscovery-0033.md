---
uid: SRS-UID-084d91030318
id: SRS-SomeIP-ServiceDiscovery-0033
cb_id: 40438687
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Limit Notification
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_MaxEventGroups
  type: uint16
  range: 1~128
  unit: count
  default: '32'
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0032
- SRS-SomeIP-ServiceDiscovery-0002
- SRS-SomeIP-ServiceDiscovery-0008
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 관리 중인 EventGroup 수가 {P_SD_MaxEventGroups}에 도달한 상태에서 신규 EventGroup 등록을 유발하는 SubscribeEventGroup 요청을 수신하면 거부된 요청의 Service ID, Instance ID, EventGroup ID와 EventGroup 관리 수 상한 초과 사유를 포함한 리소스 부족 통지를 application에 전송하여야 한다.
## Notes
