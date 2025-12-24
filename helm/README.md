# ODK Central - Helm Chart

Central is the ODK server. It manages user accounts and permissions, stores form definitions, and allows data collection clients like ODK Collect to connect to it for form download and submission upload.

## Installation

To install this Helm chart, run: helm install odkcentral oci://*repository-of-helmrepo* -f values.yaml
# odk

![Version: 1.0.0](https://img.shields.io/badge/Version-0.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v2025.4.0](https://img.shields.io/badge/AppVersion-v2024.3.2-informational?style=flat-square)

The standard for mobile data collection

## Source Code

* <https://github.com/getodk/central>
* <https://github.com/getodk/central/pkgs/container/central-service/versions?filters[version_type]=tagged>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | postgresql | 15.5.38 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| image.registry | string | `"docker.io"` | Registry where the common images can be pulled  |
| image.odkregistry | string | `"ghcr.io/getodk"` | Registry where ghcr.io/getodk/* can be pulled from |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| nameOverride | string | `""` |  |
| fullnameOverride | string | `""` |  |
| odk.existingSecret | string | `""` | Create a secret manually containing the fields shown below (recommended). |
| odk.secrets.DOMAIN | string | `"odkcentral.yourdomain.tld"` | the domain for the ODK Central instance |
| odk.secrets.ENKETO_API_KEY | string | `"enketo_api_key_secret"` | the Enketo API key  |
| odk.secrets.ENKETO_LESS_SECRET | string | `"enketo_less_secret"` | the Enketo Less API key |
| odk.secrets.ENKETO_SECRET | string | `"enketo_secret"` | The Enketo secret used for the enketo service |
| odk.secrets.EMAIL_HOST | string | `""` | the hostname for the final mailserver |
| odk.secrets.EMAIL_USER | string | `""` | the user for the final mailserver |
| odk.secrets.EMAIL_PASSWORD | string | `""` | the password for the user on the final mailserver |
| odk.secrets.EMAIL_PORT | int | `587` | the default email port for the final mailserver |
| odk.secrets.EMAIL_SECURE | string | `"true"` | whether to use TLS for the final mailserver |
| odk.secrets.EMAIL_FROM | string | `"odkcentral@yourdomain.tld"` | the email address that is used to send emails from the ODK Central instance |
| odk.secrets.DB_NAME | string | `""` | the database name for the ODK Central instance |
| odk.secrets.DB_USER | string | `""` | the database user for the ODK Central instance |
| odk.secrets.DB_PASSWORD | string | `""` | the database password for the ODK Central instance |
| odk.secrets.DB_HOST | string | `""` | the database host for the ODK Central instance |
| odk.secrets.PGSSLMODE | string | `"true"` | use true for full verification, false to disable verification, no-verify to skip verification but use SSL |
| odk.secrets.SSL_TYPE | string | `"upstream"` | SSL mode for the nginx server |
| odk.user | object | `{"existingSecret":"","password":"admin12345678","username":"admin@yourdomain.tld"}` | The initial admin user configuration |
| odk.user.username | string | `"admin@yourdomain.tld"` | the username for the initial admin user |
| odk.user.password | string | `"admin12345678"` | the password for the initial admin user |
| service | object | `{"env":[{"name":"SERVICE_NODE_OPTIONS","value":"--max-old-space-size=1536"}],"persistence":{"accessMode":"ReadWriteOnce","enabled":true,"size":"500Mi","storageClass":"default"},"resources":{"limits":{"cpu":"500m","memory":"2048Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}}` | The service is the main component of ODK Central, handling requests and serving the web application. |
| service.persistence | object | `{"accessMode":"ReadWriteOnce","enabled":true,"size":"500Mi","storageClass":"default"}` | Storage configuration for the service |
| service.env | list | `[{"name":"SERVICE_NODE_OPTIONS","value":"--max-old-space-size=1536"}]` | to roughly 75% of service.resources.limits.memory |
| enketo | object | `{"image":"ghcr.io/enketo/enketo:7.5.0","resources":{"limits":{"cpu":"500m","memory":"512Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}}` | Configuration for the ODK Central enketo service |
| enketo.image | string | `"ghcr.io/enketo/enketo:7.5.0"` | Enketo image to pull |
| nginx | object | `{"resources":{"limits":{"cpu":"200m","memory":"64Mi"},"requests":{"cpu":"100m","memory":"32Mi"}}}` | Configuration for the ODK Central nginx service |
| postfix | object | `{"enabled":true,"overwriteFrom":"ODK Sandbox <noreply@odkcentral.yourdomain.tld>","resources":{"limits":{"cpu":"100m","memory":"128Mi"},"requests":{"cpu":"50m","memory":"64Mi"}},"serverHostname":"postfix.yourdomain.tld"}` | Configuration for the ODK Central mail service |
| redis | object | `{"cache":{"resources":{"limits":{"cpu":"200m","memory":"64Mi"},"requests":{"cpu":"100m","memory":"32Mi"}}},"main":{"resources":{"limits":{"cpu":"200m","memory":"64Mi"},"requests":{"cpu":"100m","memory":"32Mi"}}},"persistence":{"accessMode":"ReadWriteOnce","enabled":true,"size":"500Mi","storageClass":"default"}}` | The standard Redis images can be found on Docker hub |
| pyxform | object | `{"replicas":1,"resources":{"limits":{"cpu":"1000m","memory":"1024Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}}` | Configuration for the ODK Central pyxform service |
| postgresql | object | `{"architecture":"standalone","auth":{"database":"odkcentral","enablePostgresUser":true,"password":"odkcentral","username":"odkcentral"},"backups":{"bucketAccessKeyId":"","bucketEndpoint":"https://s3.yourdomain.tld","bucketLifeCycle":30,"bucketName":"","bucketPath":"","bucketSecretAccessKey":"","enabled":false,"existingSecret":"","keepJobs":1,"resources":{},"schedule":"37 03 * * *"},"clusterDomain":"cluster.local","enabled":true,"global":{"imageRegistry":"docker.io"},"global.defaultStorageClass":"default","image":{"digest":"","repository":"bitnamilegacy/postgresql"},"metrics":{"enabled":false},"networkPolicy":{"enabled":true},"primary":{"persistence":{"size":"5Gi"},"resources":{"limits":{"cpu":"750m","memory":"512Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}},"readReplicas":{"persistence":{"size":"5Gi"},"replicaCount":1,"resources":{"limits":{"cpu":"750m","memory":"512Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}}}` | Values for the postgresql chart can be found here:https://github.com/bitnami/charts/blob/main/bitnami/postgresql/README.md |
| postgresql.backups | object | `{"bucketAccessKeyId":"","bucketEndpoint":"https://s3.yourdomain.tld","bucketLifeCycle":30,"bucketName":"","bucketPath":"","bucketSecretAccessKey":"","enabled":false,"existingSecret":"","keepJobs":1,"resources":{},"schedule":"37 03 * * *"}` | Writes postgresql dumps to an S3 compatible bucket. |
| postgresql.backups.schedule | string | `"37 03 * * *"` | Cronjob schedule for the backup job. Please keep in mind that the system is running in UTC! |
| postgresql.backups.keepJobs | int | `1` | Define how many cronjobs history needs to be retained in Kubernetes. |
| postgresql.backups.bucketEndpoint | string | `"https://s3.yourdomain.tld"` | These following 3 keys are ignored if a existingsecret is defined |
| postgresql.architecture | string | `"standalone"` | The postgresql archictectue |
| postgresql.primary | object | `{"persistence":{"size":"5Gi"},"resources":{"limits":{"cpu":"750m","memory":"512Mi"},"requests":{"cpu":"250m","memory":"256Mi"}}}` | Resources for the primary postgresql cluster |
| ingress | object | `{"annotations":{"cert-manager.io/cluster-issuer":"letsencrypt","ingress.kubernetes.io/ssl-redirect":"true","nginx.ingress.kubernetes.io/backend-protocol":"HTTP","nginx.ingress.kubernetes.io/enable-global-auth":"false","nginx.ingress.kubernetes.io/proxy-body-size":"512m","nginx.ingress.kubernetes.io/proxy-read-timeout":"25600","nginx.ingress.kubernetes.io/proxy-send-timeout":"25600"},"className":"public","enabled":true,"hosts":[{"host":"odkcentral.yourdomain.tld","paths":[{"path":"/","pathType":"Prefix"}]}],"tls":[{"hosts":["odkcentral.yourdomain.tld"],"secretName":"odkcentral.yourdomain.tld"}]}` | Configuration for the ODK Central ingress |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
