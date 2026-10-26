# xRoute

xRoute helps you reach sites your internet provider blocks. One big power button turns it on and off. While it is on, it modifies how your PC's web traffic is sent (its own packet engine, built on the WinDivert driver) and switches your DNS to Cloudflare (1.1.1.1), because many blocks are done with poisoned DNS answers. It lives in the notification area (system tray).

On start it checks that your sites open and, if needed, tries other methods automatically.

Choose **Chosen sites** (Discord is built in; add others by typing their name) or **Everything**.

> xRoute does not encrypt your traffic, does not hide your IP address and does not guarantee that any site works. Results depend on your provider and network. Use it only where that is legal for you.

## Install

1. Open the [latest release](https://github.com/aykutdmnn/xRoute/releases/latest) and download `xRoute-<version>-x64.msi`.
2. Run it as administrator. It installs the app, a Windows service and the engine under `C:\Program Files\xRoute` and adds a Start Menu shortcut.
3. Start **xRoute** and press the power button. Press it again to stop; your DNS settings are restored. After you turn it on once, it starts with Windows and turns itself on again after every restart.

Requirements: Windows 11, or Windows 10 build 17763 or newer, 64-bit, and the .NET 10 Desktop Runtime (the installer tells you if it is missing).

`xRoute-<version>-portable.zip` (same release page) holds the same files without the installer, for manual setup (`docs\INSTALLATION.md` inside the zip). Portable copies do not update themselves; they only point you to the releases page.

Uninstall from *Settings, Apps*. It stops the engine and removes the service and files.

## Updates

Installed copies look for a new version when they start and every few hours. When one exists a banner with **Update now** appears in the window (and in the tray menu). One click and one Windows permission prompt later the new version is installed and xRoute opens again; if the engine was on, it turns on again. Every update is signed by the maintainer and checked twice before it runs; an update that fails its check is never installed. You can switch the check off in *Settings*.

## Good to know

- The installer is **not signed**, so Windows SmartScreen may warn.
- Some antivirus programs (Kaspersky was seen) lock the installer because it contains the WinDivert driver, and `msiexec` fails with error 1619. Allow the file in your antivirus and run it again. xRoute never adds antivirus exclusions.
- No telemetry, no accounts. The only thing xRoute fetches by itself is the newest-release information from github.com (see Updates). The only system change is the DNS switch described above, and the previous values come back when you stop.

## License

MIT, see `LICENSE`. WinDivert (LGPLv3) is bundled unmodified; see `THIRD_PARTY_NOTICES.md`.
