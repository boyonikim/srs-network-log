---
uid: SRS-UID-92ed186bd860
id: SRS-SomeIP-ServiceDiscovery-0032
cb_id: 40435998
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Management Count Limit
status: Reviewed
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
- SRS-SomeIP-ServiceDiscovery-0034
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 관리 가능한 EventGroup 수를 {P_SD_MaxEventGroups} 이하로 제한하여야 한다.

## Notes
