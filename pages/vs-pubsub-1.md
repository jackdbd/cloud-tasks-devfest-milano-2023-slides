---
layout: default
---

# Cloud Tasks vs Cloud Pub/Sub (1/2)

**TL;DR:** push queue, explicit invocation VS pull queue, implicit invocation

<Transform scale="0.75">

| Feature | **Cloud Tasks** | **Cloud Pub/Sub** |
| --- | --- | --- |
| At least once delivery | ✅ | ✅ |
| Configurable retries | ✅ | ✅ |
| Task creation deduplication | ✅ | ❌ |
| Scheduled delivery | ✅ | ❌ |
| Ordered delivery | ❌ | ✅ with ordering keys |
| Explicit rate controls | ✅ | ✅ Pull subscriber clients<br />can implement [flow control](https://cloud.google.com/pubsub/docs/pull?authuser=0#config) |
| Pull via API | ❌ | ✅ |
| Batch insert | ❌ | ✅ |
| Multiple handlers/subscribers per message | ❌ | ✅ |

</Transform>

<!--
https://cloud.google.com/tasks/docs/comp-pub-sub

Cloud Tasks supports only (?) push queues.
PubSub supports pull queues AND push queues.

Does your service know which service to call?

 - If yes, this is an explicit invocation => choose a push queue
 - If no, this is an implicit invocation => choose a pull queue

Cloud Tasks is aimed at explicit invocation where the publisher retains full control of execution. In particular, a publisher specifies an endpoint where each message is to be delivered.

Pub/Sub aims to decouple publishers of events and subscribers to those events. Publishers do not need to know anything about their subscribers. Therefore, Pub/Sub gives publishers no control over the delivery of the messages save for the guarantee of delivery. In this way, Pub/Sub supports implicit invocation: a publisher implicitly causes the subscribers to execute by publishing an event.

There is also Pub/Sub Lite, which supports only pull queues.

In Cloud Tasks, enqueued task order is preserved on best-effort basis

https://cloud.google.com/pubsub/docs/choosing-pubsub-or-cloud-tasks
-->
