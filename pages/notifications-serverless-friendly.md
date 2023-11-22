---
layout: default
---

# Serverless-friendly notifications

<Transform scale="0.85">

## Firestore

- Real-time updates available only in Firestore in [Native mode](https://cloud.google.com/datastore/docs/firestore-or-datastore)
- Create a [snapshot listener](https://firebase.google.com/docs/firestore/query-data/listen) on the client
- Define [security rules](https://cloud.google.com/firestore/docs/security/get-started) to restrict client-side access to the database

## Firebase Cloud Messages (FCM)

- Push notifications via the browser [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API)

## Third-party services

- AWS SES, SendGrid, Mailgun, Postmark, etc (email)
- OneSignal, PushEngage, ntfy, etc (push notifications)
- Ably, PubNub, Pusher, etc (SSE, WebSockets)
- Twilio, AWS Pinpoint, etc (SMS)
- Telegram Bot API, Slack, WhatsApp API, etc

</Transform>

<!--
-->
