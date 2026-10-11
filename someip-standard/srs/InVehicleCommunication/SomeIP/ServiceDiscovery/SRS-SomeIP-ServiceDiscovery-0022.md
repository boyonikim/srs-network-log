---
uid: SRS-UID-a142b67d6b15
id: SRS-SomeIP-ServiceDiscovery-0022
cb_id: 40438683
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Publication Stop on Service Deactivation
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-ServiceDiscovery-0021
- SRS-SomeIP-ServiceDiscovery-0020
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 service provider가 application으로부터 해당 service의 제공 중지 요청을 수신하거나 해당 service를 제공하는 application의 종료를 감지한 경우, 해당 service의 EventGroup publication을 중단하여야 한다.
## Notes
