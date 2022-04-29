# viadee-spring-boot-helm-chart

## features

- configure the spring boot app in the helm values.yaml
  - plain application yaml as a multiline value
  - encrypted values
  - load properties from existing secret
- pre-configured readinessProbes and livenessProbes on not exposed port
- expose metrics for prometheus and collect them

## seal secret values

```shell
$ echo -n "superSecretPassword" | kubeseal --raw --scope cluster-wide
```

## prerequisite

1. cluster needs the following operators:

- [bitnami sealed secrets](https://github.com/bitnami-labs/sealed-secrets#installation) - for encrypted secrets
- [prometheus](https://github.com/prometheus-operator/prometheus-operator#quickstart) - for metric exposure

2. spring boot application needs the following starters:

- spring-boot-starter-web
- spring-boot-starter-actuator
- spring-cloud-starter-kubernetes-client-config
- micrometer-registry-prometheus

3. locally

- [kubeseal cli](https://github.com/bitnami-labs/sealed-secrets#homebrew)
