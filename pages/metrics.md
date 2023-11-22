---
layout: default
---

# Metrics

<Transform scale="0.85">

Setup monitoring and alerting. E.g. queue depth over threashold.

https://cloud.google.com/tasks/docs/dual-overview#metrics

Queue overload and target overload.

The recommended defense is the same 500/50/5 pattern suggested for queue overload: if a queue dispatches more than 500 TPS, increase traffic triggered by a queue by no more than 50% every 5 minutes.

https://cloud.google.com/tasks/docs/manage-cloud-task-scaling

This article suggests 4 metrics about your tasks you should monitor.

https://www.keypup.io/blog/cloudtasker-monitor-your-cloud-tasks-jobs-on-gcp

2 of these metrics are specific for cloudtasker (a Ruby library that uses Cloud Tasks)

https://github.com/keypup-io/cloudtasker

cloudtasker can store your tasks in Memorystore.

1. Cloud Tasks queue size (aka queue depth)
2. Cloud Run billable runtime (ok, ma è una metrica di Cloud Run, non di Cloud Tasks)
3. Job duration (cloudtasker-specific)
4. Redis memory (cloudtasker-specific)

</Transform>

<!--
https://cloud.google.com/tasks/docs/manage-cloud-task-scaling
-->
