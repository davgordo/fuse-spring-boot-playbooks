# Fuse on Spring Boot Ansible playbooks

Provision and deploy Fuse integration packaged as Spring Boot applications.

## Prepare host environment

`ansible-playbook environment.yml -i {inventory}`

## Provision a new application

`ansible-playbook application.yml -i {inventory} -e app_name=example-app`

## Deploy a build

`ansible-playbook deployment.yml -i {inventory} -e app_name=example-app -e app_version=1.0.0 -e app_artifact_path=hello-1.0.0.jar`

Alternatively, an `app_artifact_url` can be specified to download the Spring Boot jar from an HTTP endpoint.

Note that Jenkins can select to only execute specific phases of the deployment playbook with tags. e.g. `-t health-check`.
