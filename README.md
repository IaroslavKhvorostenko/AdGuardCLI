<p align="center">
<picture>
<source media="(prefers-color-scheme: dark)" srcset="https://cdn.adguard.com/public/Adguard/Common/Logos/ag_logo_dark_cli.svg" width="300px" alt="AdGuard CLI" />
<img src="https://cdn.adguard.com/public/Adguard/Common/Logos/ag_logo_light_cli.svg?" width="300px" alt="AdGuard CLI" />
</picture>
</p>

<h3 align="center">Tool to protect against ads, trackers and malicious websites</h3>

<p align="center">
  Designed for command-line users 
</p>

<p align="center">
    <a href="https://adguard.com/">Website</a> |
    <a href="https://reddit.com/r/Adguard">Reddit</a> |
    <a href="https://twitter.com/AdGuard">Twitter</a> |
    <a href="https://t.me/adguard_en">Telegram</a>
    <br /><br />
    <a href="https://github.com/AdguardTeam/AdguardCLI/releases/"><img src="https://img.shields.io/github/tag/AdguardTeam/AdGuardCLI.svg?label=release&filter=*release" alt="Latest release" /></a>
    <a href="https://github.com/AdguardTeam/AdguardCLI/releases/"><img src="https://img.shields.io/github/tag-pre/AdguardTeam/AdGuardCLI.svg?label=beta&filter=*beta" alt="Beta version" /></a>
    <a href="https://github.com/AdguardTeam/AdguardCLI/releases/"><img src="https://img.shields.io/github/tag-pre/AdguardTeam/AdGuardCLI.svg?label=nightly&filter=*nightly" alt="Nightly version" /></a>

<p align="center">
<img src="https://cdn.adtidy.org/content/release_notes/ad_blocker/cli/v1.0/adguardcli-proxy_start.gif" width = "600"px>
</p>

> ### Disclaimer
>* AdGuard CLI is not an open source project. We use GitHub as an open bug tracker for users to see what developers are working on. However, we at AdGuard create [a lot of open source software](https://github.com/search?o=desc&q=topic%3Aopen-source+org%3AAdguardTeam+fork%3Atrue&s=stars&type=Repositories).
> * Privacy policy: https://adguard.com/privacy.html

## Overview

AdGuard CLI is the command-line version of AdGuard Ad Blocker. Learn more about it [in our Knowledge base](https://adguard.com/kb/adguard-for-linux/).

## Installation

To install the latest version of AdGuard CLI, run the following command:

Release channel:

```shell
curl -fsSL https://raw.githubusercontent.com/AdguardTeam/AdGuardCLI/release/install.sh | sh -s -- -v
```

Beta channel:

```shell
curl -fsSL https://raw.githubusercontent.com/AdguardTeam/AdGuardCLI/beta/install.sh | sh -s -- -v
```

Nightly channel:

```shell
curl -fsSL https://raw.githubusercontent.com/AdguardTeam/AdGuardCLI/nightly/install.sh | sh -s -- -v
```

## Verify Releases

Inside an archive file, there is a small file with a `.sig` extension that contains the signature data. In a hypothetical situation where the binary file inside an archive is replaced by someone, you’ll know it isn’t an official release from AdGuard.

To verify the signature, you need to have the `openssl` tool version 1.1.1 or newer installed.

First, import the AdGuard public key:

```shell
curl -fsSL https://raw.githubusercontent.com/AdguardTeam/AdGuardCLI/master/adguard_ed25519_pubkey.pem -o adguard_ed25519_pubkey.pem
```

It will download public key, which should have the value `MCowBQYDK2VwAyEAN0NPZFtolGN+Cjyorh4Wo91vnBlLLQiWkbujeHDYbok=`.

Then, verify the signature:

```shell
openssl pkeyutl -verify -inkey adguard_ed25519_pubkey.pem -pubin -sigfile /opt/adguard-cli/adguard-cli.sig -in /opt/adguard-cli/adguard-cli -rawin
```

If you use a custom installation path, replace `/opt/adguard-cli` with the path to the adguard-cli and its signature file.

You’ll see the following message:

```
Signature Verified Successfully
```

### Usage

Run `adguard-cli [command]` to use AdGuard CLI. Below are the available commands and their options:

### Options

- `-h, --help`                   Print this help message and exit
- `--help-all`                   Show all available commands, subcommands, and options
- `-v, --version`                Display program version information and exit

### Subcommands

- `activate`                     Activate an AdGuard license
- `reset-license`                Reset an AdGuard license
- `configure`                    Run the configuration wizard
- `start`                        Start AdGuard CLI
- `stop`                         Stop AdGuard CLI
- `status`                       Show the status of AdGuard CLI
- `license`                      Show license information
- `config`                       Configure AdGuard CLI
    - `show`                     Show current configuration from `proxy.yaml`
    - `set`                      Set a single option in `proxy.yaml`, e.g.:
                                    - `listen_ports.http_proxy` sets the HTTP listen port
                                    - `proxy_mode` sets the proxy mode (manual or auto)
    - `get`                      Get a single option from `proxy.yaml`
- `check-update`                 Check for updates
- `update`                       Update AdGuard CLI
    - `-v, --verbose`            Show update script output
- `filters`                      Manage filters
    - `list`                     List installed and added filters, or all available filters if `--all` is specified
    - `add`                      Add internal filter, by ID or name
    - `install`                  Install a custom filter
    - `remove`                   Remove internal or custom filter
    - `enable`                   Enable the filter (Rules from this filter will be applied)
    - `disable`                  Disable the filter (Rules from this filter will no longer be applied)
    - `update`                   Update filters
- `export-logs`                  Export logs to a zip file
    - `-o, --output TEXT`        Path to the output artifact. Can be a directory
    - `-f, --force`              Overwrite the output artifact without asking
