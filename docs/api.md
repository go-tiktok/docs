# API reference

Source-verified against [`go-tiktok/tiktok`](https://github.com/go-tiktok/tiktok). The
authoritative, versioned reference is
[pkg.go.dev/github.com/go-tiktok/tiktok](https://pkg.go.dev/github.com/go-tiktok/tiktok).

## Constructor & methods

| Symbol | Purpose |
|---|---|
| `New(...Option) *Client` | Construct a client. |
| `(*Client).UserPosts(ctx, secUid, count, cursor) (*UserFeed, error)` | Fetch a user's recent videos via the web `item_list` API. |

## Options

Functional options passed to `New`:

| Option | Purpose |
|---|---|
| `WithMSToken(t)` | Send the `msToken` query parameter / cookie. |
| `WithSessionID(s)` | Send a `sessionid` cookie for authenticated reads. |
| `WithBaseURL(url)` | Override the request origin (useful for network-free tests). |
| `WithHTTPClient(*http.Client)` | Supply a custom HTTP client (timeouts, proxy, transport). |
| `WithUserAgent(ua)` | Set the `User-Agent` header. |

## Result types

| Type | Purpose |
|---|---|
| `Video` | A single video (`Permalink`, `Likes`, `Description`, …). |
| `UserFeed` | A page of `Videos` plus `Cursor` and `HasMore`. |

!!! note
    This table is a map, not the contract. Field-level details live in the
    [package reference](https://pkg.go.dev/github.com/go-tiktok/tiktok) and the
    repository's `README`.
