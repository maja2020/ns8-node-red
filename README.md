#ns8-node-red
refs: node-red:4.0.9 docker.io

## Install

Instantiate the module with:

    add-module ghcr.io/maja2020/ns8-node-red:latest 1

The output of the command will return the instance name.
Output example:

    {"module_id": "node-red1", "image_name": "node-red", "image_url": "ghcr.io/maja2020/ns8-node-red:latest"}

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

# Known issues
None at the moment, but:
- Installing works fine, updates still to be tested
- Still some unsolved erorrs in the Github automated test scripts
- Publish the version of the package on Github