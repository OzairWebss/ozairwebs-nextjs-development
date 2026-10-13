# Security and authentication review

Authentication establishes an identity. Authorization determines what that identity may do to a particular resource. A secure session does not establish permission to access another tenant's invoice. Treat browser-supplied identifiers and roles as untrusted, then enforce policy at the server boundary.

## Define the policy

Create a role/resource matrix for reads, edits, exports and administrative actions. Test denied paths as carefully as permitted ones. OAuth or social login should integrate with session expiry, revocation and account recovery; choose maintained libraries appropriate to the application. Use the [Next.js authentication guide](https://nextjs.org/docs/app/guides/authentication) as a starting point, with application-specific policy decisions documented separately.

Server Actions and Route Handlers must validate inputs and check authorization each time. Rate limits should protect high-risk endpoints without replacing permissions. Use transactions where a partial write would create an invalid state. Audit consequential actions with an actor, resource, operation and outcome, excluding credentials and sensitive payloads.

## Files, secrets and external tools

Validate uploads for size and permitted types, use safe storage names and access-controlled object retrieval, and inspect files as appropriate to the threat model. Avoid assuming an uploaded MIME type is trustworthy. Signed download links require bounded expiry and scoped access.

Keep API keys and session secrets out of browser bundles, public repositories and ordinary logs. Separate production and preview credentials. Rotate and revoke through an owned procedure. Prompt injection needs its own threat model when AI reads external documents or invokes tools: retrieved text must not redefine permissions or system instructions.

## Release checks

- [ ] Cross-user and cross-tenant access attempts are denied.
- [ ] Logout, expired sessions and revoked roles behave correctly.
- [ ] Mutations reject malformed or unauthorised requests.
- [ ] Webhook signatures and duplicate events are tested.
- [ ] Upload limits, private file retrieval and error output are reviewed.
- [ ] Dependencies and security notices are checked for the installed versions.
- [ ] Backups and a recoverable incident path are demonstrated.

The Next.js blog carried an upcoming upstream security-update notice at review time. Recheck the [official announcements](https://nextjs.org/blog) before using a release in production. This documentation is not a claim of independent penetration testing, certification or complete protection from compromise.
