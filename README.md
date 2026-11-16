# XLibre Stable for Devuan

An unofficial APT repository providing packages from the **stable release series of XLibre** for Devuan GNU/Linux.

> ⚠️ **Unofficial and experimental**
>
> This is an independent, community-maintained project. It is not officially affiliated with, endorsed by, or supported by the XLibre developers or the Devuan project.
>
> This repository is relatively new and has not been extensively tested. Packages are provided as-is, without any guarantee of stability, compatibility, or functionality. **Use at your own risk.**

## Project Goal

The goal of this repository is to make it easier for Devuan users to install and stay updated with the stable release series of XLibre through APT.

This project aims to:

- Track the upstream XLibre **25.1.x stable series**, rather than development or pre-release versions.
- Provide packages built for Devuan.
- Publish updates as new stable releases become available.
- Make installation and upgrades possible through standard APT commands.

Updates will be provided on a best-effort basis. There is no guaranteed release schedule, and new upstream releases may require additional testing or packaging changes before publication.

## Currently Supported

| | |
|---|---|
| Distribution | Devuan 6 (Excalibur) |
| Architecture | amd64 |
| XLibre version | 25.1.11 |
| Status | Experimental |

Support for additional Devuan releases and architectures may be considered in the future.

## Installation

**Warning:** Installing XLibre replaces components of the existing Xorg installation. Make sure you have a backup or recovery method before proceeding.

### 1. Add the signing key

```bash
curl -fsSL https://nivas-g.github.io/devuan-xlibre-stable/xlibre-stable-keyring.gpg -o /tmp/xlibre-stable-keyring.gpg
```

Verify that the key fingerprint matches:

```text
9056 B6E3 F833 29F0 3176 7F17 B375 8F4C DE41 3F12
```

Then install the key:

```bash
sudo install -m 644 /tmp/xlibre-stable-keyring.gpg /usr/share/keyrings/xlibre-stable-archive-keyring.gpg
```

### 2. Add the APT repository

```bash
echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/xlibre-stable-archive-keyring.gpg] https://nivas-g.github.io/devuan-xlibre-stable/ excalibur main' | sudo tee /etc/apt/sources.list.d/xlibre-stable.list
```

### 3. Install XLibre

```bash
sudo apt update
sudo apt install \
  xlibre-x11-common \
  xserver-xlibre-common \
  xserver-xlibre-core \
  xserver-xlibre-input-libinput
```

Review the proposed package removals before confirming installation.

## Updates

When updated packages have been published to this repository, they can be installed using:

```bash
sudo apt update
sudo apt upgrade
```

The repository aims to track future stable releases, but updates may be delayed by build failures, dependency changes, or compatibility testing.

## Known Limitations

- Only Devuan Excalibur amd64 is currently targeted.
- Hardware and graphics-driver compatibility has not been comprehensively tested.
- NVIDIA and other proprietary drivers may require additional compatibility checks.
- Not every XLibre driver or optional component is currently packaged.
- Packages may contain bugs or experience dependency conflicts.

## Reporting Issues

If you encounter a problem, please open an issue in this repository with your Devuan version, hardware details, XLibre package version, and relevant error logs.

For bugs originating in XLibre itself, consider reporting them to the upstream project as well.

## Credits

XLibre is developed by the [X11Libre project](https://github.com/X11Libre/xserver).

This repository uses and adapts Debian packaging work from the [xlibre-debian project](https://github.com/xlibre-debian).

Thanks to the upstream developers and package maintainers for their work.

---

**Disclaimer:** This is an independent, unofficial, experimental packaging project. No warranty or guarantee of support is provided.
