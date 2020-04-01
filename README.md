# kubectl-std-json

Export Kubernetes object in JSON format with a clean and sorted style. Remove some auto generated fields and then sort fields in it.

## Installation

`wget https://github.com/fleeto/kubectl-std-json/raw/master/kubectl-std-json -O /usr/local/bin/kubectl-std-json`

## Usage

`kubectl-std-json [resource type] [resource name] [kubectl options]`

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
