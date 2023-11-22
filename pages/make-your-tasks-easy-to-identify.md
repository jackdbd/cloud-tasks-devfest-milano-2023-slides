---
layout: center
---

# Make your tasks easy to identify

<Transform scale="0.85">

- Give you tasks a `name`. Use something self-explanatory. For example, `VERB-WHAT-UTC_TIMESTAMP`.
- Add a custom HTTP header containing the identifier of the service that created that task. For example, `X-Task-Created-By` or `X-Task-Enqueued-By`.
- Keep in mind `tombstoneTtl` for [task deduplication](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues.tasks/create#body.request_body.FIELDS.task).

</Transform>

<!--
Cloud Tasks assigns each task a name automatically. But this names are UUIDs which are meaningless for you. You open the Cloud Tasks dashboard and don't understand who enqueued a task and what the task is about.
-->
