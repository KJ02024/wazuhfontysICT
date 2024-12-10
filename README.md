This is a modified clone of https://github.com/wazuh/wazuh-kubernetes. The config and yaml files are modified or added to suit the kubernetes cluster of the fontys CTF challenge.

instructions:

$ git clone https://github.com/KJ02024/wazuhfontysICT.git

$ cd wazuhfontysICT

generate certs:

$ bash wazuh/certs/indexer_cluster/generate_certs.sh

$ bash "wazuh/certs/dashboard_http/generate_certs (1).sh"

We apply a specific label to the node node-role.kubernetes.io/storage=true so that Kubernetes knows on which node the hostPath volumes should reside this makes sure that Pods needing those volumes are scheduled onto the correct node that actually has the data directory avoiding "volume node affinity" conflicts.

Static provisioning in a small CTF environmentlike a CTF we likely know exactly how much storage we need and where it should be located. Using static provisioning (manually creating PersistentVolumes) is simpler and avoids resourseusage of running dynamic provisioning components. It reduces complexity and resource usage, if we dont label the node where we want to run wazuh it will cause errors with current conf as i set it.

$  kubectl label nodes <node-name> node-role.kubernetes.io/storage=true

Apply conf en images

$ kubectl apply -k envs/local-env/
