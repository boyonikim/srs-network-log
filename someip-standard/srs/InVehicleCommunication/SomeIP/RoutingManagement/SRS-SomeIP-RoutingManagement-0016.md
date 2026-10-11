---
uid: SRS-UID-8eb355e1a452
id: SRS-SomeIP-RoutingManagement-0016
cb_id: 38210992
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service Unavailability Notification on Provider Loss
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Parameterized
parameter_definition:
- name: P_SvcUnavail_NotifyTimeout
  type: uint32
  range: 50~2000
  unit: ms
  default: '500'
mapped_parameter: []
related_items: []
spec_pattern_type: exception_fault
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 service provider의 비정상 종료(프로세스 또는 실행 환경 종료 포함) 또는 로컬 Ethernet 단절을 포함한 네트워크 연결 단절이 감지되면, 감지 시점부터 측정하여 {P_SvcUnavail_NotifyTimeout}ms 이내에 service consumer에게 Service Unavailable 상태 통지 메시지 전송을 완료하여야 한다. SOME/IP Routing Management 소프트웨어는 위 통지 시도가 {P_SvcUnavail_NotifyTimeout}ms 이내에 완료되지 못하면 통지 실패로 기록하고 application에 통지 실패를 보고하여야 한다.

## Notes

해당 service의 내부 상태 정리는 SRS-SomeIP-RoutingManagement-0057에서 규정한다.
