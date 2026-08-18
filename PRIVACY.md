**English** · [Português](PRIVACY.pt-BR.md) · [Español](PRIVACY.es.md) · [Français](PRIVACY.fr.md)

# Privacy Policy — MacBat

**Last updated: 14 August 2026 · Applies to MacBat 1.0.0 and later**

MacBat does not collect, store, or transmit any usage data. There is no
analytics, no telemetry, no crash reporting, and no advertising. MacBat has no
account system, so you never create a profile or sign in.

This document describes exactly what MacBat reads, where it keeps it, and the
only two moments it uses the network.

---

## What stays on your Mac

MacBat reads battery and power data and writes it to your own machine. None of
it leaves your Mac.

| Data | Where it is stored |
|---|---|
| Battery history for your Mac — charge level, health, cycles, temperature, power draw | `~/Library/Application Support/MacBat/` |
| Battery history for a connected iPhone or iPad | `~/Library/Application Support/MacBat/` |
| Names and resource usage of running processes that Sentinel manages | In memory, and in a local journal under the same folder |
| Your settings and trial dates | macOS preferences (`UserDefaults`) for MacBat |
| Your licence receipt — e-mail address, product ID, activation date | `~/Library/Application Support/MacBat/license-receipt.json` |

You can delete all of it at any time. Remove the `MacBat` folder in
`~/Library/Application Support/` and the app returns to its initial state.

The CSV export writes to the location you choose. MacBat never uploads it.

### Connected iPhone and iPad

MacBat reads the battery status of an iOS device you connect by cable. It talks
to the device through `usbmuxd`, the local macOS service that Finder also uses,
over a Unix socket on your Mac. **The connection never leaves your machine.**
MacBat does not read your messages, photos, contacts, backups, or any other
content on the device — only battery status.

---

## When MacBat uses the network

MacBat makes network connections in two situations only. **Both happen because
you asked for them.** MacBat makes no connection at launch, and none in the
background.

### 1. When you check for updates

Automatic update checks are turned off. MacBat contacts the network only when
you choose **Check for Updates…** from the menu. It then requests a version
file from GitHub:

```
https://raw.githubusercontent.com/1architect/macbat-releases/refs/heads/main/appcast.xml
```

As with any web request, GitHub can see your IP address and the version of
MacBat that is asking. MacBat sends no system profile, no hardware
information, and no identifier of any kind. GitHub's handling of that request
is covered by the [GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement).

### 2. When you activate your licence

When you enter your licence key, MacBat sends one request to Gumroad, the store
that processes MacBat purchases:

```
POST https://api.gumroad.com/v2/licenses/verify
```

That request contains three fields, and nothing else:

- the MacBat product ID
- the licence key you typed
- a flag that counts the activation

**The e-mail address you type is not sent.** MacBat compares it on your Mac
with the address Gumroad returns for the key. Your address stays on your
machine.

Your purchase itself — name, e-mail, payment details — is handled by Gumroad,
not by MacBat. Refer to the [Gumroad Privacy Policy](https://gumroad.com/privacy)
for what they hold and how long they keep it.

---

## What MacBat never does

- It never sends your battery history, process list, or device data anywhere.
- It never reads files outside its own folder, apart from what you point it at.
- It never runs a background service or a privileged helper daemon.
- It does not require root access to run.

### About administrator authorization

Two features ask for administrator authorization the first time you turn them
on: **Low Power** and **Controlled**. macOS shows its own dialog — Touch ID or
your password, whichever your Mac uses — and **MacBat never sees the password
itself**. The authorization installs a `sudoers` rule limited to the exact
commands the feature needs, a short fixed list of `pmset` and `tmutil`
arguments, so you are not asked again. The rule grants nothing beyond those
commands. You can remove the rules by deleting
`/etc/sudoers.d/macbat-economia` and `/etc/sudoers.d/macbat-lowpowermode`.

---

## Children

MacBat is a utility for macOS and is not directed at children. It collects no
personal information from anyone, of any age.

## Changes to this policy

If MacBat's behaviour changes, this document changes with it, and the date at
the top changes too. The history of this file is public in this repository, so
you can see exactly what changed and when.

## Contact

Questions about privacy, or about anything in this document:

**macbat@giomantovani.com.br**
