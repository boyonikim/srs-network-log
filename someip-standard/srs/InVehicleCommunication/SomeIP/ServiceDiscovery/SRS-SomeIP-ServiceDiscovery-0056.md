---
uid: SRS-UID-22d7fe94db52
id: SRS-SomeIP-ServiceDiscovery-0056
cb_id: 38285350
domain: someip
parent: SRS-UID-88c1c630dd53
title: StopOfferService for Sleep Preparation
status: Reviewed
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: interface_comm
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 sleep 진입 준비 절차에서 모든 활성 service에 대해 StopOfferService를 전송하여야 한다.

SOME/IP Service Discovery 기능은 sleep 진입 준비 절차에서 활성 service가 없는 경우 StopOfferService를 전송하지 않아야 한다.

## Notes
