# Windows 10 Lite Codespaces — LTSC profile

A lighter Windows 10 Codespaces configuration based on [dockur/windows](https://github.com/dockur/windows).

## What is lighter here?

This profile uses **Windows 10 LTSC** (`VERSION: "10l"`) instead of regular Windows 10 and disables features that add load:

- 3 GB guest RAM
- 2 virtual CPU cores
- 24 GB qcow2 disk
- 1024×600 display
- Lossy web-VNC compression enabled
- Audio disabled
- Samba/shared-folder integration disabled
- Hardware KVM disabled for Codespaces compatibility

The container still downloads and installs the Windows image automatically from the upstream dockur/windows workflow. No Windows image is stored in this repository.

## Start

1. Open [Create this Codespace](https://codespaces.new/Nikhilsin527/windows10-lite-codespaces).
2. Choose a **4-core machine** if GitHub offers the choice.
3. Create the Codespace and wait for the first installation to finish.
4. Open forwarded port **8006** from the Ports tab.

First installation may take a long time. Keep the Codespace running during the download and installation.

## Login

```text
Username: WindowsUser
Password: ChangeThisPassword
```

Change the password immediately after first login. You can edit `PASSWORD` in `.devcontainer/docker-compose.yml` before creating the Codespace.

## Important performance truth

GitHub Codespaces normally does not expose `/dev/kvm`. Therefore this repository uses QEMU software emulation (`KVM: "N"`). It is lighter than the previous profile, but **smooth Windows performance cannot be guaranteed** on Codespaces. If it still hangs, the limitation is the missing hardware virtualization, not only RAM settings.

For genuinely smooth Windows 10, use a Linux VM/VPS with nested virtualization and `/dev/kvm`, then use the normal dockur/windows configuration with KVM enabled.

Windows activation/licensing is not included. Use a valid license where required.

## Quota warning

The VM consumes Codespaces storage and compute quota. Stop or delete the Codespace after use.
