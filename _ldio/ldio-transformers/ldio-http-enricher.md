---
layout: default
parent: LD Pipeline Transformers
title: Http Enricher Transformer
---

# LDIO Http Enricher

<b>LD Pipeline Component Name:</b> <i>```be.vlaanderen.informatievlaanderen.ldes.ldio.LdioHttpEnricher```</i>

<br>

A transformer that allows sending a GET or POST HTTP request to a dynamic URL provided by the model.
The response is converted to linked data and added to the incoming model.


```mermaid
graph LR
    L[GET/POST] --> H[Http Enricher]
    H --> S[Linked Data response]

    subgraph LDIO transformer pipeline
    H
    end
```

## Example

```yml
- name: example
  description: ""

  transformer:
    - name: be.vlaanderen.informatievlaanderen.ldes.ldio.LdioHttpEnricher
      config:
        adapter.name: be.vlaanderen.informatievlaanderen.ldes.ldi.RdfAdapter
        url-property-path: http://example.org/url 
        
```



This example contains a JsonToLdAdapter which needs "core-context" as config.
At the bottom there is also "auth" config provided for the request executor.

```yaml
- name: be.vlaanderen.informatievlaanderen.ldes.ldio.LdioHttpEnricher
  config:
    adapter:
      name: be.vlaanderen.informatievlaanderen.ldes.ldi.JsonToLdAdapter
      config:
        core-context: file:///ldio/jsonld/observation.jsonld
        url-property-path: <http://example.org/url>
        header-property-path: <http://example.org/meta>/<http://example.org/headers>
        body-property-path: <http://example.org/meta>/<http://example.org/body>
        http-method-property-path: <http://example.org/meta>/<http://example.org/method>
        auth:
          type: API_KEY
          api-key: my-secret
          api-key-header: x-api-key
```

## Config options

| Property                            | Description                                                                                                 | Required | Default | Example                                                | Supported values                                               |
| :---------------------------------- | :---------------------------------------------------------------------------------------------------------- | :------- | :------ | :----------------------------------------------------- | :------------------------------------------------------------- |
| adapter.name                        | This transformer requires an [ldio-adapter](../ldio-adapters) to convert the responses to linked data.      | Yes      | N/A     | be.vlaanderen.informatievlaanderen.ldes.ldi.RdfAdapter | Paths of supported LD Pipeline Adapters                        |
| adapter.config.xxx                  | Optional config that may be required by the adapter                                                         | No       | N/A     | be.vlaanderen.informatievlaanderen.ldes.ldi.RdfAdapter | Paths of supported LD Pipeline Adapters                        |
| url-property-path                   | Path defining the url that needs to be selected on the model for the http request.                          | Yes      | N/A     | <http://example.org/url>                               | Valid property paths                                           |
| header-property-path                | Path defining the headers that needs to be selected on the model for the http request.                      | No       | N/A     | <http://example.org/header>                            | Valid property paths                                           |
| body-property-path                  | Path defining the body that needs to be selected on the model to be added when a POST http request is used. | No       | N/A     | <http://example.org/meta>/<http://example.org/body>    | Valid property paths                                           |
| http-method-property-path           | Path defining the http method that needs to be selected on the model for the http request.                  | No       | GET     | GET                                                    | GET or POST                                                    |
| auth.xxx retries.xxx rate-limit.xxx | LDIO Http Requester Config                                                                                  | No       | N/A     | N/A                                                    | [LDIO Http Requester Config](../ldio-core/ldio-http-requester) |

Note that all adapters are supported. When the adapter requires additional config, this can be added as seen below in the example.


