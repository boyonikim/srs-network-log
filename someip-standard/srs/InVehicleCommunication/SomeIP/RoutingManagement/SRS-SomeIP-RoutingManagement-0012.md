---
uid: SRS-UID-c724932fcc30
id: SRS-SomeIP-RoutingManagement-0012
cb_id: 38223746
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Communication Recovery Trigger on Link-Up Network Interface Restart
status: Define
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: mode_state
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---

## Description

SOME/IP Routing Management 소프트웨어는 PHY link-up 상태가 유지된 상태에서 Network Interface가 재시작되어 기존 SOME/IP 통신 자원이 무효화된 경우, 자신의 초기화가 완료된 상태(준비 완료 이후)일 때에 한하여 SOME/IP 통신 복구를 개시하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 초기화 진행 중 Network Interface 재시작을 수신하면 초기화 완료 전에는 SOME/IP 통신 복구를 개시하지 않고 초기화 완료 후에 개시하여야 한다.

## Notes
