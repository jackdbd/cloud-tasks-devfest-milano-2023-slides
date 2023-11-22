---
layout: default
---

# Notifications with WebSockets

<Transform scale="0.85">

[Cloud Run supports WebSockets](https://cloud.google.com/run/docs/triggering/websockets), but it can be [really expensive](https://socket.io/).

**Pros:**

- Bidirectional data stream.

**Cons:**

- It's not HTTP, it's a different protocol.
- The Cloud Run service must be configured with CPU always allocated.
- We need to handle request timeouts and client reconnects (or use a library that does it for us, like [Socket.IO](https://socket.io/) or <Anchor href="https://github.com/taoensso/sente" text="Sente" />).

AWS has the <Anchor href="https://github.com/aws/aws-iot-device-sdk-js-v2" text="IoT Device SDK" />, which allows MQTT over WSS (Websockets Secure). [Google killed](https://killedbygoogle.com/) its IoT Core product.

A single Node.js server running Socket.IO could manage [55k connections](https://socket.io/docs/v4/performance-tuning/).

</Transform>

<!--
Websockets with Cloud Run
https://youtu.be/g6i-mb_3iWM?si=SN7x2Yyh10WN76C9

WebSocket server on Compute Engine
https://cloud.google.com/pubsub/docs/streaming-cloud-pub-sub-messages-over-websockets
-->
