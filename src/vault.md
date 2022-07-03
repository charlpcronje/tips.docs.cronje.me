---
title: Vault Usage
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

If you still need to install vault: [Vault Install](http://setup.docs.CRONje.ME/vault/)

## Prepare to Administer Vault

The next step is to move the `Vault` bin directory to the `PATH` environment variable with the command:

```shell
export PATH=$PATH:/opt/vault/bin
echo "export PATH=$PATH:/opt/vault/bin" >> ~/.bashrc
```

Followed by setting the environment variables for Vault by typing:

```shell
export VAULT_ADDRESS=http://10.128.0.2:8200
echo "export VAULT_ADDR=http://10.128.0.2:8200" >> ~/.bashrc
```

## Initialize and Unseal your Vault

To initialize and unseal Vault, you will first need to start Vault as a server in the dev mode. However, make sure not to run a dev server in production.

Run the following command:

```shell
vault server -dev
```

The command produces an output that includes the server configuration, the unseal key, and root token. Save the unseal key and root token values, as you will need them in the next steps.

> **Note**: As Vault does not fork, you need to open another shell or terminal to run the following commands.

Start by setting the environment variable. You will find this command as part of the output from the previous steps:

```shell
export VAULT_ADDR=’http://127.0.0.1:8200’
```

Then, run the following command with the information from the dev server’s output:

````shell
export VAULT_DEV_ROOT_TOKEN_ID=”XXXXXXXXXXXXXXXX”
````

Check the status of the server:

```shell
vault status
```

The output should display that Vault is now initialized and no longer sealed.

```shell
Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.2.3
Cluster Name    vault-cluster-18e6bce0
Cluster ID      16382125-eb14-f23a-8145-ad64eee072cf
HA Enabled      false
```