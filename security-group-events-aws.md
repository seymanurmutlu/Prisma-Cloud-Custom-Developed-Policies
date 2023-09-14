# Security Group Creation Events AWS 
`event from cloud.audit_logs where cloud.type = 'aws' AND operation IN ('CreateSecurityGroup') ADDCOLUMN $.requestParameters.groupName $.eventTime $.resources[2].resourceName $.responseElements.tagSet.items[*].value`

----------------

# Security Group Creation without 'CHG' tag Events AWS 
`event from cloud.audit_logs where cloud.type = 'aws' AND operation IN ('CreateSecurityGroup') AND json.rule = $.responseElements.tagSet.items[*].value does not contain 'CHG' ADDCOLUMN $.requestParameters.groupName $.eventTime $.resources[2].resourceName $.responseElements.tagSet.items[*].value`

