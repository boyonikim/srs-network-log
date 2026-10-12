{
  "output_path": "/home/worker/workspace/someip-standard/.srs-run/staging/RUN-6ea9e80601dc/review-re.review.part-2.json",
  "clarity_output_path": "/home/worker/workspace/someip-standard/.srs-run/staging/RUN-6ea9e80601dc/review-re.clarity-feedback.part-2.json",
  "task_id": "review-re",
  "leaves_reviewed": 21,
  "decisions_total": 210,
  "verdict_summary": {
    "PASS": 209,
    "FAIL": 1,
    "BLOCKED": 0
  },
  "execution_status": "SUCCEEDED",
  "fail_detail": {
    "leaf_uid": "SRS-UID-70eb93a1b2b5",
    "leaf_id": "SRS-SomeIP-RoutingManagement-0086",
    "rule_id": "RE-PARAMREF-001",
    "reason": "body references {P_SD_SubscribeRetryMax}/{P_SD_SubscribeRetryDelay} but mapped_parameter only declares SD-0045 (SRS-UID-90652d5d7aa3); missing mapping to the other owners of those same parameter names, SD-0063 (SRS-UID-54ac7aca6d5c) and SD-0048 (SRS-UID-4aa54bece4a9).",
    "reason_code": "content_defect",
    "actionability": "edit"
  },
  "clarity_delegation": "Applied srs-clarity's instruction_SRS_clarity_single.md 4-criteria judgment locally (no tracker/ask_user/CB calls) to all 21 leaves for RE-AMBIG-001/RE-SUBJECT-001/RE-VERIFY-001/RE-ATOMIC-001; all 21 passed all 4 criteria. Full clarity feedback (type classification + 4-criteria check + improvement-suggestion table) saved per leaf to clarity_output_path with overall_verdict PASS for all entries.",
  "schema_validation": "Both review.json and clarity-feedback.json validated in-process against contracts/review-submission.schema.json and contracts/clarity-feedback.schema.json respectively, and re-validated after re-reading from disk.",
  "source_files_modified": "none (read-only RE review; original srs/*.md files untouched)"
}