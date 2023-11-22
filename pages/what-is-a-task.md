---
layout: two-cols
---

# Tasks

<Transform scale="0.85">

Object (e.g. Plain Old Javascript Object) that represents a **piece of work** to be performed by **some service**.

**Explicit invocation**: who creates the task retains full **control of execution**.

Task configuration for an HTTP task:

- URL of the endpoint (required)
- Unique name
- HTTP method
- HTTP request headers
- Request body
- Authentication (API Key, OIDC token, OAuth token)
- Schedule time
- Dispatch deadline (e.g. wait max 30 minutes for the worker to process the task)

</Transform>

::right::

# Creating an HTTP task

<Transform scale="0.8">

```js {all|10-27|5-8,29|all}
const {CloudTasksClient} = require('@google-cloud/tasks')

const client = new CloudTasksClient()

const project = 'devfest-milano-2023'
const location = 'europe-west3'
const queue = 'my-queue'
const parent = client.queuePath(project, location, queue)

const url = 'https://some-api-endpoint'
const payload = { foo: "bar" }
const str = JSON.stringify(payload)
const serviceAccountEmail = 
  `task-enqueuer-user@${project}.iam.gserviceaccount.com`

const task = {
  httpRequest: {
    httpMethod: 'POST',
    url,
    oidcToken: { serviceAccountEmail, audience: url },
    headers: { 'Content-Type': 'application/json' },
    body: Buffer.from(str).toString('base64'),
  },
  name: 'my-task-id',
  // schedule the task 5 seconds from now
  scheduleTime: { seconds: Date.now() / 1000 + 5 },
}

const [response] = await client.createTask({parent, task})
```

</Transform>

<!--
https://cloud.google.com/tasks/docs/reference/rest/v2beta3/projects.locations.queues.tasks/create

https://cloud.google.com/tasks/docs/reference/rest/v2beta3/OidcToken

https://cloud.google.com/tasks/docs/reference/rest/v2beta3/OAuthToken

To create an App Engine task, replace httpRequest with appEngineHttpRequest.
-->
