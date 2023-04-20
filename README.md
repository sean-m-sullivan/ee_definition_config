# ee_definition_config
Use the EE builder using configuration Job in Controller
[Blog post discussing how to use this repo](https://www.redhat.com/architect/ansible-execution-environment-automated-build)

## Files and purposes

### Configure Controller
Configure controller to create all controller objects to create a Job template that can create an EE. 
Changes will need to made to credentials and the inventory to be applicable to your installation.

### EE Builder Survey
The playbook used in the controller Job template to create an EE.

### Survey Inputs
File to copy survey inputs from to get examples of format.

### redhat_cop.ee_utilities 1.02 tarball
Temporary tarball while the collection update is being Reviewed.

### EE builder base
Base EE definition file to create an EE with a playbook.

### EE Venv migrate
Playbook that when pointed at a Tower will create Execution environments based on the Towers defined Venvs.

### EE Builder local survey
Test file for testing survey options

## Running this on a container
This is NOT Recomended to do, it will run all containers in privledged mode. "user root inside of a container will have the same access as root on the host system"
Building an EE will work if on a container, the following option needs to be changed in the Automation controller.
/var/lib/awx/venv/awx/lib/python3.9/site-packages/awx/settings/defaults.py
```text
DEFAULT_CONTAINER_RUN_OPTIONS = ['--privileged','--network', 'slirp4netns:enable_ipv6=true']
```

Afterward restart automation-controller and nginx service

The container to then use to run is quay.io/acme_corp/ansible-runner
