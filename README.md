This is a modified private clone of https://github.com/wazuh/wazuh-kubernetes. The config is modified to suit the kubernetes cluster of the CTF challenge.

instructions:
$ git clone https://github.com/KJ02024/wazuhfontysICT.git
$ cd wazuhfontysICT

generate certs:
$ wazuh/certs/indexer_cluster/generate_certs.sh
$ wazuh/certs/dashboard_http/generate_certs.sh

enjoy
