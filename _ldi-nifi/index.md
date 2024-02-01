---
title: Introduction
layout: home
nav_order: 0
---

# Introduction

[Apache Nifi] is an easy-to-use, powerful, and reliable system to process and distribute data.

The setup of this Linked Data (LD) Pipeline necessitates the use of Docker, and Apache NiFi. Simply dragging the components into the Apache NiFi environment makes setting up the desired LD workflow possible. The LD Pipeline components can be selected from the library.

Directly in Apache NiFi, it delineates the specific LD Pipeline components to be utilized, their sequence, and the operational parameters for each component, ensuring a structured and efficient workflow.

## Usage

All the following processors can be found in the processor list when using the ldes/ldi-workbench-nifi docker image.

These processors can be [added][Adding a processor in NiFi] by filtering on the <i>```be.vlaanderen.informatievlaanderen.ldes.ldi.nifi**_ group or by filtering on the _**vsds\*\*\* tag

- [Create Version Processor](../core/ldi-transformers/version-object-creator)
- [GeoJson to WKT Processor](../core/ldi-transformers/geojson-to-wkt)
- [Json to Json LD Processor](../core/ldi-adapters/json-to-json-ld)
- [Ngsi V2 to LD Processor](../core/ldi-adapters/ngsiv2-to-ld)
- [RDF4j Repository Materialization Processor](../core/ldi-outputs/repository-materialiser)
- [SPARQL Interactions Processor](./processors/sparql-interactions)
- [Version Materialization Processor](../core/ldi-transformers/version-materializer)
- [Archive File Out Processor](../core/ldi-outputs/file-archiving)
- [Archive File In Processor](../core/ldi-outputs/file-archiving)

{: .note }
All documentation and notes about configuration are available in the NiFi component itself.

[Apache NiFi]: https://nifi.apache.org/
[Adding a processor in NiFi]: https://nifi.apache.org/docs/nifi-docs/html/getting-started.html#adding-a-processor
