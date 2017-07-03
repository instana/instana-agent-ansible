# README.md
# Ansible Role: Instana Agent 1.x

  This ansible role installs the Instana Agent on any of these supported
  platforms:

* CentOS 6 & 7
* Redhat Enterprise Linux 6 & 7
* Amazon Linux
* Debian Jessie
* Ubuntu Xenial & Trusty
* SUSE Enterprise Linux 12 (>= sp 2)

## Requirements

* If you're running a Debian or Ubuntu system, you are required to install
apt-transport https.
* RPM-based distributions require up to date versions of openssl and nss in order to speak current ciphers with our agent repositories.
* When the agent should run in a proxied environment, the package manager needs to be configured to utilize the needed proxy.
* For "minimal" flavored agents, you'd need either an OpenJDK or Oracle JDK of the Version 8 (we support releases greater than 40) configured in the instana/agent/jdk variable.

## Role Variables

  Available variables are listed below, along with default values:

```yaml
instana:
  agent:
    mode: "apm"
    limit:
      cpu:
        enabled: true
        quota: 0.5
      memory:
        enabled: true
        maxsize: 512
    flavor: "full"
    agent_key:
    endpoint:
      host: "saas-us-west-2.instana.io"
      port: 443
    jdk: ""
    user: "root"
    group: "root"
    updates:
      enabled: true
      interval: "DAY"
      time: "04:30"
      pin: ""
    zone: ""
    tags: []
    proxy:
      enabled: false
      type: "http"
      host: ""
      port: 0
      username: ""
      password: ""
      dns: true
    mirror:
      enabled: false
      auth:
        enabled: false
        username: ""
        password: ""
      urls:
        release: ""
        shared: ""
```

## Example Playbook

```yaml
- hosts: webservers
  gather_facts: true
  roles:
    - role: instana-agent
      instana:
        agent:
          jdk: "/opt/jvm/jdk"
          flavor: "minimal"
          agent_key: "123456789-a1b2c3d4e5-abcdefg"
          endpoint:
            host: "my-on-premises-backend.machine.cluster"
            port: 1444
          zone: "QA"
          tags:
            - "provisioned"
            - "by"
            - "ansible"
```

## License

Apache 2.0
