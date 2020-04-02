# kubectl-std-json

Export Kubernetes object in JSON format with a clean and sorted style. Remove some auto generated fields and then sort fields in it.

## Installation

`wget https://github.com/fleeto/kubectl-std-json/raw/master/kubectl-std-json -O /usr/local/bin/kubectl-std-json`

## Usage

`kubectl-std-json [resource type] [resource name] [kubectl options]`

### Environment varibales

|Name|Default|Note|
|---|---|---|
|JSON_METADATA|`".metadata.resourceVersion, .metadata.selfLink, .metadata.managedFields, .metadata.generation, .metadata.uid, .metadata.creationTimestamp"`|Fields to remove in `metadata`.|
|JSON_STATUS|`".status"`|Fields to remove in `status`.|
|JSON_ANNOTATION|`".metadata.annotations.\"kubectl.kubernetes.io/last-applied-configuration\", .metadata.annotations.\"deployment.kubernetes.io/revision\""`|Fields to remove in `annotation`.|
|JSON_SPEC|`".spec.template.metadata.creationTimestamp, .spec.revisionHistoryLimit, .spec.templateGeneration"`|Fields to remove in `spec`.|

## Example

~~~shell
$ kubectl std-json secret grafana
{
  "apiVersion": "v1",
  "data": {
    "admin-password": "YWRtaW4=",
    "admin-user": "YWRtaW4=",
    "ldap-toml": ""
  },
  "kind": "Secret",
  "metadata": {
    "labels": {
      "app": "grafana"
    },
    "name": "grafana",
    "namespace": "tcnp"
  },
  "type": "Opaque"
}
~~~

## Warning

It can't deal with object list at this moment.