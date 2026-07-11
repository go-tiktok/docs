# go-tiktok

Pure-Go best-effort read client for public TikTok content.

!!! warning "Best-effort — read [Fragility & ToS](fragility.md) first"
    TikTok does not publish or support a public web API. This client calls the same internal endpoints TikTok's own website uses, and TikTok actively defends them.

A pure-Go, dependency-free, **best-effort** read client for public TikTok content, talking to TikTok's undocumented web JSON endpoints. The Go API is small and stable with an overridable base URL for network-free testing; the code builds correct requests and parses correct responses, but working end-to-end against live TikTok is not guaranteed.

## Install

```sh
go get github.com/go-tiktok/tiktok
```

## At a glance

- **CGO-free** (`CGO_ENABLED=0`), Go 1.26+ — builds for every 64-bit target.
- **Zero third-party dependencies** — standard library only.
- **Read-only** — this is a read client; it does not post or mutate.
- BSD-3-Clause.

See [Usage](usage.md) for a runnable example and [API reference](api.md) for the
full surface. The canonical, always-current reference is
[pkg.go.dev](https://pkg.go.dev/github.com/go-tiktok/tiktok).
