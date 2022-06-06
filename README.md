# viadee-spring-boot-helm-chart

## features

- configure the spring boot app in the helm values.yaml
  - plain application yaml as a multiline value
  - encrypted values
  - load properties from existing secret
- pre-configured readinessProbes and livenessProbes

## seal secret values

```shell
$ echo -n "superSecretPassword" | kubeseal --raw --scope cluster-wide
```

## prerequisite

1. cluster needs the following operators:

- [bitnami sealed secrets](https://github.com/bitnami-labs/sealed-secrets#installation) - for encrypted secrets

2. spring boot application needs the following starters:

- spring-boot-starter-web
- spring-boot-starter-actuator
- spring-cloud-starter-kubernetes-client-config

3. locally

- [kubeseal cli](https://github.com/bitnami-labs/sealed-secrets#homebrew)
