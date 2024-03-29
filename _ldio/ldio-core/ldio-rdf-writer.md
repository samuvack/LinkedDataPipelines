---
layout: default
parent: LD Pipeline Core
title: LD Pipeline RDF Writer
---

# LD Pipeline RDF Writer

To easily output RDF in the correct format, a generic RDF Writer is introduced. 

```mermaid
graph LR
    L[...] --> H[RDF writer]
    H --> S[correct RDF]

    subgraph LD Pipeline
    H
    end
```



## Example

Format as N-Quads:

```yaml
config:
  rdf-writer:
    content-type: application/n-quads
```

Format as JSON-LD with given frame:

```yaml
config:
  rdf-writer:
    content-type: application/ld+json
    frame: |
      {
        "@context": {"@vocab": "http://example.org/"},
        "@type": "Library",
        "contains": {
          "@type": "Book",
          "contains": {
            "@type": "Chapter"
          }
        }
      }
```



## Config options

The RDF Writer supports the below config:

| Property     | Description                                                      | Required | Default     | Example                                                           | Supported values                                              |
| :----------- | :--------------------------------------------------------------- | :------- | :---------- | :---------------------------------------------------------------- | :------------------------------------------------------------ |
| content-type | Target content type.                                             | No       | text/turtle | application/ld+json                                               | Any type supported by [Apache Jena](https://jena.apache.org/) |
| frame        | Additional JSON-LD Frame to format the outputted JSON-LD Object. | No       | N/A         | See https://www.w3.org/TR/json-ld11-framing/#sample-library-frame | Any valid JSON Object that describes a JSON-LD Frame          |
