# Fuse on Spring Boot Ansible playbooks

Provision and deploy Fuse integration packaged as Spring Boot applications.

## Run the playbook

`ansible-playbook playbook.yml -i {inventory} -e app_name=example-app -e app_version=1.0.0 -e app_artifact_path=files/hello-1.0.0.jar`

Alternatively, an `app_artifact_url` can be specified to download the Spring Boot jar from an HTTP endpoint.

## Test with Vagrant
- place sample jar in `files` directory or provide a default artifact URL
- `vagrant up`

If you're looking for a sample service that works with this playbook, checkout
this simple [RESTlet example](https://github.com/davgordo/fuse-restlet-spring-boot)
