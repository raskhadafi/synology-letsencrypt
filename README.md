# synology-letsencrypt

Create and maintain a [Let's Encrypt](https://letsencrypt.org/) certificate on a Synology NAS.

Uses [lego](https://go-acme.github.io/lego/) and the [ACME DNS-01 challenge](https://letsencrypt.org/docs/challenge-types/#dns-01-challenge) for any of the supported [DNS Providers](https://go-acme.github.io/lego/dns/).

## Install & Update Script

To **install** or **update** synology-letsencrypt, run the [install script](install.sh). To do that, either download and run the script manually, or use the following cURL command:

```sh
curl -sSL https://raw.githubusercontent.com/raskhadafi/synology-letsencrypt/master/install.sh | bash
```

## Configuration

Update `/usr/local/etc/synology-letsencrypt/env` with domain(s), email, and DNS API-key:

```sh
DOMAINS=(--domains "example.com" --domains "*.example.com")
EMAIL="user@example.com"

## Specify DNS Provider (this example is from https://go-acme.github.io/lego/dns/infomaniak/
DNS_PROVIDER="infomaniak"
export INFOMANIAK_ACCESS_TOKEN=XXXXXXX
```

Now you should be able to run `/usr/local/bin/synology-letsencrypt.sh`.

To schedule a daily task, log into the Synology DSM and add a user-defined script:

    Synology DSM -> Control Panel -> Task Scheduler
       Create -> Scheduled Task -> User-defined script
          General -> User = root
          Task Settings -> User-defined script = /usr/local/bin/synology-letsencrypt.sh

## Uninstall

To **uninstall** synology-letsencrypt, run the [uninstall script](uninstall.sh). To do that, either download and run the script manually, or use the following cURL command:

```sh
curl -sSL https://raw.githubusercontent.com/raskhadafi/synology-letsencrypt/master/uninstall.sh | bash
```
