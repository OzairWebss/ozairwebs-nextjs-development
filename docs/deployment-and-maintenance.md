# Deployment and maintenance runbook

Turbopack and framework development tooling can improve the build and debugging workflow, but development performance does not establish production reliability. Record the actual build configuration, reproduce errors against the installed version and review automated upgrade changes before release. The [16.4 announcement](https://nextjs.org/blog/next-16-4) describes current migration assistance; an agent-produced refactor still needs type, integration and journey checks.

Deployment decisions determine which framework features and recovery procedures are available. Compare Vercel, a supported Node.js service, Docker-based hosting and suitable managed platforms against runtime, data region, networking, request duration, cache and operating responsibilities. A static export is a different capability set from a full server deployment.

## Before the first release

Record the production/preview boundaries, secret owners, build command, required environment variables and external dependencies. Pin actual dependencies and retain the lockfile for a software project. Keep preview credentials separate and avoid copying production customer data into a public or casually shared environment.

Define build, type and test checks around the critical workflows. A payment callback, tenant permission or catalogue update needs an integration test rather than only a snapshot of a button. Review database migrations for concurrent access and compatibility with the previous application version.

## Cutover and rollback

Use a release record with version, schema change, owner and acceptance evidence. Inspect the deployed health, authenticated paths, uploads, webhooks and background queues. Record cache behaviour across multiple instances. A rollback plan must identify whether reverting code is safe with the new schema and whether new writes require reconciliation.

Store recoverable backups separately and restore into an isolated environment. Verify that records, permissions and important workflows function after restoration. Set recovery objectives with the business owner; do not infer them from a hosting provider's generic marketing promise.

## Ongoing operation

Monitor request errors, latency, queue age, dependency failures and critical user journeys. Alert on actionable thresholds with a named response owner. Define how provider outages, exhausted AI budgets and failed notifications reach a manual fallback. Redact logs and agree retention.

Review framework/security announcements after releases, and periodically test compatibility before upgrades. Next.js 16.4 was the stable version identified during this review, while a later security update was announced as upcoming. Do not freeze a long-term production recommendation to the review date.

Use the [official self-hosting guide](https://nextjs.org/docs/app/guides/self-hosting) for caching, instance coordination and deployment-specific concerns. This runbook is a planning resource; it does not deploy, monitor or certify an application automatically.
