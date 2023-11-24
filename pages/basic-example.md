---
layout: center
---

# A basic example

```mermaid {theme: 'default', scale: 0.8}
sequenceDiagram
    autonumber
    participant TC as Task Creator
    participant CT as Cloud Tasks
    participant Target
    TC->>CT: create task
    Note right of CT: A task can be scheduled<br/>up to 30 days in the future
    loop Keep dispatching task until
        CT->>Target: - 2xx from Target<br />- max attempts<br />- timeout<br />- task TTL
    end
    activate Target
    Note left of Target: task processing must<br />finish within 30 minutes
    Target-->>CT: HTTP 2xx
    deactivate Target
```

<!--
Timeouts: for all HTTP Target task handlers the default timeout is 10 minutes, with a maximum of 30 minutes.
https://cloud.google.com/tasks/docs/creating-http-target-tasks

https://stackoverflow.com/questions/58530361/how-increase-maximum-schedule-time-in-gcloud-tasks-api

https://cloud.google.com/tasks/docs/reference/rpc/google.cloud.tasks.v2#google.cloud.tasks.v2.Task.FIELDS.google.protobuf.Timestamp.google.cloud.tasks.v2.Task.schedule_time
-->