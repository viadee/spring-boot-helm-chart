# viadee-spring-boot-helm-chart


## features

- configure the spring boot app in the helm values.yaml 
  - plain application yaml as value
    - reference value as a entry for the configmap
    - value which contains multiline string where you can put spring config as yaml 
    - configmap gets mounted
    - Add environmental variable SPRING_CONFIG_ADDITIONAL_LOCATION which points to the mounted application.yaml
  - encrypted values (TODO)
  - load properties from existing secret
    - mount application-helm-generated-values.yaml from secret to pod and add path to SPRING_CONFIG_ADDITIONAL_LOCATION environment variable
    - add a comma separated entry to the spring.cloud.kubernetes.secrets.paths property in application-helm-generated-values.yaml
    - mount referenced secrets to pod
- pre-configured readinessProbes and livenessProbes on not exposed port
