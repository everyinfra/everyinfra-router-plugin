# EveryInfra Router: capability reference and evidence

EveryInfra Router is a standalone agent skill for selecting the right EveryInfra infrastructure API. It maps a requested outcome to structured data, web search, AI, authorized captcha, email, phone-number or proxy workflows, then checks the applicable MCP or REST contract before execution.

## Identity

- Publisher: [EveryInfra](https://everyinfra.com).
- Organization: [everyinfra on GitHub](https://github.com/everyinfra).
- Source repository: [everyinfra/everyinfra-router-plugin](https://github.com/everyinfra/everyinfra-router-plugin).
- Plugin identifier: `everyinfra-router`. Skill identifier: `everyinfra`.
- Package type: one standalone agent skill, not a separate API server or account permission boundary.
- Interface used by the skill: `mixed`. Mail, Number and Proxy workflows remain REST-only in these packages.

## Task and result

Use this skill when you know the outcome but not the product to call. It is a dispatch guide, not a replacement for a data source, an email transport or a proxy client.

A routing decision with one product per operation, the discovery step, required inputs, side effects and any blocked prerequisite. A plan is not proof that the later operations have succeeded.

## Preconditions

Use a compatible agent host and the service access described in [setup](setup.md). The live tool schema or REST catalog determines required inputs, supported actions, availability, limits and any exposed price. Do not infer universal platform coverage from a product name.

## Evidence behind the description

- The [packaged skill](../plugins/everyinfra-router/skills/everyinfra/SKILL.md) defines the workflow and authority boundaries.
- The [plugin manifest](../plugins/everyinfra-router/.codex-plugin/plugin.json) declares package identity, assets and skill path. It does not automatically register a service connection.
- [Workflow acceptance criteria](workflow.md) define the expected output and failures. Examples are illustrative, not paid API test results.
- [Source metadata](../repository-metadata.json) records the original reviewed skill commit and intended repository metadata.
- [Current API documentation](https://api.everyinfra.com/docs) is the public service reference. Runtime discovery remains authoritative when an inventory, field or model changes.

## Scope distinctions

Choose Router to decide which product fits. Choose a product skill when the service is already known. Choose Research for an evidence-backed conclusion or Data Export for a bounded file-delivery workflow.

No benchmark, uptime guarantee, universal availability, official marketplace approval or account-ban probability is asserted by this reference. Local package validation checks structure; production service behavior requires its own authorized verification.

Maintainer: EveryInfra. Documentation scope reviewed on 2026-09-04; this date is not a live API availability timestamp. [Return to overview](../README.md).
