# DNS Introducer Healthcheck

Runs alongside the dns-introducer/seeder service in chia-blockchain and checks for dns responses. If DNS service is up and serving requests, this service responds with HTTP 200 on port 53/TCP, otherwise, it responds with an HTTP 500.
Useful for any healthcheck that needs to check a TCP port, since the seeder only responds on UDP.

## Installation

Download the correct executable file from the release page and run. If you are on debian/ubuntu, you can install using the apt repo, documented below.

### Apt Repo Installation

#### Set up the repository

1. Update the `apt` package index and install packages to allow apt to use a repository over HTTPS:

```shell
sudo apt-get update

sudo apt-get install ca-certificates curl gnupg
```

2. Add Chia's official GPG Key:

```shell
curl -sL https://repo.chia.net/FD39E6D3.pubkey.asc | sudo gpg --dearmor -o /usr/share/keyrings/chia.gpg
```

3. Use the following command to set up the stable repository.

```shell 
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/chia.gpg] https://repo.chia.net/dns-introducer-healthcheck/debian/ stable main" | sudo tee /etc/apt/sources.list.d/dns-introducer-healthcheck.list > /dev/null
```

#### Install DNS Introducer Healthcheck

1. Update the apt package index and install the latest version of DNS Introducer Healthcheck

```shell
sudo apt-get update

sudo apt-get install dns-introducer-healthcheck
```

## Usage

First, install [chia-blockchain](https://github.com/Chia-Network/chia-blockchain). DNS Introducer Healthcheck expects to be run on the same machine as the chia blockchain installation.

`dns-introducer-healthcheck` will start the app on the default port `53/TCP`.

### Configuration

Configuration options can be passed using environment variables.

`DNS_HOSTNAME` Overrides the default hostname (`dns-introducer.chia.net`) with an alternate hostname to check for DNS responses.
