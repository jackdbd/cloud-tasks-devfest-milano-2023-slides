---
layout: default
---

# IAM

<Transform scale="0.8">

## Task creator

The service account attached to the service that creates tasks and sends them to Cloud Storage must have the IAM roles **Task Enqueuer** and **Service Account User**:

- <code class="inline-code">roles/cloudtasks.enqueuer</code>
- <code class="inline-code">roles/iam.serviceAccountUser</code>

## Cloud Tasks

The service account for Cloud Tasks is managed by Google. Double check that this service account exists and that it has the IAM role **Cloud Tasks Service Agent**:

<code class="inline-code">service-<project_number>@gcp-sa-cloudtasks.iam.gserviceaccount.com</code>

## Task handler

The service account attached to the service that processes tasks must have the necessary IAM permissions to do its job. E.g. For a Cloud Run service that requires read/write access to Firestore we can assign the IAM role <code class="inline-code">roles/datastore.user</code>.

</Transform>

<!--
https://cloud.google.com/tasks/docs/reference-access-control

To be precise, we need the IAM permission `cloudtasks.tasks.create`. We can obtain this permission by assigning the IAM role `roles/cloudtasks.enqueuer`.

You can create an IAM binding:

- at the GCP project level. It grants the service account permissions on ALL Cloud Tasks queues. With Pulumi this seems NOT to work.
- at the Cloud Tasks queue level. It grants the service account permissions on JUST THAT queue. With Pulumi this works and can be done using `gcp.cloudtasks.QueueIamBinding`

The first time I used Cloud Tasks I messed up because I changed the service account used by Cloud Tasks.

The IAM role `roles/cloudtasks.enqueuer` does NOT grant permission to run tasks. Just to enqueue them.
To run tasks we need `roles/cloudtasks.taskRunner`.

Also, restrict access to your Cloud Tasks queues.
https://cloud.google.com/tasks/docs/secure-queue-configuration
-->
