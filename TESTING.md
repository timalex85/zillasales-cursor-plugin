# Reviewer test plan

## Local discovery

Install the package following README.md, reload the client and verify that its MCP server and all skills appear. Only the declared HTTPS endpoint should be contacted. No local command, hook or installer should run.

## Public tools (no account required)

1. Ask: "Find technology sales opportunities covering the United States. Compare disclosed territories and commission terms; mark unknown terms clearly. Do not save or apply."
2. Ask: "Find independent technology sales reps covering the United States. Compare their public experience and territory coverage. Do not contact anyone."
3. Expect catalog/search/detail tool calls and source-backed results or an honest empty result. No sign-in should be requested for these public searches. Text results must work even if the host cannot render MCP Apps.

## Optional account tools

Use a dedicated synthetic rep account to save an opportunity and inspect favorites. Saving must not apply. Preparing an application must show the exact content and require explicit confirmation before submission; stop before submission during review.

Use a dedicated synthetic company account to inspect its own sample private opportunity draft. Do not publish it or send it to moderation. Confirm the rep account cannot access company-only records and that no real customer data appears.

## OAuth and failure behavior

Account operations should trigger the host's normal OAuth connection, using dynamic client registration and S256 PKCE. Test successful consent, denied consent, reconnection and refresh without placing credentials in the conversation. An unconnected private tool must not disclose records. Report rate limits and unavailable tools accurately.

Reviewer credentials, if separately authorized, must be supplied through the marketplace's private review channel. They are deliberately absent from this public repository.

## Completion record

Record client version, package commit, date, local discovery, public tool results and optional authenticated results for each host. A completed protocol smoke test is not an in-app test. Do not check the submission's testing attestation until the target-host checks pass.
