---
layout: center
---

# Make your tasks easy to identify

<Transform scale="0.85">

- Give you tasks a <code class="inline-code">name</code>. Use something self-explanatory. For example, <code class="inline-code">VERB-WHAT-UTC_TIMESTAMP</code>, like <code class="inline-code">scrape-example_com_homepage-1700834383</code>. Or maybe <code class="inline-code">VERB-WHAT-PERIOD</code>, like <code class="inline-code">generate-sales_report-2023-11</code>.*
- Add a custom HTTP header containing the identifier of the service that created that task. For example, <code class="inline-code">X-Task-Created-By</code> or <code class="inline-code">X-Task-Enqueued-By</code>.
- Keep in mind <code class="inline-code">tombstoneTtl</code> for [task deduplication](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues.tasks/create#body.request_body.FIELDS.task).

*Giving your name to task introduces a [performance penalty](https://cloud.google.com/tasks/docs/manage-cloud-task-scaling#named_tasks). These costs can be magnified significantly if tasks are named sequentially, such as with timestamps.

</Transform>

<!--
Cloud Tasks assigns each task a name automatically. But this names are UUIDs which are meaningless for you. You open the Cloud Tasks dashboard and don't understand who enqueued a task and what the task is about.

We recommend using a well-distributed prefix for task names, such as a hash of the contents.

These costs can be magnified significantly if tasks are named sequentially, such as with timestamps. I think this is similar to the index hotspotting problem of databases (see key visualizer in BigTable or Firestore).
-->
