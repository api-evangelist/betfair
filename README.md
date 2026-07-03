# Betfair (betfair)

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
