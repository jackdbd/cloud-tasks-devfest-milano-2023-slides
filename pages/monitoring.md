---
layout: two-cols
---

# Cloud Tasks metrics

<Transform scale="0.85">

The Cloud Tasks API defines [4 metrics](https://cloud.google.com/monitoring/api/metrics_gcp#gcp-cloudtasks) (sampled every 60 seconds):

1. <code class="inline-code">api/request_count</code>: count of Cloud Tasks API calls.
1. <code class="inline-code">queue/depth</code>: number of tasks in the queue.
1. <code class="inline-code">queue/task_attempt_count</code>: count of task attempts broken down by response code.
1. <code class="inline-code">queue/task_attempt_delays</code>: delay between each scheduled attempt time and actual attempt time.

We could also enable [Cloud Tasks logging](https://cloud.google.com/tasks/docs/logging?authuser=0#logged_operations) and monitor <code class="inline-code">AttemptDispatch</code> and <code class="inline-code">AttemptResponse</code>.

</Transform>

::right::

# Task-specific metrics

<Transform scale="0.85">

If the HTTP target containing the task handler is a [Cloud Run service](https://cloud.google.com/monitoring/api/metrics_gcp#gcp-run), you could monitor:

- <code class="inline-code">container/billable_instance_time</code>: billable time aggregated across all container instances.
- <code class="inline-code">container/memory/utilizations</code>: memory utilization distribution across all container instances.

You can also define your own metrics:

- job duration: it depends on what services your job relies on (e.g. database, cache store, third-party API). The Ruby library <Anchor href="https://github.com/keypup-io/cloudtasker" text ="Cloudtasker" /> adds a <code class="inline-code">duration</code> field to each "Job done" log entry. This allows you to define a [log-based metric](https://cloud.google.com/logging/docs/logs-based-metrics) and monitor it. See [this article](https://www.keypup.io/blog/cloudtasker-monitor-your-cloud-tasks-jobs-on-gcp) for an example.

Maybe also define SLIs, SLOs and error budgets.

</Transform>

<!--
I think queue/depth in Cloud Tasks is similar to subscription/num_undelivered_messages (i.e. the message backlog) in Cloud Pub/Sub. But Pub/Sub allows N subscribers to a topic. Cloud Tasks only allows 1 Target for a Queue.
https://cloud.google.com/pubsub/docs/monitoring#monitoring_the_backlog
-->
