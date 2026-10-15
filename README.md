# ZillaSales for Cursor and Grok Bot

Find independent sales reps and commission-based opportunities. Compare territories and terms, build shortlists, and prepare applications or private opportunity drafts.

![ZillaSales](assets/icon.png)

Find independent sales opportunities and representatives, compare results, and manage your own shortlist and application or opportunity drafts.

Public opportunity and representative searches work without sign-in. Connect a ZillaSales company or rep account when you ask to save items, read private records, prepare drafts, or apply. Existing account permissions still govern access. Saving does not apply, contact anyone, unlock contact details or spend credits. Applications and moderation submissions require reviewing the exact proposed action and explicitly confirming it.

The plugin includes two skills: finding sales opportunities and building sales coverage. Interactive comparison views use MCP Apps; text results remain available when a client cannot show the view.

## Examples

- "Find commission-based industrial automation opportunities covering Texas. Show the commission terms and anything unknown."
- "Find reps for commercial LED lighting in Texas and compare their relevant experience."
- "Save this opportunity to my favorites." Sign in when prompted; saving does not submit an application.
- "Help me apply to this opportunity." Review the prepared application and confirm before it is submitted.

## Install and connect

This repository is a standalone Cursor plugin package. Marketplace availability depends on review; the existence of this repository does not mean it is approved.

For local testing in Cursor, copy this repository's contents (including `.cursor-plugin`) into `~/.cursor/plugins/local/zillasales`, then restart Cursor or run **Developer: Reload Window**. Open **Customize** and verify that the skills and MCP server appear. Local imports must be allowed by your organization. See [Cursor's plugin installation documentation](https://cursor.com/docs/plugins).

Grok Bot uses the same plugin ecosystem. Once available, install through its plugin interface; follow [Grok Bot's setup guide](https://cursor.com/docs/grok-bot/get-started) for account and client requirements. Do not install the same MCP server twice through both a plugin and a manual configuration.

For a client that supports a custom remote MCP server, use:

```json
{
  "mcpServers": {
    "zillasales": {
      "url": "https://zillasales.com/api/mcp/claude"
    }
  }
}
```

The `/claude` suffix is the existing OAuth-compatible transport endpoint, not a restriction on the client. It supports public tools without sign-in and an HTTP 401 OAuth challenge for account tools. The original OpenAI/Muse endpoints and packages remain separate.

When an account tool is requested, use the host's OAuth flow and sign in on ZillaSales. The server supports dynamic client registration, S256 PKCE and refresh-token rotation. No API key, password, fixed client secret or authorization header is included in this package. Disconnect using the host's connector controls; reconnect if authorization expires or is revoked.

## Reviewer test plan

See [TESTING.md](TESTING.md) for public smoke tests, optional account workflows, expected results and safety boundaries. Test both local component discovery and real tool calls in each target host before attesting that the plugin works in-app. Protocol tests alone do not establish host compatibility.

## Data and privacy

The skills invoke only the declared ZillaSales MCP server. The package runs no local scripts, hooks, installers or background processes. The hosted service receives tool arguments and, after OAuth consent, the account permissions needed for the requested action. It does not require the full conversation. Searches and profile/application content are processed by ZillaSales. Account records remain subject to the service retention and deletion policy. See the [privacy policy](https://zillasales.com/privacy#connected-assistants), [terms](https://zillasales.com/terms) and [developer documentation](https://zillasales.com/developers) for details.

## Pricing and scope

This MIT-licensed plugin is distributed free of charge. Public searches/calculations require no account. Private workflows require an appropriate account and remain subject to its permissions and service limits. The plugin cannot purchase subscriptions, reports, contact unlocks or credits. The host application may require its own subscription. Website services and their terms are separate from this package.

## Support

Use [ZillaSales support](https://zillasales.com/developers#support). If a tool reports a rate limit, wait for its retry interval; do not invent missing results. Report reproducible plugin issues in this repository without including credentials, private records or real birth details.

## License

The plugin files are MIT licensed. No hosted application code, database contents, Swiss Ephemeris binaries or calculation datasets are distributed here. Hosted services and their data remain subject to their own terms.
