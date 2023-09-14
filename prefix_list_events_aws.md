# Prefix List Creation Events AWS 

event from cloud.audit_logs where cloud.type = 'aws' AND operation = 'CreateManagedPrefixList' AND json.rule = $.errorMessage does not exist ADDCOLUMN $.requestParameters.CreateManagedPrefixListRequest.PrefixListName 

//json.rule = $.errorMessage does not exist > If an error message occurs, prefixlist has not been created. We are able to filter out the only real created security groups with this filter. 

------------
# Prefix List Creation Events AWS  without 'CHG' tag Events AWS 

event from cloud.audit_logs where cloud.type = 'aws' AND operation = 'CreateManagedPrefixList' AND json.rule = ($.responseElements.CreateManagedPrefixListResponse.prefixList.tagSet.item[*].value does not exist OR $.responseElements.CreateManagedPrefixListResponse.prefixList.tagSet.item[*].value does not contain 'CHG') AND $.errorMessage does not exist ADDCOLUMN $.requestParameters.CreateManagedPrefixListRequest.PrefixListName $.requestParameters.CreateManagedPrefixListRequest.PrefixListName $.responseElements.CreateManagedPrefixListResponse.prefixList.tagSet.item[*].value 

------------
# Prefix List Remove Events AWS 

event from cloud.audit_logs where cloud.type = 'aws' AND operation = 'DeleteManagedPrefixList' AND json.rule = $.errorCode != '' ADDCOLUMN $.requestParameters.DeleteManagedPrefixListRequest.PrefixListId
