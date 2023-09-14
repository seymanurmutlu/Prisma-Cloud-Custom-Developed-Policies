# Firewall rule on GCP allows SSH port 22 traffic from except certain IPs

`config from cloud.resource where cloud.type = 'gcp' AND api.name = 'gcloud-compute-firewall-rules-list' AND json.rule = disabled is false and direction equals INGRESS and (allowed[?any( (ports is member of (22) or ports contains _Port.inRange(22,22) or ports does not exist) and (IPProtocol contains tcp or IPProtocol contains "all" ))] exists) and (sourceRanges[*] size does not equal 3 or (sourceRanges[*] does not contain "MY IP1" or sourceRanges[*] does not contain "MY IP2" or sourceRanges[*] does not contain "MY IP3" ))`

# Firewall rule on GCP allows RDP port 22 traffic from except certain IPs

`config from cloud.resource where cloud.type = 'gcp' AND api.name = 'gcloud-compute-firewall-rules-list' AND json.rule = disabled is false and direction equals INGRESS and (allowed[?any( (ports is member of (3389) or ports contains _Port.inRange(3389,3389) or ports does not exist) and (IPProtocol contains tcp or IPProtocol contains "all" ))] exists) and (sourceRanges[*] size does not equal 3 or (sourceRanges[*] does not contain "MY IP1" or sourceRanges[*] does not contain "MY IP2" or sourceRanges[*] does not contain "MY IP3")) `
