---
on:
  pull_request:
    types: [opened, synchronize]

permissions:
  contents: read
  pull-requests: read

engine: copilot   # optional (default)

tools:
  github:
    toolsets: [pull_requests, repos]

safe-outputs:
  add-comment:
    max: 1
  create-pull-request-review-comment:
    max: 10
    side: "RIGHT"
  submit-pull-request-review:
    max: 1
    allowed-events: [COMMENT]
---

# Pull Request Review Assistant

Review the diff of this pull request. Focus on correctness, security, maintainability, and test coverage.
Post inline comments only for high-severity findings, and finish with a single review containing an overall summary. Write in English and Japanese.