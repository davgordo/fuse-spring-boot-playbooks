# Fuse on Spring Boot Ansible playbook

Provision and deploy Fuse integration packaged as Spring Boot applications.

## Prepare host environment

`ansible-playbook environment.yml -i {inventory}`

## Provision a new application

`ansible-playbook application.yml -i {inventory} -e app_name=example-app`

## Deploy a build

`ansible-playbook deployment.yml -i {inventory} -e app_name=example-app -e app_version=1.0.0 -e app_artifact_path=hello-1.0.0.jar`
