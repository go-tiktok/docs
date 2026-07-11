# Fragility & Terms of Service

!!! danger "Read this before depending on the library"
    TikTok does not publish or support a public web API. This client calls the same internal endpoints TikTok's own website uses, and TikTok actively defends them.

TikTok does **not** publish or support a public web API. This client calls the same internal endpoints TikTok's own website uses, and TikTok actively defends them. The endpoint shape, parameters, and response schema can change without notice, breaking this library at any time.

## What this means in practice

- Requests often need a valid **`msToken`** (query parameter and cookie) and a signed parameter (`X-Bogus` / `_signature`) that this library does **not** compute. Many reads additionally require a logged-in **`sessionid`** cookie.
- TikTok returns anti-bot responses — HTTP `403`/`429`, or an HTTP `200` with an empty or `{}` body — when it decides a request looks automated.
- The code builds correct requests and parses correct responses, but working end-to-end against live TikTok is not guaranteed.

## Your responsibility

Automated access to TikTok may violate its Terms of Service and/or
applicable law. **You are responsible for how you use this library** — use it
only for content and in ways you are authorised to access, and respect rate
limits. The maintainers cannot promise the underlying transport keeps working.
