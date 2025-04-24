# OCP-AGENT-DISCO
These ansible roles will setup all files needed for mirroring and installing a (fully) disconnected ocp environment using the agent based installation method and the oc-mirror plugin
It tries to reduce the time needed to prepare a PoC within this environments. It is not ment for production purposes.

## Problems this role tries to solve

1. Inconsistencies in the agent-config.yaml and the install-config.yaml and between both of them, when preparing them by hand
2. Tedious imagesetconfiguration fillout by searching operators, channels and versions.
3. version inconsistencies between synced images, openshift installer and other ocp tools

By executing the playbook you will get:

1. A ready to use imagesetconfiguration
2. a ready to use agent-config and install-config
3. a offline mirror tar with the images for transport

## HowTo

1. install requirements with `ansible-galaxy install -r requirements.yml`
1. Define your variables for the environment in `ocp_disco_vars.yaml`. There is an example file `ocp_disco_vars_example.yaml` which you can use as a starting point. There are some assumptions about the machine network being a /24 network in defaults, so you might have to change more network related defaults.
2. if you do not set `ocp_rh_pull_secret` with your red hat [pull secret](https://console.redhat.com/openshift/downloads#tool-pull-secret), please login before executing the playbook. Otherwise it fails.
3. run playbook with `ansible-playbook ansible/playbook.yaml` (--ask-become-pass)
4. obtain everything you need in $HOME/ocp_tools folder (default)

## TODO

[] Enable RHEL8/RHEL9 download tool choice

## OpenStack

1. create ~/.config/openstack/clouds.yaml with the necessary configuration

```yaml
clouds:
  default:
    auth:
      auth_url: https://keystone.example.com:443/v3/
      username: "username"
      project_id: 12753c10d9c948c0134239359b9b8352
      project_name: "demo"
      user_domain_name: "Default"
    region_name: "DefaultRegion"
    interface: "public"
    identity_api_version: 3
```
