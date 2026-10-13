# Choosing an application pattern

The workflows below are illustrative architecture choices, not a list of completed OzairWebs client projects. Each requires discovery and project-specific acceptance tests.

| Pattern | Boundary to decide before building | Useful acceptance check |
| --- | --- | --- |
| Multi-tenant SaaS | Tenant ownership and authorization enforced on every record operation | One tenant cannot read another tenant's data through a guessed identifier |
| CRM or customer portal | Which system owns contacts, permissions and workflow state | A revoked user loses record access without depending on hidden UI controls |
| Recruitment or job platform | Listing validation, moderation, expiry and candidate-data retention | Expired listings and private candidate records follow their agreed visibility rules |
| Booking application | Availability source, holds, time zones and cancellation rules | Concurrent requests cannot create conflicting confirmed bookings |
| Membership or subscription | Provider-confirmed billing state and entitlement transitions | A delayed or repeated webhook cannot grant duplicate or incorrect access |
| Marketplace | Seller scope, moderation, fulfilment and transaction responsibilities | A seller sees only their permitted records and has a defined dispute route |
| Internal reporting | Data freshness, export permissions and auditability | A restricted report stays restricted when downloaded or shared |
| Headless publishing | Draft preview, public content and cache invalidation | Draft content never appears publicly through a cache or preview link |
| Enterprise modernization | Integration contracts, migration sequencing and recovery | A failed dependency preserves a recoverable state and useful diagnostics |
| MVP | One complete journey with deliberate exclusions | A representative user completes the journey and understands failure states |

Start with a state diagram for the critical workflow and a short register of data owners. A booking page, payment callback and administrative dashboard should not make independent decisions about the same transaction. Prefer server-enforced rules and explicit transitions over duplicated client-side assumptions.

An operational plan is part of the architecture. Identify who can inspect a failure, retry a task, restore records and communicate an outage. For external APIs, document timeouts, retry limits, idempotency, version constraints and the meaning of a successful response. A vendor outage should not silently erase a user's completed work.

AI-assisted workflows add a separate uncertainty boundary. Retrieval can support a recommendation, but model output is not authorization. Keep tools narrowly scoped, validate proposed actions and require review for changes that affect money, access or public information. Test missing sources and ambiguous instructions as deliberately as successful answers.

Use [architecture and rendering](architecture-and-rendering.md), [security and authentication](security-and-authentication.md), [API integrations](api-and-ai-integrations.md) and the [decision register](../examples/README.md) to record choices. No reference architecture can establish suitability without the application's actual users, data and constraints.
