# EveryInfra Router prompts

These examples are illustrative task requests, not live API output.

## Example 1

> I need public data about a set of businesses. Decide whether this is an EveryData or EverySearch task; inspect capabilities before proposing calls.

## Example 2

> Plan a workflow to find current product documentation and draft an email summary. Do not send the email or buy anything.

## Example 3

> This request combines text classification and a proxy. Identify the required products and permission boundaries without placing an order.

## Cleanup transition candidate — not live

> I want to normalize selected fields from an EveryData result. Determine whether the live runtime
> exposes a source-bound cleanup contract. If it does not, report the missing route and do not use
> general chat to simulate it.

> My cleanup submission was interrupted. Discover the live tools, then find the original task with
> the original idempotency key. Do not create a replacement solely because lookup returns 404.

> Route me to read-only field discovery for this EveryData source. Return inferred paths and types
> without example values, and stop before preview, activation or submission.

See [workflow acceptance criteria](../docs/workflow.md).
