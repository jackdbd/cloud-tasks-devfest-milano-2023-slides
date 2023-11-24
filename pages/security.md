---
layout: two-cols
---

# Least privilege

<Transform scale="0.85">

Follow the [principle of least privilege](https://cloud.google.com/iam/docs/using-iam-securely#least_privilege).

Restrict queue management methods to a small set of people. Prefer using a Google Group instead of individual users.

```sh
gcloud projects add-iam-policy-binding PROJECT_ID \
  --member group:EMAIL \
  --role roles/cloudtasks.queueAdmin
```

If you have multiple queues in a project and want to limit access to individual queues, define IAM bindings at the queue level instead of the project level.

```sh
gcloud tasks queues add-iam-policy-binding QUEUE_NAME \
  --location LOCATION \
  --member serviceAccount:EMAIL \
  --role roles/cloudtasks.enqueuer
```

</Transform>

::right::

# Service perimeter

<Transform scale="0.85">

Set up a service perimeter using [VPC Service Controls](https://cloud.google.com/tasks/docs/use-vpc-service-controls).

HTTP requests from a Cloud Tasks execution will be blocked when directed towards non-Cloud Functions endpoints, non-Cloud Run endpoints, and in general for any service outside of the perimeter you set up.

Service perimeters mitigate the risk of **data exfiltration**.

</Transform>

<!--
-->
