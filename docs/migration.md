# Routing during the EveryAI cleanup transition

> Production advertises source-bound cleanup alongside the existing `everyinfra_chat` compatibility
> tool. Always confirm the two cleanup tools through live MCP discovery; discovery does not prove a
> particular account is eligible, activated or end-to-end tested.

## Routing rule

First decide whether the request is ordinary text processing or post-processing of an EveryData
result.

| Requested outcome | Route now | Route after verified cleanup launch |
| --- | --- | --- |
| Classify, extract, translate or summarize text supplied directly by the user | EveryAI through the live `everyinfra_chat` contract, when authorized. | Follow the dated compatibility notice. Cleanup is not an automatic replacement for arbitrary supplied text. |
| Normalize, translate, classify, extract or summarize a verified EveryData result | Use the live cleanup MCP or REST contract after entitlement, source ownership/version and recipe discovery. Do not send the result through generic chat. | Follow the same source-bound contract and any dated compatibility notice. |
| Deterministic normalization | Use ordinary code when it is sufficient. | Continue to prefer deterministic processing where it gives the requested result. |
| Retrieve or verify current information | EverySearch or Research. | Cleanup remains processing, not retrieval or evidence. |

The planned first cleanup trial is conditional rather than unlimited: verified net settled recharge
principal of at least CNY 500.00, explicit activation, 30 days, 1,000 successful units per UTC day,
30,000 successful units total, 5 execute attempts per minute per account and 5 concurrent units.
These values are an approved implementation contract, not evidence that the feature or production
capacity is available.

## Live 15-operation route

Production has two tools. Re-read MCP `tools/list` and their current `inputSchema` before execution.

| Tool | Operations |
| --- | --- |
| `everyinfra_data_cleanup_read` | `get_entitlement`, `get_source`, `get_source_fields`, `list_recipes`, `preview`, `list_jobs`, `find_job`, `get_job`, `list_units`, `get_result`, `export` |
| `everyinfra_data_cleanup_action` | `activate`, `submit`, `cancel`, `delete_result` |

Routing sequence: discover tools → inspect entitlement → discover source
version, selectable fields and fixed recipes → preview → explicitly activate when required →
explicitly submit. Reads do not authorize mutations. After refresh or an unknown submit response,
use `list_jobs` or `find_job` with the original idempotency key, then inspect the original job,
units and results. A 404 is not proof that the submit was never accepted, so do not automatically
switch keys or transports.

## Discovery and failure behavior

1. Read the production MCP `tools/list` or public OpenAPI document at execution time.
2. If cleanup is absent in the current host, report the unavailable route and keep any proposed
   payload out of the response.
3. If cleanup is advertised, inspect the current entitlement, source and recipe schemas before
   previewing or submitting anything.
4. Activation and execution are separate mutations. A read or preview does not authorize either.
5. An unknown execution result stays attached to the original idempotent operation; do not switch
   transports or fall back to general chat to repeat it.

The existing general chat endpoint remains a compatibility interface until a dated retirement
notice. A planned 30-day customer migration period is separate from an account's 30-day cleanup
trial. Do not invent start or cutoff dates.

## Delivery layers

- **Skill:** routing and workflow instructions. Updating it changes agent guidance only.
- **MCP:** runtime tools and schemas. Availability is established by live discovery and execution.
- **Plugin:** an installable distribution package that can contain Skills, MCP metadata, or both.
  Installation, source publication and marketplace listing are separate from service enablement.

Return to the [Router overview](../README.md) or [workflow](workflow.md).
