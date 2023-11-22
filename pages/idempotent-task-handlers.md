---
layout: default
---

# Implement idempotent task handlers

<Transform scale="0.85">

Idempotency:

- is **different** from safety.
- means that multiple identical requests will have the **same outcome**.
- does **not** mean that the server has to respond in the same way on each request. If the constraint is violated, the server should return [HTTP 409 Conflict](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/409).

We can implement an idempotent task handler using:

- a constraint from our business logic.
- ETags (only for existing resources, so only for PATCH requests, not for POST requests).
- an idempotency key (e.g. [Stripe API](https://stripe.com/docs/api/idempotent_requests)).

Reference:

- [HTTP methods: Idempotency and Safety](https://www.mscharhag.com/api-design/http-idempotent-safe)
- [Making POST and PATCH requests idempotent](https://www.mscharhag.com/api-design/rest-making-post-patch-idempotent)
- [Pattern: Idempotent Consumer](https://microservices.io/patterns/communication-style/idempotent-consumer.html)
- <Anchor href="https://youtu.be/xeBY8fCWfvU?si=44zPx5-lDkkrlS3b" text="Handling Duplicate Messages (Idempotent Consumers)" />

</Transform>

<!--
PUT vs POST: PUT is idempotent, POST is not.
https://restcookbook.com/HTTP%20Methods/put-vs-post/

PUT vs PATCH: PUT is idempotent, PATCH is not.
PUT always requires the entire request payload.
PATCH allows a subset of the payload.
-->
