**English** · [Português](README.pt-BR.md) · [Español](README.es.md) · [Français](README.fr.md)

# MacBat

**Battery time remaining is back in your menu bar — and your Mac runs cooler.**

MacBat estimates how long your battery really lasts, shows the power data macOS
hides, and quiets the background processes that drain it. It uses less than 1%
CPU, needs no root access, and **collects no data about you**.

[**Download MacBat**](#install) ·
[Buy a licence](https://giovaniman8.gumroad.com/l/macbat) ·
[Privacy Policy](PRIVACY.md)

---

## What it does

**Battery time remaining, back where it belongs.** Apple removed the estimate
from the menu bar. MacBat brings it back with its own algorithm, and keeps it
steady instead of flickering between wild numbers.

**Controlled mode.** Your Mac already manages its own battery well. What it does
not always manage is a background process burning energy for no reason. MacBat
finds those processes and reduces their CPU usage — without touching CPU or GPU
performance for the app you are actually using.

**Sentinel.** The engine behind Controlled mode, available on its own if you
prefer the stock battery icon. Choose which processes it manages, or pin a
process to the efficiency cores.

**Advanced power data, for your Mac and your iPhone.** Charge, health, cycles,
temperature and power draw, recorded over time so you can see what changed.
Connect an iPhone or iPad by cable and MacBat tracks its battery too. Export
everything to CSV.

**Insights, day and night.** MacBat surfaces what matters about consumption,
battery health and managed processes right in the main panel, and stays out of
the way otherwise.

**A real interface, not another menu.** Liquid Glass pills that put the controls
you use at your pointer. Right-click for the advanced menu.

**Your icon, your choice.** The new macOS 27 icon or the classic one.

**Four languages.** English, Portuguese, Spanish and French. MacBat follows
your system language.

---

## Install

### Homebrew (official)

```bash
brew install --cask 1architect/macbat/macbat
```

Homebrew is the official way to install MacBat.

### Direct download (alternative)

Use this only if you cannot use Homebrew. Download the latest
`MacBat-x.y.z.zip` from
[Releases](https://github.com/1architect/macbat-releases/releases/latest),
unzip it, and drag **MacBat.app** to your Applications folder.

MacBat is signed ad-hoc, not with a paid Developer ID, so macOS blocks the
first launch. To allow it:

1. Double-click **MacBat.app**. macOS refuses and says it cannot verify the developer.
2. Open **System Settings → Privacy & Security**, scroll to **Security**, and click **Open Anyway** next to the MacBat message.
3. Confirm with Touch ID or your password.

macOS remembers the choice — this is a one-time step.

> Older guides say to right-click and choose **Open**. That shortcut was removed
> in macOS 15 and does not work on the versions MacBat supports.

### Requirements

- macOS 26 or later
- Apple Silicon or Intel

### Updating

MacBat never checks for updates on its own. Choose **Check for Updates…** from
the menu when you want to look, or run `brew upgrade --cask macbat`.

---

## Try it, then buy it

MacBat runs fully for **7 days**. After that a licence unlocks it again. There
is no account to create and no subscription — you buy it once.

[**Buy a licence**](https://giovaniman8.gumroad.com/l/macbat)

To activate: open the menu, choose the licence item, and enter the e-mail and
key from your purchase e-mail.

---

## Privacy

MacBat has no analytics, no telemetry, and no crash reporting. Your battery
history, your process list and your device data stay on your Mac.

MacBat touches the network exactly twice, and only when you ask: when you check
for updates, and when you activate a licence. It makes no connection at launch
and none in the background.

The full detail — every file it writes, every field it sends — is in the
[Privacy Policy](PRIVACY.md).

---

## Permissions

Two features ask for administrator authorization the first time you turn them
on — Touch ID or your password, whichever your Mac uses. The authorization
installs a `sudoers` rule limited to the exact commands they need, so you are
never asked again:

| Feature | Commands allowed |
|---|---|
| Low Power | `pmset -a lowpowermode 0` / `1` |
| Controlled | a fixed list of `pmset` display-sleep, Power Nap and wake-on-LAN arguments, plus `tmutil enable` / `disable` |

macOS handles the authorization, so MacBat never sees your password. It
installs no background daemon. Remove the rules any time by deleting `/etc/sudoers.d/macbat-economia` and
`/etc/sudoers.d/macbat-lowpowermode`.

---

## Support

**macbat@giomantovani.com.br**

---

## Licence

MacBat is proprietary software. Copyright © 2026 Gio Mantovani / 1architect.
All rights reserved. The source code is not public.

This repository holds the public releases, the update feed, and the documents
above.
