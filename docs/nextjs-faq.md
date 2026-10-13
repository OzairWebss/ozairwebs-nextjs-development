# Next.js commissioning FAQ

## When is WordPress a better choice?

An editor-led company site with ordinary publishing needs may benefit from WordPress's established authoring interface and extension ecosystem. Compare the editorial workflow, custom business logic and operating team. Next.js adds value when the application needs integration or interaction patterns that justify a custom architecture, rather than because a framework is fashionable.

## When is Shopify a better commerce choice?

A standard storefront can benefit from Shopify's managed commerce services. Evaluate catalogue rules, checkout constraints, recurring costs and integration access. A custom storefront may solve a distinctive experience or workflow but introduces engineering and maintenance responsibilities. Document that trade-off before replacing a working platform.

## What should an MVP contain?

The smallest useful workflow with proportionate protection and recovery. Reducing scope does not remove the need for authentication, permission checks and handling invalid input. Agree the launch audience, excluded features and operational risks. A prototype using mock data is not evidence that production integrations work.

## Does TypeScript validate incoming API data?

TypeScript helps define and check code contracts during development. Untrusted runtime requests still require validation, and permitted field shapes still need business-rule checks. Treat server endpoints and tool arguments as trust boundaries regardless of compile-time types.

## Can an AI assistant operate without review?

Read-only support within approved sources is a different risk from sending messages or changing financial records. The application must enforce allowed tools and record permissions. Sensitive writes need the agreed approval boundary. Prompt text cannot replace those checks or authorize its own actions.

## What makes a useful handover?

Repository/account ownership, deployment configuration, dependency record, permission model, test evidence, backup restoration instructions and known limitations. Identify who operates queues and dependencies after launch. Maintenance should have an agreed boundary and escalation route.

## Is a version number proof that advice is current?

No. Inspect the installed release, configuration and current security notices. Next.js caching models have changed, and features may depend on configuration or hosting. Follow the [references](references.md) and verify before adopting a recommendation in an existing application.
