---
layout: default
---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-3 gap-10 pt-4 -mb-6">

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```plantuml {scale: 0.85}
@startuml
left to right direction

package "App" {
  [Task]
}

cloud "Cloud Tasks" {
    [Queue]
}

frame "HTTP Target" {
    [HTTP Handler]
}

frame "App Engine Target" {
    [App Engine Handler]
}

[App] --> [Cloud Tasks] : sends task to
[Cloud Tasks] -[#0000ff]-> [HTTP Target] : HTTP
[HTTP Handler] .[#0000ff].> [Queue] : 2xx
[Cloud Tasks] -[#00ff00]-> [App Engine Target] : HTTP
[App Engine Handler] .[#00ff00].> [Queue] : 2xx

@enduml
```


```mermaid {theme: 'default', scale: 0.95}
graph TD
A[Order service]-->|HTTP task| CT[Cloud Tasks]
A[Order service]-->|HTTP task| CT[Cloud Tasks]
CT-->B[Shipping service]
CT-->C[Order service]
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)

<!--
https://mermaid.js.org/config/theming.html

https://mermaid.js.org/syntax/flowchart.html

https://plantuml.com/
https://plantuml.com/component-diagram
-->
