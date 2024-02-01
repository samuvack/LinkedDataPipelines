---
title: Introduction
layout: home
nav_order: 0
---

# Introduction

A Linked Data Pipeline CLI are configurable components that can be used to create a pipeline in order to transform, convert, prepare linked data independently. This LD Pipeline CLI is a lightweight alternative for LD Pipeline for [Apache NiFi].

The setup of this Linked Data (LD) Pipeline necessitates the use of Docker. A YAML configuration file delineates the specific LD Pipeline components to be utilized, their sequence, and the operational parameters for each component, ensuring a structured and efficient workflow.

{: .note }
The <b>LDES client</b> is a configurable component that is part of the LD Pipeline toolkit.


## Setup Basic Configuration

To set up a basic LDIO configuration, all that is needed is passing a YAML configuration.

This can look as follows:

````yaml
orchestrator:
  pipelines:
    - name: my-first-pipeline
      input:
        name: fully-qualified name of LDI Input
        config:
          foo: bar
        adapter:
          name: fully-qualified name of LDI Adapter
          config:
            foo: bar
      transformers:
        - name: fully-qualified name of LDI Transformer
          config:
            foo: bar
      outputs:
        - name: fully-qualified name of LDI Transformer
          config:
            foo: bar
````

- Note that one orchestrator can have multiple pipelines 
- Note that one pipeline can have multiple LDI Transformers and LDI Outputs 

## LDIO DEBUG Logging

To enable logging the input model for a 
* [LDIO Adapter](./ldio-adapters)
* [LDIO Transformer](./ldio-transformers)
* [LDIO Output](./ldio-outputs)

Make sure you 

* Add the following property in your application config:
    ````yaml
    logging:
        level:
            be.vlaanderen.informatievlaanderen: DEBUG
    ````
* Add the ```debug: true``` property to your transformer or output config.

## LDIO Logging & Monitoring

To provide a better insight in the workings in the LDIO, we expose a prometheus endpoint (`/actuator/prometheus`) that
encloses some metrics (with included tags):

* ldio_data_in_total: Number (Amount of items passed at the start of Transformer Pipeline)
  * pipeline: String (Refers to the pipeline name)
  * ldio_type: String (Refers to the LDIO Input Type of pipeline)
* ldio_data_out_total: Number (Amount of items passed at the end of Transformer Pipeline)
  * pipeline: String (Refers to the pipeline name)

To consult these metrics, make sure the prometheus endpoint is enabled by setting
the following setting:

````yaml
management:
  endpoints:
    web:
      exposure:
        include:
          - prometheus
````

[Apache NiFi]: https://nifi.apache.org/
