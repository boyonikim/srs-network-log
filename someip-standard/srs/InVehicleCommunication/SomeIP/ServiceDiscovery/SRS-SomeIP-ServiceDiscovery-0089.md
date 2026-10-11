---
uid: SRS-UID-f7bbb9fa57d6
id: SRS-SomeIP-ServiceDiscovery-0089
cb_id: null
domain: someip
parent: SRS-UID-88c1c630dd53
title: Malformed SubscribeEventGroup Entry Handling
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0037
- SRS-SomeIP-ServiceDiscovery-0043
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

SOME/IP Service Discovery 기능은 수신한 SubscribeEventGroup entry가 길이 불일치, 미지원 entry type, 또는 protocol version 불일치로 인해 파싱에 실패한 경우 해당 entry를 폐기하여야 하며, 필드 값 범위 위반 시와 달리 SubscribeEventGroupNack을 전송하지 않아야 한다.

## Notes

