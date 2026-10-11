---
uid: SRS-UID-dec119b739b5
id: SRS-SomeIP-ServiceDiscovery-0003
cb_id: 38210984
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Offer Initial Wait Timing
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SD_InitialDelay_Min
  type: uint32
  range: 10~1000
  unit: ms
  default: '100'
- name: P_SD_InitialDelay_Max
  type: uint32
  range: 1~3000
  unit: ms
  default: '300'
mapped_parameter: []
related_items: []
spec_pattern_type: nonfunctional
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 {P_SD_InitialDelay_Min}을 {P_SD_InitialDelay_Max} 이하로 구성하여야 하며, service provider가 Service Offer 절차를 개시할 때마다 Initial Wait Phase에서 두 파라미터 사이의 균등 분포 난수로 지연 시간을 새로 선택하고, 선택한 지연 시간 동안 대기한 후 OfferService를 전송하여야 한다.

※ 예외 규칙: SOME/IP Service Discovery 기능은 Service Offer 절차가 개시되지 않은 경우 Initial Wait Phase 대기 및 OfferService 전송을 수행하지 않아야 한다.

## Notes
