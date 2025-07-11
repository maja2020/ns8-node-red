#node-red as ns8 module

refs: node-red:4.0.9 docker.io

## Install

Instantiate the module with:

    add-module ghcr.io/maja2020/node-red:1.0.2 1

The output of the command will return the instance name.
Output example:

    {"module_id": "node-red1", "image_name": "node-red", "image_url": "ghcr.io/maja2020/node-red:1.0.2"}

## Configure

Launch configure-module, by setting the following parameters:

- host: a fully qualified domain name for the application
- http2https: enable or disable HTTP to HTTPS redirection (true/false)
- lets_encrypt: enable or disable Let's Encrypt certificate (true/false)

Example:
```
api-cli run configure-module --agent module/node-red1 --data - <<EOF
{
  "host": "mynodered.domain.com",
  "http2https": true,
  "lets_encrypt": false
}
EOF
```
The above command will:
    start and configure the kickstart instance
    configure a virtual host for trafik to access the instance

## Uninstall

To uninstall the instance:

    remove-module --no-preserve node-red1

## Update
api-cli run update-module --data '{"module_url":"ghcr.io/maja2020/node-red:1.0.2","instances":["node-red1"],"force":true}'

# Known issues
None at the moment, but:
- Still some unsolved erorrs in the Github automated test scripts