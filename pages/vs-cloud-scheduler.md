---
layout: two-cols
---

# Cloud Tasks

<Transform scale="0.85">

## Trigger

A Cloud Tasks **task** runs immediately or according to its configured <code class="inline-code">scheduleTime</code>. You can schedule a task up to 30 days into the future.

## Rates

A task can run up to the <code class="inline-code">maxDispatches</code> value of the queue it is dispatched from. The maximum value is 500 (see the queue's [rate limits config](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#RateLimits)).

## Retries

Cloud Tasks adopts a truncated exponential backoff strategy to retry failed tasks (see the queue's [retry config](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#retryconfig)).

</Transform>

::right::

# Cloud Scheduler

<Transform scale="0.85">

## Trigger

A Cloud Scheduler **job** runs according to the [cron expression](https://crontab.guru/) you defined. You can schedule a job any time (?) into the future.

## Rates

A job can run max **once per second**.

## Retries

Cloud Scheduler adopts a truncated exponential backoff strategy to retry failed jobs.

</Transform>

<!--
https://cloud.google.com/tasks/docs/comp-tasks-sched
-->
