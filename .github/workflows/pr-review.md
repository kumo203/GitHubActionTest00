---
on:
  pull_request:
    types: [opened, synchronize]

permissions:
  contents: read
  pull-requests: read

engine:
  id: copilot
  model: gpt-6-luna
  env:
    COPILOT_PROVIDER_BASE_URL: https://20261106foundry.openai.azure.com/openai/v1
    COPILOT_PROVIDER_API_KEY: ${{ secrets.FOUNDRY_API_KEY }}

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
Post inline comments only for high-severity findings, and finish with a single review containing an overall summary. Write in Japanese.