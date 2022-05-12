# ansible-instana-agent role

> This repository is forked from instana/instana-agent-ansible - a blueprint to show how the Instana agent installation and configuration can be automated with 


Here is an example of a playbook with the various configuration options:

## Example:

```yaml
---
  - hosts: all
    become: yes
    roles:
      - ansible-instana-agent
    vars:
      instana_agent_flavor: "dynamic"
      instana_agent_jdk: "/opt/jdk"
      instana_agent_updates_enabled: yes
      instana_agent_updates_interval: "DAY"
      instana_agent_updates_time: "04:30"
      instana_agent_zone: "prod"
      instana_agent_agent_key: <YOUR_INSTANA_AGENT_KEY>
      instana_agent_endpoint_host: <YOUR_INSTANA_REGION_ENDPOINT:saas-us-west-2.instana.io>
      instana_agent_endpoint_port: 443
```

## Flavors

**`instana-agent-dynamic`**

This blank agent comes bundled with a JDK and is configured to download all necessary sensors when it starts. Additionally, it is configured to update its set of sensors on a daily basis.

**`instana-agent-static`**

This "gated" agent package is supposed to not connect to the internet at all. It comes with all the recent sensors and a JDK, and is your package of choice when you run a tight firewall setup.

## Monitoring endpoint

If you're an onprem customer, please specify your hostname and port in the corresponding attributes. If you're using our SaaS offering, and don't know which endpoint the agent should send to, feel free to ask our sales team.

## Supported operating systems

See [instana official documentation](https://docs.instana.io/quick_start/agent_setup/).

## Attributes

* See [attributes file](defaults/main.yml).

## License and Authors

This playbook is being submitted and maintained under the [Apache v2.0 License](https://github.com/instana/ansible-role/blob/master/LICENSE).

* [Bastian Spanneberg](https://github.com/spanneberg)
* [Stefan Staudenmeyer](https://github.com/doerteDev)
* [Marcel Birkner](https://github.com/marcelbirkner)
* [James Parker](https://github.com/jmsprkr)

Copyright 2018, INSTANA Inc.
