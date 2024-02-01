---
layout: default
parent: LD Pipeline Transformers
title: SPARQL Construct
---

# LDIO SPARQL Construct

<b>LD Pipeline Component Name:</b> <i>```be.vlaanderen.informatievlaanderen.ldes.ldi.SparqlConstructTransformer```</i>

<br>

An LDIO wrapper component for the [LDI SPARQL Construct building block](../../core/ldi-transformers/sparql-construct)

## Config

| Property | Description                                              | Required | Default | Example  | Supported values |
| :------- | :------------------------------------------------------- | :------- | :------ | :------- | :--------------- |
| query    | Path to content of SPARQL Query/content of SPARQL query. | Yes      | N/A     | query.rq | Path/String      |
| infer    | Include original model in end result.                    | No       | false   | false    | true or false    |
