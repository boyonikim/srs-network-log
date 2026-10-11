---
uid: SRS-UID-c2e6e4d1c0a3
id: SRS-SomeIP-ServiceDiscovery-0061
cb_id: 38210993
domain: someip
parent: SRS-UID-88c1c630dd53
title: EventGroup Resubscription Attempt
status: Specified
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items:
- SRS-SomeIP-RoutingManagement-0016
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38203831
---

## Description

SOME/IP Service Discovery 기능은 EventGroup subscription 연결이 SD TTL 만료, 전송 계층 연결 종료 또는 Provider 비정상 종료(프로세스/실행 환경 종료 포함)가 감지되어 단절된 경우에 한하여 resubscription을 시도하여야 한다.
## Notes
