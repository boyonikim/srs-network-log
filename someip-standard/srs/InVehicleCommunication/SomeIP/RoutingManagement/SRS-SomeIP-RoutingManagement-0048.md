---
uid: SRS-UID-c9d33433a36d
id: SRS-SomeIP-RoutingManagement-0048
cb_id: 40610556
domain: someip
parent: SRS-UID-b5ad30afa2ec
title: Service and Method Transport Policy
status: Specified
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

SOME/IP Routing Management 소프트웨어는 재등록 및 service discovery 재개 시 각 service 또는 Method에 대해 transport policy를 적용할 때, 프로젝트 설정으로 지정된 delivery requirement 값이 guaranteed/reliable delivery(재전송 및 순서 보장 필요)이면 TCP를 선택하여야 한다.

SOME/IP Routing Management 소프트웨어는 delivery requirement 설정값이 프로젝트 설정에 정의되어 있지 않으면 transport policy 평가 실패로 처리하여야 하며, 해당 설정값이 정의될 때까지 transport 선택을 완료한 것으로 처리하지 않아야 한다.

## Notes
