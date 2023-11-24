---
layout: two-cols
---

<Transform scale="0.85">

## Buffering requests to comply with rate & concurrency limits from 3rd party APIs

APIs may impose rate and/or concurrency limits. If we exceed these limits, APIs respond with HTTP 429 Too Many Requests. We can configure a Cloud Tasks queue to comply with these limits, instead of doing it in our code.

## Buffering requests to smooth out traffic spikes to our service

This is especially useful if our service is deployed on a single VM, or if we have an upper limit to the number of containers of a Cloud Run service.

</Transform>

::right::

<Transform scale="0.85">

## Delegating slow operations to a dedicated service

APIs that send webhooks to an endpoint we control, tipically require the endpoint to respond with an HTTP 2xx status code within a few seconds (e.g. [Stripe API](https://stripe.com/docs/webhooks#acknowledge-events-immediately)). If we want to perform a potentially slow operation (e.g. write to DB, send email, generate PDF), we can create a task, let Cloud Tasks dispatch it to a dedicated service, and respond to the webhook sender immediately.

## Preserving requests in the context of a service outage

We need to send an email, but SendGrid is down. We create a task, let Cloud Tasks retry a bunch of times, and hopefully SendGrid will come back online.

</Transform>

<!--
Examples of a Cloud Tasks queue used to avoid rate limits:

- https://cloud.google.com/tasks/docs/tutorial-workflows
- https://towardsdatascience.com/gcp-serverless-design-pattern-adhering-to-rate-concurrency-limits-with-cloud-tasks-30aa756da763

https://tomorrowio.zendesk.com/hc/en-us/articles/5187600335124-What-is-the-difference-between-rate-limiting-and-concurrent-API-calls
-->
