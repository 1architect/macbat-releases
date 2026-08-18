**English** · [Português](SECURITY.pt-BR.md) · [Español](SECURITY.es.md) · [Français](SECURITY.fr.md)

# Security Policy

MacBat is a menu-bar utility for macOS. It runs with your normal user account,
installs no background daemon, and collects no data about you. This document
explains exactly what it touches on your Mac and how to report a problem.

## Reporting a vulnerability

Email **macbat@giomantovani.com.br** with the details and steps to reproduce.
Please do not open a public issue for a security report. You get an
acknowledgement within a few days.

## Supported versions

Security fixes go into the latest release only. Always update to the newest
version from [Releases](https://github.com/1architect/macbat-releases/releases/latest)
or with `brew upgrade --cask macbat`.

## What MacBat does on your Mac

### Network

MacBat makes network connections in exactly two cases, and only when you start
them. It makes no connection at launch and none in the background.

1. **Check for Updates.** When you choose *Check for Updates…* from the menu,
   MacBat reads a version feed hosted with the releases on GitHub. If you accept
   an update, it downloads the new version from GitHub Releases. Nothing is sent
   about you.
2. **Activate a licence.** When you enter your e-mail and licence key, MacBat
   sends them to Gumroad (`POST https://api.gumroad.com/v2/licenses/verify`) to
   verify the key. This is the only time your e-mail leaves the Mac, and only
   because you asked to activate.

There is no analytics, no telemetry, and no crash reporting.

### Where your data is stored

Everything stays on your Mac, under your user account:

- `~/Library/Application Support/MacBat/` — battery and device history
  (`battery-history.json`) and trial state (`trial.json`).
- Preferences in the `com.giovanimanto.macbat` user defaults domain
  (`~/Library/Preferences/com.giovanimanto.macbat.plist`).

None of this is uploaded anywhere.

### How Sentinel works

Sentinel is the engine behind Controlled mode. For the background processes you
let it manage, it reduces their CPU usage without terminating them, and the
process goes back to running normally as soon as it is released. It can also
keep a process on the efficiency cores, and always undoes that when the process
is released. Sentinel never changes the CPU or GPU behaviour of the app you have
in the foreground, and it never touches system-critical processes.

### Administrator permissions

Two features ask for administrator authorisation the first time you enable them
(Touch ID or your password). The authorisation installs a `sudoers` rule scoped
to the exact commands the feature needs, so you are not asked again:

| Feature | Commands allowed |
|---|---|
| Low Power | `pmset -a lowpowermode 0` / `1` |
| Controlled | a fixed list of `pmset` display-sleep, Power Nap and wake-on-LAN arguments, plus `tmutil enable` / `disable` |

macOS handles the prompt, so MacBat never sees your password, and it installs no
background daemon. The rules live at `/etc/sudoers.d/macbat-lowpowermode` and
`/etc/sudoers.d/macbat-economia`, and you can remove them at any time (see
Uninstall below).

### Code signing

MacBat is signed ad-hoc, not with a paid Apple Developer ID. Verify a download
before you trust it:

```bash
codesign -dv --verbose=4 /Applications/MacBat.app
```

## Uninstall completely

1. Quit MacBat. Turn **Controlled** and **Low Power** off first so their system
   settings revert.
2. Remove the app:
   ```bash
   brew uninstall --cask macbat
   ```
   or drag **MacBat.app** from Applications to the Trash.
3. Remove its data and preferences:
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Remove the administrator rules (only if you ever enabled Low Power or
   Controlled):
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode
   ```
5. If MacBat hid the native battery icon, re-enable it in **System Settings →
   Control Center → Battery**.

After this, no MacBat file remains on your Mac.
