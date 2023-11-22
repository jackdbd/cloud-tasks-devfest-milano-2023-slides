---
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# https://sli.dev/custom/#frontmatter-configures
# Try CSS classes here:
# https://unocss.dev/interactive/
# class: 'text-center'
css: unocss
defaults:
  layout: cover
# whether to persist drawings in exports and build
drawings:
  persist: false
# https://sli.dev/custom/highlighters.html
highlighter: shiki
htmlAttrs:
  dir: 'ltr'
  lang: 'en'
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# show line numbers in code blocks
lineNumbers: false
# https://sli.dev/guide/presenter-mode.html
presenter: true
src: ./pages/title.md
theme: default
# theme: seriph
# https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
---

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
src: ./pages/speaker.md
---

---
src: ./pages/what-is-cloud-tasks.md
---

---
src: ./pages/queues-in-theory-vs-in-cloud-tasks.md
---

---
src: ./pages/creating-a-queue.md
---

---
src: ./pages/what-is-a-task.md
---

---
src: ./pages/token-bucket-algorithm.md
hide: true
---

---
src: ./pages/basic-example.md
---

---
src: ./pages/advanced-example.md
---

---
src: ./pages/notifications-sse.md
---

---
src: ./pages/notifications-websockets.md
---

---
src: ./pages/notifications-serverless-friendly.md
---

---
src: ./pages/iam.md
---

---
src: ./pages/vs-pubsub-1.md
---

---
src: ./pages/vs-pubsub-2.md
---

---
src: ./pages/vs-cloud-scheduler.md
---

---
src: ./pages/diagrams.md
hide: true
---

---
src: ./pages/make-your-tasks-easy-to-identify.md
---

---
src: ./pages/idempotent-task-handlers.md
---

---
src: ./pages/tests.md
---

---
src: ./pages/metrics.md
---

---
src: ./pages/components.md
hide: true
---

---
class: px-20
src: ./pages/themes.md
hide: true
---

---
src: ./pages/demo.md
---

---
class: text-center
layout: center
---

# Thanks!

<!--
Cloud Tasks is a managed service that allows developers to create distributed task queues that can execute background jobs asynchronously.

In this talk we will describe how Cloud Tasks works, highlight its differences with Cloud Pub/Sub, and suggest a few guidelines we can adopt when creating our tasks and monitoring our queues.

<Anchor href="https://github.com/jackdbd/cloud-tasks-devfest-milano-2023-project" text="Pulumi project" />
-->
