---
layout: two-cols
---

# Queues

<Transform scale="0.85">

Configuration for a Cloud Task queue:

- GCP region
- [Rate limits](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#ratelimits)
- [Retries](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#RetryConfig)
- [Logging](https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#stackdriverloggingconfig)
- `taskTtl`: maximum amount of time that a task is retained in this queue (from [v2beta3](https://cloud.google.com/tasks/docs/release-notes#January_14_2021))
- `tombstoneTtl`: amount of time the task tombstone is retained after a task is deleted or executed. The tombstone is used in task de-duplication (from [v2beta3](https://cloud.google.com/tasks/docs/release-notes#January_14_2021))

</Transform>

::right::

# Creating a queue

<Transform scale="0.85">

Using gcloud:

```sh
gcloud tasks queues create my-queue \
  --location europe-west3 \
  --max-dispatches-per-second 500 \
  --max-attempts 100
```

Or using an IaC tool like pulumi:

```ts {all|3-6|8-17|all}
import * as gcp from '@pulumi/gcp'

const enable_cloudtasks = new gcp.projects.Service(
  'enable-cloudtasks-api',
  { service: 'cloudtasks.googleapis.com' }
)

const queue = new gcp.cloudtasks.Queue('my-queue',
  {
    location: 'europe-west3',
    name: 'my-queue',
    rateLimits: { maxDispatchesPerSecond: 500 },
    retryConfig: { maxAttempts: 100 },
    stackdriverLoggingConfig: { samplingRatio: 0.5 }
  },
  { dependsOn: [enable_cloudtasks] }
)
```

</Transform>

<!--
Use the Cloud Tasks API to create/manage a queue. There is also the queue.yaml file, but I think it's a legacy method. It is strongly recommended that you use either the configuration file method or the Cloud Tasks API to configure your queues, but not both.
https://cloud.google.com/tasks/docs/queue-yaml

https://cloud.google.com/tasks/docs/configuring-queues

https://www.pulumi.com/registry/packages/gcp/api-docs/cloudtasks/

`taskTtl` is the maximum amount of time that a task will be retained in this queue. After a task has lived for taskTtl, the task will be deleted regardless of whether it was dispatched or not. The minimum value is 10 days. The maximum value is 10 years. Queues created by Cloud Tasks have a default taskTtl of 31 days.
https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues#resource:-queue
-->
