---
layout: default
---

# Cloud Tasks vs Cloud Pub/Sub (2/2)

<Transform scale="0.75">

| Feature | Cloud Tasks | Cloud Pub/Sub |
| --- | --- | --- |
| Task/message retention | 30 days | Up to 31 days |
| Max size of task/message | 1 MB | 10 MB |
| Max delivery rate | 500 qps per queue | No upper limit |
| Geographic availability | Regional | Global |
| Maximum push handler/subscriber processing duration | 30 minutes (HTTP)<br />10 minutes (App Engine Standard automatic scaling)<br />24 hours (App Engine Standard manual or basic scaling)<br />60 minutes (App Engine Flexible) | 10 minutes for push operations |
| Number of queues/subscriptions per project | 1,000/project, more available via quota increase request | 10,000/project |

</Transform>

<!--
https://cloud.google.com/tasks/docs/comp-pub-sub

https://cloud.google.com/pubsub/docs/choosing-pubsub-or-cloud-tasks

https://youtu.be/Q_airdHCuV8?si=SwJECVHzwirx9WM_&t=2254
-->
