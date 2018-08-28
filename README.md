ansible-role-grafana-in-docker
=========
Ansible galaxy role to deploy [Grafana](https://grafana.com/) in docker


Requirements
------------

The following packages have to be installed and well configured on the host :
- [Docker-ce](https://docs.docker.com/engine/installation/)

Role Variables
--------------

### Mandatory variables (Grafana will not be connected to any database if those are not set)
Specify the following variable to specify the datasource Grafana should connect to :
```yaml
datasource_type: "" # can be CloudWatch, Elasticsearch, Graphite, InfluxDB, MySQL, OpenTSDB, PostgreSQL or Prometheus
datasource_database: ""
datasource_hostname: "" # hostname of the server the db is running on
datasource_port: "" # database port
```

### Overridable default variables
```yaml
grafana_container_name: "grafana"
grafana_docker_networks: []
grafana_container_restart_policy: "always"
grafana_conf_location: "/opt/docker-data/{{ grafana_container_name }}/conf"
```

Dependencies
------------


Example Playbook
----------------

ansible-playbook tests/test.yml --ask-become-pass -e grafana_conf_location="$(pwd)/.workdir/"
On MacsOS due to Docker Machine root limitation, add : -e ansible_become_user="$(whoami)"

	- hosts: localhost
	  roles:
	    - ../ansible-role-grafana-in-docker


License
-------

MIT

Author Information
------------------

https://github.com/lribiere/ansible-role-grafana-in-docker.git