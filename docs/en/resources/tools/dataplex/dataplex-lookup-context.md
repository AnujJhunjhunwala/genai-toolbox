---
title: "dataplex-lookup-context"
type: docs
weight: 1
description: > 
  A "dataplex-lookup-context" tool retrieves metadata of data assets.
aliases:
- /resources/tools/dataplex-lookup-context
---

## About

A `dataplex-lookup-context` tool retrieves metadata of data assets.
It's compatible with the following sources:

- [dataplex](../../sources/dataplex.md)

`dataplex-lookup-context` takes a required `name` parameter which contains the
project and location to which the request should be attributed in the following
form: projects/{project}/locations/{location} and also a required `resources`
parameter which is a list of resource names for which metadata is needed in one of the 
following forms:
Entry names: projects/{project}/locations/{location}/entryGroups/{group}/entries/{entry}
GCP resource names: //bigquery.googleapis.com/projects/{project}/datasets/{dataset}/tables/{table}
Fully qualified names (FQN): bigquery:{project}.{dataset}.{table}

## Requirements

### IAM Permissions

Dataplex uses [Identity and Access Management (IAM)][iam-overview] to control
user and group access to Dataplex resources. Toolbox will use your
[Application Default Credentials (ADC)][adc] to authorize and authenticate when
interacting with [Dataplex][dataplex-docs].

In addition to [setting the ADC for your server][set-adc], you need to ensure
the IAM identity has been given the correct IAM permissions for the tasks you
intend to perform. See [Dataplex Universal Catalog IAM permissions][iam-permissions]
and [Dataplex Universal Catalog IAM roles][iam-roles] for more information on
applying IAM permissions and roles to an identity.

[iam-overview]: https://cloud.google.com/dataplex/docs/iam-and-access-control
[adc]: https://cloud.google.com/docs/authentication#adc
[set-adc]: https://cloud.google.com/docs/authentication/provide-credentials-adc
[iam-permissions]: https://cloud.google.com/dataplex/docs/iam-permissions
[iam-roles]: https://cloud.google.com/dataplex/docs/iam-roles

## Example

```yaml
kind: tools
name: lookup_context
type: dataplex-lookup-context
source: my-dataplex-source
description: Use this tool to retrieve metadata of Data Assets.
```

## Reference

| **field**   | **type** | **required** | **description**                                    |
|-------------|:--------:|:------------:|----------------------------------------------------|
| type        |  string  |     true     | Must be "dataplex-lookup-context".                 |
| source      |  string  |     true     | Name of the source the tool should execute on.     |
| description |  string  |     true     | Description of the tool that is passed to the LLM. |
