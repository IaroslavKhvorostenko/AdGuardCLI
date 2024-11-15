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

AdGuard CLI is the command-line version of AdGuard Ad Blocker.

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

To verify the signature, you need to have the `gpg` tool installed.

First, import the AdGuard public key:

```shell
gpg --keyserver 'keys.openpgp.org' --recv-key '28645AC9776EC4C00BCE2AFC0FE641E7235E2EC6'
```

Then, verify the signature:

```shell
gpg --verify /opt/adguard_cli/adguard-cli.sig 
```  

If you use a custom installation path, replace `/opt/adguard_cli/adguard-cli.sig` with the path to the signature file. It should be in the same directory as the binary file.

You’ll see something like this:

```
gpg: assuming signed data in 'adguard-cli'
gpg: Signature made Fri Nov 15 13:20:43 2024 +02
gpg:                using RSA key 28645AC9776EC4C00BCE2AFC0FE641E7235E2EC6
gpg:                issuer "devteam@adguard.com"
gpg: Good signature from "AdGuard <devteam@adguard.com>" [ultimate]
```

Check the following:
- RSA key: must be `28645AC9776EC4C00BCE2AFC0FE641E7235E2EC6`;
- Issuer name: must be `AdGuard`;
- Email address: must be `devteam@adguard.com`.

There may also be the following warning:

```
gpg: WARNING: The key's User ID is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 2864 5AC9 776E C4C0 0BCE  2AFC 0FE6 41E7 235E 2EC6
```

### Usage

Run `adguard-cli [command]` to use AdGuard CLI. Below are the available commands and their options:

### Options

- `-h, --help`                   Print this help message and exit
- `--help-all`                   Show all available commands, subcommands, and options
- `-v, --version`                Display program version information and exit

### Subcommands

- `activate`                     Activate the app
- `reset-license`                Deactivate the app
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
    - `list`                     List installed filters
        - `--all`                Show all filters
    - `install`                  Install a filter
    - `enable`                   Enable a filter
    - `disable`                  Disable a filter
    - `update`                   Update filters
