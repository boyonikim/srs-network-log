{
  "output_path": "/home/worker/workspace/someip-standard/.srs-run/staging/RUN-6ea9e80601dc/review-re.review.part-1.json",
  "clarity_output_path": "/home/worker/workspace/someip-standard/.srs-run/staging/RUN-6ea9e80601dc/review-re.clarity-feedback.part-1.json",
  "leaves_reviewed": 23,
  "decisions_total": 230,
  "pass_count": 228,
  "fail_count": 2,
  "blocked_count": 0,
  "not_evaluated_count": 0,
  "fail_details": [
    {
      "leaf_id": "SRS-SomeIP-RoutingManagement-0096",
      "rule_id": "RE-EXCEPT-001",
      "summary": "FindService retry exhaustion path not addressed by self or any confirmed sibling (0036, SD-0011)"
    },
    {
      "leaf_id": "SRS-SomeIP-RoutingManagement-0096",
      "rule_id": "RE-PARAMREF-001",
      "summary": "mapped_parameter declares only SD-0011 but P_SD_FindRepetitionMax/BaseDelay are also independently owned by context leaves SD-0116 and SD-0115 (duplicate ownership upstream)"
    }
  ],
  "context_promotions_submitted": 2,
  "schema_validation": "both review-submission.schema.json and clarity-feedback.schema.json validated with 0 errors",
  "original_srs_files_modified": false
}