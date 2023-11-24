---
layout: two-cols
---

# Queues in theory

<Transform scale="0.85">

1. Infinitely long.
1. Open at both ends (enqueue, dequeue).
1. FIFO (First In, First Out).
1. Exactly-once semantics.

</Transform>

::right::

# Queues in Cloud Tasks

<Transform scale="0.85">

<div class="stack">

1. Limited rate of processing (set by us).
1. We can only add tasks to a queue (enqueue), not remove them (dequeue). We can delete tasks by their ID though! Cloud Tasks automatically deletes old tasks (see <code class="inline-code">taskTtl</code> in [v2beta3](https://cloud.google.com/tasks/docs/release-notes#January_14_2021)).
1. [No task execution order is guaranteed](https://cloud.google.com/tasks/docs/common-pitfalls#execution_order). We can schedule tasks for later, configure retries, force specific tasks to run!
1. [No exactly-once semantics is guaranteed](https://cloud.google.com/tasks/docs/common-pitfalls#duplicate_execution).

<Citation
  citeHref="https://cloud.google.com/tasks/docs/common-pitfalls#duplicate_execution"
  citeText="Duplicate execution">
  <template v-slot:quote>
    <p>Cloud Tasks aims for a strict "execute exactly once" semantic. However, in situations where a design trade-off must be made between guaranteed execution and duplicate execution, the service errs on the side of guaranteed execution. As such, <b>a non-zero number of duplicate executions do occur</b>.</p>
  </template>
</Citation>

</div>

</Transform>

<!--
https://cloud.google.com/tasks/docs/common-pitfalls#execution_order

> Cloud Tasks aims for a strict "execute exactly once" semantic. However, in situations where a design trade-off must be made between guaranteed execution and duplicate execution, the service errs on the side of guaranteed execution. As such, a non-zero number of duplicate executions do occur.
-->
