# OCP-AGENT-DISCO
These ansible roles will setup all files needed for mirroring and installing a (fully) disconnected ocp environment using the agent based installation method and the oc-mirror plugin
It tries to reduce the time needed to prepare a PoC within this environments. It is not ment for production purposes.

# Problems this role tries to solve
1. Inconsistencies in the agent-config.yaml and the install-config.yaml and between both of them, when preparing them by hand
2. Tedious imagesetconfiguration fillout by searching operators, channels and versions.
3. version inconsistencies between synced images, openshift installer and other ocp tools

By executing the playbook you will get:
1. A ready to use imagesetconfiguration
2. a ready to use agent-config and install-config
3. a offline mirror tar with the images for transport
