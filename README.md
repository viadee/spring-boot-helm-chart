# viadee-spring-boot-helm-chart

## features

- configure the spring boot app in the helm values.yaml
  - plain application yaml as a multiline value
  - encrypted values
  - load properties from existing secret
- pre-configured readinessProbes and livenessProbes

## How to install the chart

The helm chart can be installed through a helm chart repository hosted on a github page in this repository. To install follow the next steps:

```shell
helm repo add viadee https://viadee.github.io/spring-boot-helm-chart
helm install <release-name> viadee/spring-boot-helm-chart
```

## Uninstalling the Chart

To uninstall/delete the my-release deployment:

```shell
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## prerequisite

1. cluster needs the following operators:

- [bitnami sealed secrets](https://github.com/bitnami-labs/sealed-secrets#installation) - for encrypted secrets

2. spring boot application needs the following starters:

- spring-boot-starter-web
- spring-boot-starter-actuator
- spring-cloud-starter-kubernetes-client-config

3. locally

- [kubeseal cli](https://github.com/bitnami-labs/sealed-secrets#homebrew)

## seal secret values example

```shell
$ echo -n "superSecretPassword" | kubeseal --raw --scope cluster-wide
```
