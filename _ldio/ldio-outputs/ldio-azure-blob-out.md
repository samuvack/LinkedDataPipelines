---
layout: default
parent: LD Pipeline Outputs
title: Azure Blob Out
---

# LDIO Azure Blob Out

<b>LD Pipeline Component Name:</b> <i>```be.vlaanderen.informatievlaanderen.ldes.ldio.LdiAzureBlobOut```</i>

<br>

The LDIO Azure Blob Out writes out messages to an Azure Blob Container. Messages can be written in any format supported by Apache Jena or in JSON format.

{.warning}
For the json format it is necessary to have a URI which holds the context.


```mermaid
graph LR
    LDES --> C[Client]
    C --> H[LDIO Azure Blob Out Component]
    H --> S[KAzure Blob Container]

    subgraph LDIO output pipeline
    C
    H
    end
```

## Example

### JSON

```yaml
outputs:
  - name: "be.vlaanderen.informatievlaanderen.ldes.ldio.LdiAzureBlobOut"
    config:
      lang: "json"
      storage-account-name: "storageaccount"
      connection-string: "DefaultEndpointsProtocol=https;AccountName=demopowerquery;AccountKey=...;EndpointSuffix=core.windows.net"
      blob-container: "blobcontainer"
      json-context-uri: "https://essentialcomplexity.eu/gipod.jsonld"
```

### N-QUADS

```yaml
outputs:
  - name: "be.vlaanderen.informatievlaanderen.ldes.ldio.LdiAzureBlobOut"
    config:
      lang: "n-quads"
      storage-account-name: "storageaccount"
      connection-string: "DefaultEndpointsProtocol=https;AccountName=demopowerquery;AccountKey=...;EndpointSuffix=core.windows.net"
      blob-container: "blobcontainer"
```


## Config options

| Property             | Description                                                                                     | Required | Default | Example                                                                                                  | Supported values                                                                                                      |
| -------------------- | ----------------------------------------------------------------------------------------------- | -------- | ------- | -------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| lang                 | **Json\*** and any lang supported by Apache Jena. \*json requires the json-context-uri property | No       | n-quads | json                                                                                                     | json, jsonld, turtle, n-triples, n-quads, ...                                                                         |
| storage-account-name | Name of the Azure Storage Account                                                               | Yes      | N/A     | saldesclientdemo                                                                                         | String                                                                                                                |
| connection-string    | Value of the Connection String of the Azure Storage Account                                     | Yes      | N/A     | DefaultEndpointsProtocol=https;AccountName=demopowerquery;AccountKey=...;EndpointSuffix=core.windows.net | [Azure Connection String](https://learn.microsoft.com/en-us/azure/storage/common/storage-configure-connection-string) |
| blob-container       | Name of the Blob Container                                                                      | Yes      | N/A     | data                                                                                                     | String                                                                                                                |
| json-context-uri     | URI which holds the Json Context                                                                | No       | ""      | https://private-api.gipod.beta-vlaanderen.be/api/v1/context/gipod.jsonld                                 | URI describing [context](https://www.w3.org/TR/json-ld11/#the-context)                                                |
