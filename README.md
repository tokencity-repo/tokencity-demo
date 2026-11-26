# Token City

Blockchain-powered social platform. A vision for connected communities, creative ownership, and shared value.

Token City brings social profiles, interest-based communities, creator content, messaging, events, and blockchain-backed contribution records into one platform. Members connect, create, build communities, and receive recognition or funded benefits for verified participation. Users control their identity, creations, and what they share.

**Token City Connect** is an optional device and location-enabled community participation network. It can connect consenting members with nearby communities, shared activities, and approved event or creator partners.

## Outcomes

- Meaningful connections around shared interests
- Active communities built through creativity and collaboration
- Member-controlled identity, content sharing, and community participation
- Clear membership benefits and recognition for verified contributions
- Safe interaction with friends, creators, and nearby consenting participants
- Community-funded activities, transparent contribution records, and verified benefits

## Who participates

The member stays at the center. Friends and communities are optional social layers. Members choose which interests, creations, achievements, and activities to share. Social sharing does not include private messages, precise location, identity documents, or restricted account information.

Creators manage content, collaborations, and audience access. Community managers handle membership, programs, moderation, messaging, and disputes. Sponsors fund activities and benefits without unrestricted access to member data. Event and partner organizations manage programs, staff, and delivery responsibility. Every participant sees and does only what they are authorized to do.

## Connected devices

Permitted participation signals can come from optional wearables, mobile device frameworks, event check-in equipment, and dedicated IoT hardware. Devices can support community events and shared activities; core social participation does not require hardware. Device data is supporting evidence, not automatic proof of contribution. Missing, stale, or uncertain readings are data-quality conditions.

Early hardware can use the Nordic Semiconductor nRF5 Series (nRF52832, nRF52833, nRF52840), plus STM32 and Arduino BLE. Devices handle sensing, local buffering, Bluetooth Low Energy, identity, and secure sync. Approved edge gateways may extend coverage later and do not receive restricted member data.

```text
Device → BLE / gateway → authenticated ingestion → quality checks
  → secure participation store → community programs → member and community apps
```

## Token City Connect

Approved wearables (watch, ring, pendant, participation band, or similar) can support an explicit event check-in or activity request. AI may suggest relevant communities or flag unusual participation signals. A suggestion or device signal is a request for review, not confirmed participation or reward authorization.

Location is event-scoped and minimum-necessary. Nearby members or activities may be matched within about 100–500 meters where density, consent, safety rules, and local law allow it. Members receive a short invitation, approximate location, and an accept or decline action. Participation is voluntary. Reports, unsafe interactions, and suspicious invitations route to authorized moderation or event partners.

```text
Activity request or check-in signal → authenticate → locate → orchestrate
  → confirm when appropriate → nearby members and event routing
  → verify participation → close → reward only after verification
```

The member app shows a simple path: Requested, Discovering, Matching, Invitation Accepted, Activity In Progress, Verification, Closed. Server-side event states include Detected, Requested, Confirmation Pending, Active, Matching, Invitation Accepted, Partner Review Requested, Activity In Progress, Verification Pending, Resolved, Cancelled, and Closed. Clients cannot invent completed participation or create a reward.

## Experience and backend

The web app can use SvelteKit and TypeScript. Native or mobile components handle Bluetooth, notifications, and device permissions. The interface separates social content, participation evidence, AI suggestions, and verified community records. Users control what is shared.

Go services enforce identity, consent, enrollment, community programs, device registration, participation signals, messaging, benefits, and partner integrations. PostgreSQL holds operational data. Controlled object storage holds restricted evidence. Partner APIs connect community, creator, and event systems where appropriate. A reward outage must not block social feeds, community communication, or access to member content.

## AI

AI organizes information, summarizes permitted community content, explains approved program instructions, recommends relevant communities, and routes questions. It can return “insufficient information.” It does not change membership rights, override moderators, release community funds, or authorize rewards. Abuse and participation-anomaly detection produces a review signal and escalation level. False positives and false negatives are quality metrics. An AI event alone never authorizes payment.

## Benefits and rewards

Communities, creators, and sponsors fund eligible programs, including from community revenue where agreed. Members do not buy, deposit, invest, or trade reward units. The app shows a benefit balance. Credits are closed-loop entitlements: not sold to users, not transferred between members, not cash by default, and not listed on an exchange. Legal treatment is reviewed per market and sponsor before launch.

A credit is issued once, against a unique approved contribution, community milestone, or participation event, and only while the funded allocation covers its maximum redemption liability. Value is fixed or bounded in advance. Reward terms are defined before the activity begins.

```text
Program budget → eligible activity → review → authorization
  → benefit balance → approved partner → fulfillment → sponsor settlement
```

Community contribution rewards require a full activity timeline: signed timestamps, authenticated submissions, location consistency only when relevant and consented, acceptance and completion, protected messages, and member, community-manager, or partner confirmation when available. Decisions are Verified, Partially Verified, Rejected, or Manual Review Required. The ledger stores the accounting result and non-sensitive references only.

Reward states: Potential, Under Review, Approved, Processing, Available, Reserved, Redeemed.

## Permissioned ledger

Hyperledger Fabric with Go chaincode is a proposed internal blockchain ledger for authorized community reward movements: duplicate prevention, program limits, reservation, redemption, release, and correction. It records approved accounting outcomes; it does not judge social content, grant content rights, or store private member information.

Contract operations: `CreateProgram`, `AmendProgram`, `FundAllocation`, `IssueAward`, `ReserveAward`, `ConfirmRedemption`, `ReleaseReservation`, `RecordCorrection`. Writes are idempotent. Corrections are new linked entries. Issued redemption liability cannot exceed the funded allocation.

Use Fabric in production only if multiple organizations need a shared, independently verifiable record and the audit benefit outweighs the operating cost. Until peers, joint approval, finance reconciliation, and a consortium agreement exist, the ledger is a proposed design. A single-operator pilot should compare it with a conventional audited database first.

## Privacy and safety

Encrypt data in transit and at rest. Use OIDC, server-side authorization, role-based access, staff MFA, key management, tenant isolation, audit, and retention controls. Precise location is purpose-limited and expires with the event. Controls cover harassment, spam, impersonation, spoofed participation or location, replay, account takeover, stalking, and reward fraud. Users can manage community participation, content visibility, blocking, reporting, and location permission.

## Technology baseline

| Area | Technology |
| --- | --- |
| Web | SvelteKit + TypeScript |
| Backend | Go |
| Operational data | PostgreSQL |
| Evidence and attachments | Controlled object storage |
| Identity | OIDC, RBAC, consent, staff MFA |
| Interoperability | Community, creator, and event partner APIs |
| IoT | nRF5 Series, STM32, Arduino BLE; BLE and Wi-Fi |
| AI | Backend-managed assistance |
| Observability | OpenTelemetry |
| Rewards | Go reward service; Hyperledger Fabric and Go chaincode as proposed |
| Reward views | PostgreSQL projections of committed ledger events |

Build in dependency order: identity and consent, social profiles and communities, devices and integrations, participation validation, community programs, AI assistance, moderation responsibility, sponsor funding, then authorized reward accounting. Social participation continues if the reward ledger is unavailable.

Success is meaningful connections, active communities, member retention, original creations, verified contributions, benefit use, and long-term community trust. Token City is a blockchain-powered social platform built around community participation and member-controlled identity.
