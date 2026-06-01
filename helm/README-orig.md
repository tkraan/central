# ODK Central - Helm Chart

Central is the ODK server. It manages user accounts and permissions, stores form definitions, and allows data collection clients like ODK Collect to connect to it for form download and submission upload.

## Installation

To install this Helm chart, run: helm install odkcentral oci://harbor.containers.wurnet.nl/wur/odk -f values.yaml
