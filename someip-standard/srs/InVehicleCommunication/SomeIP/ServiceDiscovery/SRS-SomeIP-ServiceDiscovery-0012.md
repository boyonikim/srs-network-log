---
uid: SRS-UID-8f3c39855642
id: SRS-SomeIP-ServiceDiscovery-0012
cb_id: 40438674
domain: someip
parent: SRS-UID-88c1c630dd53
title: Service Find Restart
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0010
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 consumer의 Repetition Phase에서 최대 재전송 횟수를 모두 소진하여 FindService 재전송이 종료된 이후 application으로부터 해당 service에 대한 FindService 재요청을 수신하면 Initial Wait Phase부터 Service Find 절차를 재시작하여야 한다.

## Notes
