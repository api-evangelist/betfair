# Betfair (betfair)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Betfair operates the world's largest online betting exchange, where customers back and lay outcomes against each other rather than against a bookmaker. The Betfair Exchange API (API-NG) gives automated clients programmatic access to the exchange - navigating markets, retrieving live prices, placing and managing bets, and reading account state. It is exposed as lightweight JSON-RPC and REST operations over HTTPS under `https://api.betfair.com/exchange` (the Betting, Accounts, and Heartbeat APIs), with a separate real-time Exchange Stream API delivered over a raw SSL/TCP socket (CRLF-delimited JSON, **not** WebSocket) for low-latency market and order updates. A Historic Data API and a licensed Vendor (affiliate) API round out the platform. Authentication combines an Application Key with a session token (ssoid) obtained from Betfair's identity SSO login.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/betfair/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/betfair/refs/heads/main/apis.yml)

## Tags

- Betting Exchange
- Sports Betting
- Wagering
- Trading
- Market Data
- JSON-RPC
- Streaming

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## APIs

### Betfair Betting API

The core exchange API (SportsAPING). Navigate markets (`listEventTypes`, `listCompetitions`, `listEvents`, `listMarketCatalogue`), read live prices and depth (`listMarketBook`, `listRunnerBook`), and place, cancel, replace, and update bets (`placeOrders`, `cancelOrders`, `replaceOrders`, `updateOrders`) plus read current and cleared orders. Available as JSON-RPC (`/betting/json-rpc/v1`) and per-operation REST (`/betting/rest/v1.0/`).

- **Human URL:** [https://developer.betfair.com/en/get-started/](https://developer.betfair.com/en/get-started/)
- **Base URL:** `https://api.betfair.com/exchange/betting`

#### Tags

- Betting
- Markets
- Orders
- Prices

#### Properties

- [Documentation](https://developer.betfair.com/exchange-api/)
- [API Reference](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Betting+API)
- [OpenAPI](openapi/betfair-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/betfair.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/betfair.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Betfair Accounts API

Account-level operations (AccountAPING) - retrieve account funds and details (`getAccountFunds`, `getAccountDetails`), read the account statement (`getAccountStatement`), list currency rates, and manage developer application keys and application subscription tokens. JSON-RPC (`/account/json-rpc/v1`) and REST (`/account/rest/v1.0/`).

- **Human URL:** [https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Accounts+API](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Accounts+API)
- **Base URL:** `https://api.betfair.com/exchange/account`

#### Tags

- Accounts
- Funds
- Statement

#### Properties

- [API Reference](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Accounts+API)
- [OpenAPI](openapi/betfair-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/betfair.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/betfair.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Betfair Heartbeat API

A "dead man's switch" (HeartbeatAPING) - the client calls `heartbeat` on an interval (10-300s preference); if Betfair stops receiving heartbeats it will automatically cancel the client's unmatched bets, protecting an automated trader against a crashed or disconnected process. JSON-RPC (`/heartbeat/json-rpc/v1`) and REST (`/heartbeat/rest/v1.0/`).

- **Human URL:** [https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Heartbeat+API](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Heartbeat+API)
- **Base URL:** `https://api.betfair.com/exchange/heartbeat`

#### Tags

- Heartbeat
- Risk
- Dead Mans Switch

#### Properties

- [API Reference](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Heartbeat+API)
- [OpenAPI](openapi/betfair-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/betfair.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/betfair.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Betfair Exchange Stream API

Low-latency, subscription-based push of market and order changes over a persistent raw SSL/TCP socket to `stream-api.betfair.com:443`. The protocol is CRLF-delimited JSON (one JSON message per line) - **NOT WebSocket**; attempted WebSocket connections are refused. Clients authenticate then send `marketSubscription` / `orderSubscription` requests and receive market change (`mcm`) and order change (`ocm`) messages plus `connection`, `status`, and `heartbeat` frames.

- **Human URL:** [https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Exchange+Stream+API](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Exchange+Stream+API)
- **Base URL:** `tcp+ssl://stream-api.betfair.com:443`

#### Tags

- Streaming
- Real Time
- Market Data
- TCP

#### Properties

- [Documentation](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Exchange+Stream+API)
- [Source Code](https://github.com/betfair/stream-api-sample-code)
- [AsyncAPI](asyncapi/betfair-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/v2.6.0)

### Betfair Historic Data API

Programmatic access to purchased historical exchange market data. REST POST operations (`GetMyData`, `GetCollectionOptions`, `GetAdvBasketDataSize`, `DownloadListOfFiles`, `DownloadFile`) authenticated with the same session token (ssoid). Data packages must first be purchased via historicdata.betfair.com.

- **Human URL:** [https://historicdata.betfair.com/](https://historicdata.betfair.com/)
- **Base URL:** `https://historicdata.betfair.com/api`

#### Tags

- Historical Data
- Downloads
- Market Data

#### Properties

- [Documentation](https://developer.betfair.com/historical-data-services-api/)
- [Specification](https://historicdata.betfair.com/Betfair-Historical-Data-Feed-Specification.pdf)
- [OpenAPI](openapi/betfair-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Betfair Vendor API

The Web Vendor Facility for licensed software vendors building web-based betting applications. Uses an OAuth2-style authorization flow so a vendor's web application can obtain access and refresh tokens and act on a Betfair customer's behalf, with the vendor able to charge subscriptions via application subscription tokens.

- **Human URL:** [https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Web+Vendor+Facility](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Web+Vendor+Facility)
- **Base URL:** `https://identitysso.betfair.com`

#### Tags

- Vendor
- Affiliate
- OAuth2
- Web Apps

#### Properties

- [Documentation](https://docs.developer.betfair.com/display/1smk3cen4v3lu3yomq5qye0ni/Web+Vendor+Facility)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/betfair)
- [Website](https://www.betfair.com)
- [Documentation](https://developer.betfair.com/)
- [Plans](plans/betfair-plans-pricing.yml)
- [Rate Limits](rate-limits/betfair-rate-limits.yml)
- [Fin Ops](finops/betfair-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
