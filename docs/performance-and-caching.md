# Performance and cache contracts

Reviewed against Next.js 16.4 on 13 October 2026. New recommended create-next-app projects enable Cache Components and Partial Prefetching. Existing applications require an inspection of version and configuration. Do not combine previous-model assumptions with current cache behaviour.

## Describe what may become stale

For each cached output record its owner, inputs, acceptable age, invalidation event and privacy classification. Public editorial content, stock availability and an account-specific permission result have different requirements. Test an update through every read layer, including client navigation and a distributed deployment.

The current model supports explicitly selected cacheable work through use cache. The [official caching guide](https://nextjs.org/docs/app/getting-started/caching) explains enabled flags and current APIs. Use the appropriate previous-model documentation for applications that have not migrated. Avoid placing private records in a broadly shared cache without a reviewed partitioning contract.

## Example decision table

| Output | Design question | Verification |
| --- | --- | --- |
| Public article | How soon must an edit appear? | Edit, invalidate and inspect a fresh request and navigation |
| Catalogue availability | Which system owns stock? | Simulate a stock change and delayed synchronisation |
| Account dashboard | Which fields belong to this user? | Test separate users, logout and permission changes |
| Search suggestions | Is a shared result acceptable? | Review personalisation inputs and expiry behaviour |

These are planning questions rather than universal cache settings. Choose settings only after the required behaviour is agreed.

## Measure the release

Inspect client bundle size, long tasks, image delivery, server timings and database latency. Streaming does not repair a repeatedly slow query. Use representative public and private journeys on intended devices. Set budgets and monitor regression after interface, tracking or integration changes.

Distributed self-hosting may need shared cache storage and coordinated invalidation. Document eviction, outage and recovery. An Edge function is not automatically closer to the database or compatible with every dependency. Verify runtime support, duration and streaming limits on the target platform. See [deployment guidance](deployment-and-maintenance.md) and [self-hosting documentation](https://nextjs.org/docs/app/guides/self-hosting).
