# pro_vision.jenkins_pv

This role manages the installation, update and uninstallation of Plugins
on pro!vision Jenkins instances.

It covers Plugins that are not already covered by:

* [wcm_io_devops.jenkins_pipeline_library](https://github.com/wcm-io-devops/ansible-jenkins-pipeline-library)
* [pro_vision.jenkins_pv_pipeline_library](https://github.com/pro-vision/ansible-jenkins-pv-pipeline-library)

## Versioning

The Version number will follow the following versioning schema:

`v[JenkinsVersion]-[ReleaseCount]`

So for example:
* `v2.138.1-1` - first release for Jenkins 2.107.2
* `v2.107.2-2` - second release for Jenkins 2.107.2
* `v2.107.2-N` - nth release for Jenkins 2.107.2
* `v2.138.1-1` - first release for Jenkins 2.138.1

## Requirements

This role requires Ansible 2.4 or higher and a running Jenkins on the
target instance.

## Role Variables

Available variables are listed below, along with their default values:

    jenkins_pv_admin_username: admin

Jenkins admin username.

    jenkins_pv_admin_password: admin

Jenkins admin password.

    jenkins_pv_jenkins_home: /var/lib/jenkins

Path to the jenkins directory.

    jenkins_pv_jenkins_hostname: localhost

Hostname of the jenkins instance.

    jenkins_pv_jenkins_port: 8080

HTTP port of the jenkins instance.

    jenkins_pv_jenkins_url_prefix: ""

Url prefix of the jenkins instance, e.g. when running in tomcat.

    jenkins_pv_jenkins_base_url: "http://{{ jenkins_pv_jenkins_hostname }}:{{ jenkins_pv_jenkins_port }}{{ jenkins_pv_jenkins_url_prefix }}"

The base url of the jenkins instance.

    jenkins_pv_updates_expiration: 86400

Maximum seconds since the last jenkins plugin update check.

    jenkins_pv_updates_timeout: 60

Timeout for jenkins update operation.

    jenkins_pv_debug: false

When set to enable the role will log some debug information.

    jenkins_pv_plugins_present: [...]

Plugins and their versions that must be present on a p!v Jenkins instance.

:bulb: Since this list is long please refer to
[defaults](defaults/main.yml)

Plugins and their versions that must be present on p!v jenkins instances.

    jenkins_pv_plugins_absent: []

Plugins that must be absent on p!v jenkins instances.

## Dependencies

This role depends on the
[wcm_io_devops.jenkins_plugins](https://github.com/wcm-io-devops/ansible-jenkins-plugins)
role to install/uninstall the plugins needed by the
[jenkins-pipeline-library](https://github.com/wcm_io_devops.jenkins_pipeline_library)

As transitive dependency this role uses the
[wcm_io_devops.jenkins_facts](https://github.com/wcm-io-devops/ansible-jenkins-facts)
role to retrieve the list of installed plugins from the Jenkins
instance.
