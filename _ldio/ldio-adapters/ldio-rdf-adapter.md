---
layout: default
parent: LD Pipeline Adapters
title: RDF Adapter
---

# LDIO RDF Adapter

<b>LD Pipeline Component Name:</b> <i>```be.vlaanderen.informatievlaanderen.ldes.ldi.RdfAdapter```</i>

<br>

An LDIO wrapper component for the [LDI RDF Adapter building block](../../core/ldi-adapters/rdf-adapter)

```mermaid
graph LR
    L[...] --> H[RDF writer]
    H --> S[correct RDF]

    subgraph LD Pipeline
    H
    end
```


## Example

```yml
orchestrator:
  pipelines:
    -   name: example
        adapter:
            name: be.vlaanderen.informatievlaanderen.ldes.ldi.RdfAdapter
```


## Config

This component has no required config
