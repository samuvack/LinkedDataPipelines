---
layout: default
parent: LD Pipeline Outputs
title: Console Out
---

# LDIO Console Out

<b>LD Pipeline Component Name:</b> <i>```be.vlaanderen.informatievlaanderen.ldes.ldio.LdioConsoleOut```</i>

<br>

The LDIO Console Out will output its given model to the console.

## Example

```yml
orchestrator:
  pipelines:
    - name: example
      output:
        name: be.vlaanderen.informatievlaanderen.ldes.ldio.LdioConsoleOut
        config:
          rdf-writer: N/A
          
```

## Config options

| Property   | Description           | Required | Default      | Example | Supported values                                      |
| :--------- | :-------------------- | :------- | :----------- | :------ | :---------------------------------------------------- |
| rdf-writer | LDI RDF Writer Config | No       | Empty Config | N/A     | [LDI RDF Writer Config](../ldio-core/ldio-rdf-writer) |
