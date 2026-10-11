---
uid: SRS-UID-5d80f0f84b43
id: SRS-SomeIP-RoutingManagement-0073
cb_id: null
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Session-Oriented Method TCP Policy
status: Draft
inclusion_type: Mandatory
optional_condition: null
configuration_type: Fixed
parameter_definition: []
mapped_parameter: []
related_items: []
spec_pattern_type: data_logic
evidence: []
verification: null
diagrams: []
attachments: []
cb_target_profile:
  parent_cb_id: 38223716
---
## Description

SOME/IP Routing Management 소프트웨어는 재등록 및 service discovery 재개 시 각 service 또는 Method에 대해 transport policy를 적용할 때 delivery requirement가 best-effort(유실 허용)이고 SOME/IP payload size가 표준 Ethernet MTU 1500B에서 IP/UDP/SOME/IP header overhead를 제외한 1400 bytes 이하이더라도 session/connection-oriented Method에는 TCP를 선택하여야 한다.

※ 예외 규칙
SOME/IP Routing Management 소프트웨어는 session/connection-oriented Method에 대한 transport policy 기준을 평가할 수 없거나 TCP를 선택할 수 없으면 transport policy 평가 실패로 처리하여야 하며, 유효한 기준과 입력이 확보될 때까지 해당 Method의 transport 선택을 완료한 것으로 처리하지 않아야 한다.

## Notes


