# ODK Central - Helm Chart

Central is the ODK server. It manages user accounts and permissions, stores form definitions, and allows data collection clients like ODK Collect to connect to it for form download and submission upload.

## Installation

To install this Helm chart, run: helm install odkcentral oci://harbor.containers.wurnet.nl/wur/odk -f values.yaml
# odk

![Version: 0.0.0](https://img.shields.io/badge/Version-0.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v2024.3.2](https://img.shields.io/badge/AppVersion-v2024.3.2-informational?style=flat-square)

The standard for mobile data collection

## Source Code

* <oci://harbor.containers.wurnet.nl/wur/odk>
* <https://github.com/getodk/central>
* <https://github.com/getodk/central/pkgs/container/central-service/versions?filters[version_type]=tagged>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | postgresql | 15.5.38 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| enketo.image | string | `"harbor.containers.wurnet.nl/ghcr-proxy/enketo/enketo:7.5.1"` |  |
| enketo.resources.limits.cpu | string | `"1000m"` |  |
| enketo.resources.limits.memory | string | `"1024Mi"` |  |
| enketo.resources.requests.cpu | string | `"500m"` |  |
| enketo.resources.requests.memory | string | `"256Mi"` |  |
| fullnameOverride | string | `""` |  |
| image.odkregistry | string | `"ghcr.io/getodk"` | Registry where ghcr.io/getodk/* can be pulled from |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.registry | string | `"harbor.containers.wurnet.nl/proxy-cache"` | Registry where the common images can be pulled  |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| ingress.annotations."cert-manager.io/cluster-issuer" | string | `"sectigo"` |  |
| ingress.annotations."ingress.kubernetes.io/ssl-redirect" | string | `"true"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/backend-protocol" | string | `"HTTP"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/enable-global-auth" | string | `"false"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-body-size" | string | `"512m"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-read-timeout" | string | `"25600"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-send-timeout" | string | `"25600"` |  |
| ingress.className | string | `"nginx-public"` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `"odk-sandbox.containers-test.wur.nl"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls[0].hosts[0] | string | `"odk-sandbox.containers-test.wur.nl"` |  |
| ingress.tls[0].secretName | string | `"odk-sandbox.containers-test.wur.nl"` |  |
| nameOverride | string | `""` |  |
| nginx.resources.limits.cpu | string | `"200m"` |  |
| nginx.resources.limits.memory | string | `"64Mi"` |  |
| nginx.resources.requests.cpu | string | `"100m"` |  |
| nginx.resources.requests.memory | string | `"32Mi"` |  |
| odk.existingSecret | string | `""` | Create a secret manually containing the fields shown below (recommended). |
| odk.secrets.DB_HOST | string | `""` | the database host for the ODK Central instance |
| odk.secrets.DB_NAME | string | `""` | the database name for the ODK Central instance |
| odk.secrets.DB_PASSWORD | string | `""` | the database password for the ODK Central instance |
| odk.secrets.DB_SSL | bool | `true` | SSL mode for the database connection |
| odk.secrets.DB_USER | string | `""` | the database user for the ODK Central instance |
| odk.secrets.DOMAIN | string | `"odk-sandbox.containers-test.wur.nl"` | the domain for the ODK Central instance |
| odk.secrets.EMAIL_FROM | string | `"emailfromadress@odk-sandbox.containers-test.wur.nl"` | the email address that is used to send emails from the ODK Central instance |
| odk.secrets.EMAIL_HOST | string | `""` | the hostname for the final mailserver |
| odk.secrets.EMAIL_PASSWORD | string | `""` | the password for the user on the final mailserver |
| odk.secrets.EMAIL_PORT | int | `587` | the default email port for the final mailserver |
| odk.secrets.EMAIL_SECURE | string | `"true"` | whether to use TLS for the final mailserver |
| odk.secrets.EMAIL_USER | string | `""` | the user for the final mailserver |
| odk.secrets.ENKETO_API_KEY | string | `"enketo_api_key_secret"` | the Enketo API key  |
| odk.secrets.ENKETO_LESS_SECRET | string | `"enketo_less_secret"` | the Enketo Less API key |
| odk.secrets.ENKETO_SECRET | string | `"enketo_secret"` | The Enketo secret used for the enketo service |
| odk.user | object | `{"existingSecret":"","password":"admin12345678","username":"admin@domain.tld"}` | The initial admin user configuration |
| odk.user.password | string | `"admin12345678"` | the password for the initial admin user |
| odk.user.username | string | `"admin@domain.tld"` | the username for the initial admin user |
| postfix.enabled | bool | `true` |  |
| postfix.overwriteFrom | string | `"ODK Sandbox <noreply@odk-sandbox.containers-test.wur.nl>"` |  |
| postfix.resources.limits.cpu | string | `"100m"` |  |
| postfix.resources.limits.memory | string | `"128Mi"` |  |
| postfix.resources.requests.cpu | string | `"50m"` |  |
| postfix.resources.requests.memory | string | `"64Mi"` |  |
| postfix.serverHostname | string | `"odk-sandbox.containers-test.wur.nl"` |  |
| postgresql.architecture | string | `"standalone"` |  |
| postgresql.auth.database | string | `"odkcentral"` |  |
| postgresql.auth.enablePostgresUser | bool | `true` |  |
| postgresql.auth.password | string | `"odkcentral"` |  |
| postgresql.auth.username | string | `"odkcentral"` |  |
| postgresql.backups.bucketAccessKeyId | string | `""` |  |
| postgresql.backups.bucketEndpoint | string | `"https://scality02.wurnet.nl"` |  |
| postgresql.backups.bucketLifeCycle | int | `30` |  |
| postgresql.backups.bucketName | string | `""` |  |
| postgresql.backups.bucketPath | string | `""` |  |
| postgresql.backups.bucketSecretAccessKey | string | `""` |  |
| postgresql.backups.enabled | bool | `false` |  |
| postgresql.backups.existingSecret | string | `""` |  |
| postgresql.backups.keepJobs | int | `1` |  |
| postgresql.backups.resources | object | `{}` |  |
| postgresql.backups.schedule | string | `"37 03 * * *"` |  |
| postgresql.clusterDomain | string | `"cluster.local"` |  |
| postgresql.enabled | bool | `true` |  |
| postgresql.global.imageRegistry | string | `"harbor.containers.wurnet.nl/proxy-cache"` |  |
| postgresql.image.digest | string | `""` |  |
| postgresql.image.repository | string | `"bitnamilegacy/postgresql"` |  |
| postgresql.metrics.enabled | bool | `false` |  |
| postgresql.networkPolicy.enabled | bool | `true` |  |
| postgresql.primary.persistence.size | string | `"5Gi"` |  |
| postgresql.primary.resources.limits.cpu | string | `"750m"` |  |
| postgresql.primary.resources.limits.memory | string | `"512Mi"` |  |
| postgresql.primary.resources.requests.cpu | string | `"250m"` |  |
| postgresql.primary.resources.requests.memory | string | `"256Mi"` |  |
| postgresql.readReplicas.persistence.size | string | `"5Gi"` |  |
| postgresql.readReplicas.replicaCount | int | `1` |  |
| postgresql.readReplicas.resources.limits.cpu | string | `"750m"` |  |
| postgresql.readReplicas.resources.limits.memory | string | `"512Mi"` |  |
| postgresql.readReplicas.resources.requests.cpu | string | `"250m"` |  |
| postgresql.readReplicas.resources.requests.memory | string | `"256Mi"` |  |
| pyxform.replicas | int | `1` |  |
| pyxform.resources.limits.cpu | string | `"1000m"` |  |
| pyxform.resources.limits.memory | string | `"1024Mi"` |  |
| pyxform.resources.requests.cpu | string | `"250m"` |  |
| pyxform.resources.requests.memory | string | `"256Mi"` |  |
| redis.cache.resources.limits.cpu | string | `"200m"` |  |
| redis.cache.resources.limits.memory | string | `"64Mi"` |  |
| redis.cache.resources.requests.cpu | string | `"100m"` |  |
| redis.cache.resources.requests.memory | string | `"32Mi"` |  |
| redis.main.resources.limits.cpu | string | `"200m"` |  |
| redis.main.resources.limits.memory | string | `"64Mi"` |  |
| redis.main.resources.requests.cpu | string | `"100m"` |  |
| redis.main.resources.requests.memory | string | `"32Mi"` |  |
| redis.persistence.accessMode | string | `"ReadWriteOnce"` |  |
| redis.persistence.enabled | bool | `true` |  |
| redis.persistence.size | string | `"500Mi"` |  |
| redis.persistence.storageClass | string | `"default"` |  |
| service.env[0].name | string | `"SERVICE_NODE_OPTIONS"` |  |
| service.env[0].value | string | `"--max-old-space-size=1536"` |  |
| service.persistence.accessMode | string | `"ReadWriteOnce"` |  |
| service.persistence.enabled | bool | `true` |  |
| service.persistence.size | string | `"500Mi"` |  |
| service.persistence.storageClass | string | `"default"` |  |
| service.resources.limits.cpu | string | `"500m"` |  |
| service.resources.limits.memory | string | `"2048Mi"` |  |
| service.resources.requests.cpu | string | `"250m"` |  |
| service.resources.requests.memory | string | `"256Mi"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
