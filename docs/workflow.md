# EveryInfra Router workflow and acceptance criteria

## Intended outcome

A routing decision with one product per operation, the discovery step, required inputs, side effects and any blocked prerequisite. A plan is not proof that the later operations have succeeded.

## Text processing

Route cleaning, labeling, extraction and summaries, including records collected with EveryData, to
EveryAI (`everyinfra_chat`), which is free for accounts that have topped up. The former data
cleanup tools were retired on 2026-10-09.

## Execution contract

1. Describe the requested result, destination and permitted side effects.
2. Map each operation to a product: EveryData for structured public data, EverySearch for web retrieval, EveryAI for text processing, EverySolve for authorized challenges, EveryMail for email, EveryNumber for numbers, or EveryProxy for traffic.
3. Use live MCP discovery for the four MCP-enabled products; inspect the free REST catalog for the other three.
4. Present the smallest execution plan, with required parameters and separate approval points.
5. Execute only authorized operations and report results, billing evidence and unfinished external actions separately.

## Failure handling

If discovery or catalog access fails, stop before a paid action. Read required fields from the current schema instead of copying a remembered payload. Report unavailable capabilities and denied account scopes as distinct conditions. Do not broaden keys, repeatedly retry a permanent error or substitute an unrelated mechanism without disclosure.

- Installing the router does not install the other nine skills or configure their services.
- A shared API key does not imply that every product scope is enabled.
- A product appearing in a catalog is not evidence that an account can complete a paid operation.

## Worked request boundaries

### Scenario 1

> I need public data about a set of businesses. Decide whether this is an EveryData or EverySearch task; inspect capabilities before proposing calls.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.

### Scenario 2

> Plan a workflow to find current product documentation and draft an email summary. Do not send the email or buy anything.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.

### Scenario 3

> This request combines text classification and a proxy. Identify the required products and permission boundaries without placing an order.

Accepted behavior: preserve the stated scope; discover the required contract and stop at the explicit no-action boundary. Any broader operation requires new authority.


These are illustrative prompts, not captured API responses or claims of successful live execution. They deliberately avoid guessed JSON payloads and fabricated prices. See [prompt acceptance fixtures](../examples/acceptance.json) for the offline safety assertions.

## Result review

A routing decision with one product per operation, the discovery step, required inputs, side effects and any blocked prerequisite. A plan is not proof that the later operations have succeeded.

Check original results rather than relying on the agent's summary alone. Preserve response status and evidence only to the extent safe; redact personal or secret fields. If billing is absent from the response, say it is not observable there rather than inferring a charge from HTTP success.

## Related decision

Choose Router to decide which product fits. Choose a product skill when the service is already known. Choose Research for an evidence-backed conclusion or Data Export for a bounded file-delivery workflow.

Return to [README](../README.md) or [setup](setup.md).
