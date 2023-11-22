---
layout: default
---

# Cloud Tasks vs Cloud Pub/Sub (1/2)

<Transform scale="0.75">

| Feature | Cloud Tasks | Cloud Pub/Sub |
| --- | --- | --- |
| At least once delivery | Yes | Yes |
| Configurable retries | Yes | Yes |
| Task creation deduplication | Yes | No |
| Scheduled delivery | Yes | No |
| Ordered delivery | No | Yes with ordering keys |
| Explicit rate controls | Yes | Pull subscriber clients can implement [flow control](https://cloud.google.com/pubsub/docs/pull?authuser=0#config) |
| Pull via API | No | Yes |
| Batch insert | No | Yes |
| Multiple handlers/subscribers per message | No | Yes |

</Transform>

<!--
https://cloud.google.com/tasks/docs/comp-pub-sub

Enqueued task order is preserved on best-effort basis

https://cloud.google.com/pubsub/docs/choosing-pubsub-or-cloud-tasks

https://youtu.be/Q_airdHCuV8?si=SwJECVHzwirx9WM_&t=2254
-->
