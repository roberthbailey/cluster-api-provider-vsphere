# Trusted certificates

## Use case

Often there is a need for trusting non-standard CA certs in the system. For e.g. these could be custom CA certs internal to an enterprise. In order to support secure connectivity to any secure endpoint with certs signed by the custom CA, these CA certs need to be added to the machine's trusted certs store

## How to use

Base64 encode the certificate and add that encoded string to the list under `trustedCerts` property:

```shell
base64 --wrap=0 <path to CA cert>
```

Use the output of the above command in the list of `trustedCerts` like below:

```yaml
providerSpec:
  value:
    apiVersion: "vsphere.cluster.k8s.io/v1alpha1"
    kind: "VsphereMachineProviderSpec"
    datacenter: "datacenter"
    ...
    trustedCerts:
    - <Base64 encoded certificate 1>
    - <Base64 encoded certificate 2>
```
