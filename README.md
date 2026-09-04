# EveryInfra Router — Choose the right infrastructure API for an agent task

![EveryInfra H2 shared-base mark](plugins/everyinfra-router/assets/logo.svg)

[简体中文](README.zh-CN.md) · [Setup](docs/setup.md) · [Workflow](docs/workflow.md) · [Prompts](examples/prompts.md) · [Capability reference](docs/reference.md) · [API documentation](https://api.everyinfra.com/docs)

EveryInfra Router is a standalone agent skill for selecting the right EveryInfra infrastructure API. It maps a requested outcome to structured data, web search, AI, authorized captcha, email, phone-number or proxy workflows, then checks the applicable MCP or REST contract before execution.

An agent request such as “collect public information and notify my team” is not one API operation. It mixes data access, research and an external message. EveryInfra Router separates these decisions, selects the relevant product contract and identifies the point where a paid call or an outgoing action needs approval.

Use this skill when you know the outcome but not the product to call. It is a dispatch guide, not a replacement for a data source, an email transport or a proxy client.

## What you can do

- Distinguish a structured platform-data request from a current-web search.
- Plan a multi-product workflow without treating permission to research as permission to send.
- Explain which part of a request is blocked by a missing capability, scope or configuration.

## Quick start

This is a standalone, one-skill **MCP and REST routing** package, not a new API service. It requires a compatible agent host and the configured access described in [setup](docs/setup.md). Local package validation does not establish live API availability.

Install the source repository in Codex after reviewing its contents. These commands add a GitHub-backed repository catalog, not an official marketplace endorsement:

```bash
codex plugin marketplace add everyinfra/everyinfra-router-plugin
codex plugin add everyinfra-router@everyinfra-router-plugin
```

For a local checkout, replace the first command's source with `.`. [Setup](docs/setup.md) also covers Claude Code and the separate service connection.

Configure access once, then ask:

> I need public data about a set of businesses. Decide whether this is an EveryData or EverySearch task; inspect capabilities before proposing calls.

This initial prompt is scoped to inspection or preparation. Review any paid operation or external side effect before proceeding. Claude Code instructions and Cursor packaging boundaries are in [setup](docs/setup.md).

## How the workflow works

1. Describe the requested result, destination and permitted side effects.
2. Map each operation to a product: EveryData for structured public data, EverySearch for web retrieval, EveryAI for text processing, EverySolve for authorized challenges, EveryMail for email, EveryNumber for numbers, or EveryProxy for traffic.
3. Use live MCP discovery for the four MCP-enabled products; inspect the free REST catalog for the other three.
4. Present the smallest execution plan, with required parameters and separate approval points.
5. Execute only authorized operations and report results, billing evidence and unfinished external actions separately.

### What a useful result contains

A routing decision with one product per operation, the discovery step, required inputs, side effects and any blocked prerequisite. A plan is not proof that the later operations have succeeded.

## When to use this skill

Choose Router to decide which product fits. Choose a product skill when the service is already known. Choose Research for an evidence-backed conclusion or Data Export for a bounded file-delivery workflow.

## Limits and safety

- Installing the router does not install the other nine skills or configure their services.
- A shared API key does not imply that every product scope is enabled.
- A product appearing in a catalog is not evidence that an account can complete a paid operation.

The package contains one skill and does not grant permissions or register a duplicate MCP connection. Never put credentials in prompts, checked-in files, screenshots or shared logs. Discovery, API execution, billing and a final external result are separate states. See [security](SECURITY.md).

## Frequently asked questions

### Does this run every product automatically?

No. It separates intent, discovery and execution. Sending a message, allocating a paid resource or delivering credentials still requires the relevant authority.

### Is a second plugin required?

The router instructions are self-contained. Executing a chosen service requires the corresponding configured MCP or REST access, not another repository checkout.

### What happens if an API scope is missing?

The skill reports the denied scope or configuration. It must not broaden permissions or substitute a different service silently.

## Validate and contribute

```bash
python3 scripts/validate.py
```

This offline check validates packaging, local documentation links, the single-skill boundary, metadata and fixtures. It does not send messages, allocate resources or verify a production account. [Contribution guidance](CONTRIBUTING.md) and [the release checklist](RELEASING.md) describe the remaining checks.

Source publication, tagged releases, official marketplace acceptance and live service verification are separate milestones. Maintained by [EveryInfra](https://everyinfra.com). Licensed under [Apache-2.0](LICENSE).
