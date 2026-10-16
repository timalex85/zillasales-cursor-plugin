# Reviewer test plan

## Local discovery

Install the package following README.md, reload the client and verify that its MCP server and all skills appear. Only the declared HTTPS endpoint should be contacted. No local command, hook or installer should run.

## Public tools

1. Ask: "Find technology sales opportunities covering the United States. Compare disclosed territories and commission terms; mark unknown terms clearly. Do not save or apply."
2. Ask: "Find independent technology sales reps covering the United States. Compare their public experience and territory coverage. Do not contact anyone."
3. Expect catalog/search/detail tool calls and source-backed results or an honest empty result. These service calls are public, but the full package may request OAuth during initial connection. Text results must work even if the host cannot render MCP Apps.

## Optional account tools

Use a dedicated synthetic rep account to save an opportunity and inspect favorites. Saving must not apply. Preparing an application must show the exact content and require explicit confirmation before submission; stop before submission during review.

Use a dedicated synthetic company account to inspect its own sample private opportunity draft. Do not publish it or send it to moderation. Confirm the rep account cannot access company-only records and that no real customer data appears.

## OAuth and failure behavior

The package uses a registered public OAuth client and S256 PKCE. Complete the host connection prompt before testing private tools. Test successful consent, denied consent, reconnection and refresh without placing credentials in the conversation. An unconnected private tool must not disclose records. Report rate limits and unavailable tools accurately.

Reviewer credentials, if separately authorized, must be supplied through the marketplace's private review channel. They are deliberately absent from this public repository.

## Completion record

Record client version, package commit, date, local discovery, public tool results and optional authenticated results for each host. A completed protocol smoke test is not an in-app test. Do not check the submission's testing attestation until the target-host checks pass.

## Verify actual authorization

After consent, call the account-access tool and verify it succeeds. A host label saying “Connected” or “authenticated” is not sufficient: Cursor can establish an anonymous MCP transport without an account token. Version 1.0.1 adds explicit public-client OAuth configuration to address this. Test URL-only anonymous access separately when reviewing the public service endpoint.

## Recorded verification — 16 October 2026

Cursor desktop 3.24.18 for macOS, using Grok 4.6 Medium: 22 tools, one resource and two skills discovered. Public catalog, opportunity search and representative search passed. After browser OAuth consent, get_account_access returned a connected company and get_my_opportunities returned its single synthetic hidden draft.

The initial URL-only configuration exposed a Cursor lazy-authentication failure. Version 1.0.1 was verified with explicit public-client OAuth and actual private tool calls, not just a connected indicator. No customer records, purchases, outreach or publication were involved.

Standalone Grok Bot has not been tested: the test account is on Cursor Free with Legacy Privacy Mode. Grok Bot requires eligible paid access and cloud-storage-compatible privacy settings. Cursor results must not be represented as standalone Grok Bot results.
