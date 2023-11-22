---
layout: default
---

# Test your system

<Transform scale="0.8">

## Use an emulator?

No official emulator. There is <Anchor href="https://github.com/aertje/cloud-tasks-emulator" text="aertje/cloud-tasks-emulator" /> but I haven't tried it yet.

## Integration tests

Test the integration between Cloud Tasks and your components (task generator and task handler).

Since Cloud Tasks is not a service under our control, these tests are **cross-system** integration tests and [someone might argue they are not that useful](https://www.draconianoverlord.com/2017/08/23/the-futility-of-cross-system-integration-testing.html/).

## System tests (e2e)

Test the system as a single piece, as an end user would use it.

## Other tests: load testing, chaos testing

Stress test your system with an HTTP load generator like <Anchor href="https://github.com/locustio/locust" text="Locust" />, <Anchor href="https://github.com/artilleryio/artillery" text="artillery" /> or <Anchor href="https://github.com/mcollina/autocannon" text="autocannon" />.

Simulate outages of 3rd paty services your system depends on (e.g. Stripe is down).

</Transform>

<!--
draconianoverlord usa il termine Cross-System Integration Testing perche' secondo lui ci sono:

- **Intra-system integration tests**. Si tratta di test di integrazione fra componenti di cui te hai il controllo. Ad esempio il tuo JS frontend, la tua API, il tuo database layer. **Questi tests secondo lui hanno senso** perche’ te **controlli tutto l’environment**.
- **Inter-/cross-system integration tests**. Si tratta di test di integrazione fra una o piu' componenti di cui te hai il controllo (vedi sopra) e una o piu' componenti di un qualche vendor. Ad esempio quando te scrivi un API client per una API **non** tua, gli eventuali integration tests che scrivi sarebbero **cross-system** integration tests. **Questi tests secondo lui non hanno senso**. Ecco, ma questi direi che sono quelli che normalmente vengono chiamati system tests.
-->
