---
layout: default
---

# Notifications with SSE

<Transform scale="0.85">

We can implement a [Cloud Run service that sends server-sent events (SSE)](https://cloud.google.com/blog/products/serverless/cloud-run-now-supports-http-grpc-server-streaming) and receive those events on the frontend using an [EventSource](https://developer.mozilla.org/docs/Web/API/EventSource). Unfortunately, on serverless platforms SSE can be expensive and unreliable.

**Pros:**

- It's just HTTP, not a different protocol.
- Handles disconnect/reconnect and missed messages automatically.
- No need for special handshaking.

**Cons:**

- Unidirectional, **server-to-client** data stream.
- The Cloud Run service must be configured with [CPU always allocated (i.e. never idle)](https://www.googlecloudcommunity.com/gc/Serverless/Server-Sent-Events-on-Cloud-Run-not-working/td-p/609896).
- Network proxies and other hardware/software can [totally break SSE](https://dev.to/miketalbot/server-sent-events-are-still-not-production-ready-after-a-decade-a-lesson-for-me-a-warning-for-you-2gie).
- When not used over HTTP/2, SSE suffers from a [limitation to the maximum number of open connections](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events), which can be especially painful when opening multiple tabs, as the limit is per browser and is set to a very low number (6).

[SSE doesn't work well on Cloudflare Workers either](https://community.cloudflare.com/t/workers-server-sent-events-server-push/184219/2).

</Transform>

<!--
SSE data stream is UTF-8 encoded.
The SSE server needs to send this HTTP response header: Content-Type: text/event-stream

With CPU always allocated you obviously pay more.
https://cloud.google.com/run/docs/configuring/cpu-allocation
I'm not entirely sure whether "CPU idle" means the exact same thing as "CPU throttled".

We often use HTTP/1.1 in a Cloud Run service, since the HTTP/2 connection ends at the Google Frontend level. Our Cloud Run service is not directly deployed on the internet, but it's always behind GFE. Any internal service that must publish itself externally uses the GFE as a smart reverse-proxy frontend. The GFE provides public IP address hosting of its public DNS name, DoS protection, and TLS termination.
https://cloud.google.com/docs/security/infrastructure/design#google-frontend-service
-->
