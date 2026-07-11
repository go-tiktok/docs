# Usage

```go
package main

import (
	"context"
	"fmt"

	"github.com/go-tiktok/tiktok"
)

func main() {
	c := tiktok.New(
		tiktok.WithMSToken("...msToken from a browser session..."),
		tiktok.WithSessionID("...sessionid cookie for authed reads..."),
	)

	// secUid is TikTok's opaque per-user id; obtain it once from a profile
	// page's embedded JSON, then pass it here.
	feed, err := c.UserPosts(context.Background(), "MS4wLjABAAAA...", 20, "0")
	if err != nil {
		panic(err)
	}
	for _, v := range feed.Videos {
		fmt.Printf("%s  %d likes  %s\n", v.Permalink, v.Likes, v.Description)
	}
	fmt.Printf("cursor=%s hasMore=%v\n", feed.Cursor, feed.HasMore)
}
```

An empty page (no videos, `HasMore == false`) is returned **without** error. A non-2xx status, an empty/anti-bot body, or malformed JSON returns a descriptive error including the HTTP status where relevant.

For the complete, always-current API — every type and field — see
[pkg.go.dev/github.com/go-tiktok/tiktok](https://pkg.go.dev/github.com/go-tiktok/tiktok).
