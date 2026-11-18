# SelectiveVpn (Linux)

Linux / Avalonia port of **[SelectiveVpn](https://github.com/fullspb/SelectiveVpn)** — selective VPN routing for chosen apps, folders, or address lists (or everything except a deny list).

Built with **.NET / Avalonia**, powered by **Mihomo** and **AmneziaWG** configs / subscription links.

Windows builds and the Windows updater live only in the original repo: **[fullspb/SelectiveVpn](https://github.com/fullspb/SelectiveVpn)**. This repository is Linux-only so `/releases/latest` there is never confused by `.deb` / `.pkg` assets.

[![Release](https://img.shields.io/github/v/release/fullspb/SelectiveVpn-Linux?label=release)](https://github.com/fullspb/SelectiveVpn-Linux/releases/latest)

<p align="center">
  <img src="docs/screenshots/orbit-main.jpg" alt="SelectiveVpn Linux Orbit UI — main window" width="900">
</p>

## Screenshots

### Main window

![Orbit main window (Avalonia)](docs/screenshots/orbit-main.jpg)

### Disconnected

![Orbit main window, disconnected](docs/screenshots/orbit-disconnected.jpg)

> Avalonia Orbit UI on Linux. Screenshots use local demo profiles and a redacted server field.

## Install

Open the [latest Linux release](https://github.com/fullspb/SelectiveVpn-Linux/releases/latest).

### Debian / Ubuntu

```bash
sudo apt install ./selectivevpn_0.1.25-1_amd64.deb
```

Self-contained `linux-x64` package. Details: packaging under `packaging/deb/`.

### Arch / CachyOS

```bash
sudo pacman -U selectivevpn-git-0.1.25.r43.g636b63e-1-x86_64.pkg.tar.zst
```

Or build from `packaging/aur/selectivevpn-git` (see AUR packaging notes in the Project docs).

Root / polkit may be needed for Mihomo TUN (`setcap` / capabilities).

## Features (Linux tip)

- **Avalonia Orbit UI** — connection control, profiles, routing, traffic, RU/EN copy
- **Profiles** — AmneziaWG configs, subscription URLs, or pasted `vless://` / `vmess://` / `trojan://` / `ss://` links
- **Selective routing** — processes, folders, nested address lists (incl. YouTube/Google presets)
- **Full / selective tunnel** — Mihomo TUN on Linux
- **Live rule reload** and traffic counters

## Build from source

```bash
dotnet build SelectiveVpn.Desktop/SelectiveVpn.Desktop.csproj -c Release
dotnet test SelectiveVpn.Tests/SelectiveVpn.Tests.csproj -c Release
```

Debian package:

```bash
./packaging/deb/build-deb.sh
```

AUR package (local):

```bash
./packaging/aur/selectivevpn-git/makepkg-local.sh
```

## Project layout

| Path | Role |
|------|------|
| `SelectiveVpn.Desktop/` | Avalonia Linux UI |
| `SelectiveVpn.Core/` | Mihomo engine, config / subscription parsing, traffic |
| `SelectiveVpn.Tests/` | Unit tests |
| `packaging/deb/` | Debian `.deb` |
| `packaging/aur/selectivevpn-git/` | Arch / CachyOS package |
| `SelectiveVpn/` | Upstream WPF UI (Windows; not the Linux runtime) |

## Related

| Repo | Role |
|------|------|
| [fullspb/SelectiveVpn-Linux](https://github.com/fullspb/SelectiveVpn-Linux) | This repo — Linux releases |
| [fullspb/SelectiveVpn](https://github.com/fullspb/SelectiveVpn) | Windows client + Windows releases |

## Disclaimer

SelectiveVpn is a personal / community client. You are responsible for complying with local law and your VPN provider’s terms. Do not commit or share private keys or subscription tokens in issues or PRs.
