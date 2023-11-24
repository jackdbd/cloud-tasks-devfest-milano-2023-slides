---
layout: two-cols
---

# Alert: queue overload

<Transform scale="0.85">

Queues or queue groups can become overloaded any time traffic increases suddenly. As a result, these queues can experience:

- Increased task creation latency
- Increased task creation error rate
- Reduced dispatch rate

To defend against this, Google recommends establishing controls in any situation where the create or dispatch rate of a queue or queue group can spike suddenly.

### The 500/50/5 pattern

Google recommends a maximum of **500 operations per second to a cold queue or queue group, then increasing traffic by 50% every 5 minutes**. In theory, you can grow to 740K operations per second after 90 minutes using this ramp up schedule.

</Transform>

::right::

# Alert: target overload

<Transform scale="0.85">

<div class="stack">

Cloud Tasks can overload other services that you are using (e.g. Cloud Run, Firestor), and your network usage, if dispatches from a queue increase dramatically in a short period of time.

If a backlog of tasks has accumulated, then unpausing those queues can potentially overload these services.

The recommended defense is the same **500/50/5** pattern suggested for queue overload: if a queue dispatches more than 500 TPS, increase traffic triggered by a queue by no more than 50% every 5 minutes.

</div>

</Transform>

<!--
https://cloud.google.com/tasks/docs/manage-cloud-task-scaling#queue

https://cloud.google.com/tasks/docs/manage-cloud-task-scaling#target

Always define your alerting policies in JSON, keep them under version control and document them (e.g. in markdown)
https://cloud.google.com/monitoring/alerts/policies-in-json
-->
