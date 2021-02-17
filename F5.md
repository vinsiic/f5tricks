# What to do if F5 SSLO upgrade from 15.x to 16.x goes wrong and SSLO page show "Access forbidden!"

## list all blocks
`restcurl shared/iapp/blocks/`

## list all SSLO block id's
`restcurl shared/iapp/blocks/ | jq -r '.items[]  | select(.name | startswith("f5-ssl-orchestrator")) | .id'`


## delete specific block
`curl -k -u username:password -X DELETE -H "Accept: application/json" -d '{"id": "1e66f5dc-3329-30c3-80b2-46efb7adb673"}' https://localhost/mgmt/shared/iapp/blocks`

`restcurl shared/iapp/blocks/ -X DELETE -d '{"id": "1e66f5dc-3329-30c3-80b2-46efb7adb673"}'`


## install SSLO package
`curl -u username:password -X POST http://localhost:8100/mgmt/shared/iapp/package-management-tasks -d '{ "operation":"INSTALL","packageFilePath": "/var/config/rest/downloads/f5-iappslx-ssl-orchestrator-16.0.0-8.3.11.noarch.rpm"}'`

`restcurl -X POST shared/iapp/package-management-tasks -d '{ "operation":"INSTALL","packageFilePath": "/var/config/rest/downloads/f5-iappslx-ssl-orchestrator-16.0.0-8.3.11.noarch.rpm"}'`


## show install progress
`curl -k -u username:password https://localhost/mgmt/shared/iapp/package-management-tasks/14418d92-9926-4262-becc-9ee225a07fd3`

`restcurl shared/iapp/package-management-tasks/92b00285-02a6-4bc0-8bc8-394ccd1c7421`
