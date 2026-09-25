**English** · [Português](README.pt-BR.md) · [Español](README.es.md) · [Français](README.fr.md)

# MacBat

**Battery time remaining is back in your menu bar — and your Mac runs cooler.**

MacBat estimates how long your battery really lasts, shows the power data macOS
hides, and quiets the background processes that drain it. It uses less than 1%
CPU, needs no root access, and **collects no data about you**.

[**Download MacBat**](#install) ·
[Buy a licence](https://giovaniman8.gumroad.com/l/macbat) ·
[Privacy Policy](PRIVACY.md) ·
[Security](SECURITY.md)

---

## What it does

**Battery time remaining, back where it belongs.** Apple removed the estimate
from the menu bar. MacBat brings it back with its own algorithm, and keeps it
steady instead of flickering between wild numbers.

**Controlled mode.** Your Mac already manages its own battery well. What it does
not always manage is a background process burning energy for no reason. MacBat
finds those processes and reduces their CPU usage — without touching CPU or GPU
performance for the app you are actually using. It measures the result on
battery and shows you how much less power your Mac used.

**Sentinel.** The engine behind Controlled mode, available on its own if you
prefer the stock battery icon. Choose which processes it manages, or pin a
process to the efficiency cores. With your authorization, it can also move
macOS background services to the efficiency cores and pause processes owned by
other users.

**Advanced power data, for your Mac and your iPhone.** Charge, health, cycles,
temperature and power draw, recorded over time so you can see what changed.
Connect an iPhone or iPad by cable and MacBat tracks its battery too. Export
everything to CSV.

**Insights, day and night.** MacBat surfaces what matters about consumption,
battery health and managed processes right in the main panel, taking turns with
a live list of the apps using the most energy right now. Otherwise it stays out
of the way.

**A real interface, not another menu.** Liquid Glass pills that put the controls
you use at your pointer. Right-click for the advanced menu.

**Your icon, your choice.** More than 20 battery icon styles, from the new
macOS 27 look to classic designs, filled with the color of your power mode.
Show the percentage inside the icon or next to it.

**A guided start.** The first launch walks you through Sentinel and Controlled
mode, lets you pick your icon, and starts your free trial.

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
for updates (a version feed on GitHub), and when you activate a licence (Gumroad,
to verify the key). It makes no connection at launch and none in the background.

Your data stays on your Mac, under `~/Library/Application Support/MacBat/`. The
full detail — every file it writes, every field it sends, and how Sentinel acts
on processes — is in the [Privacy Policy](PRIVACY.md) and the
[Security Policy](SECURITY.md).

---

## Permissions

Up to three features ask for administrator authorization the first time you turn
them on — Touch ID or your password, whichever your Mac uses. The authorization
installs a `sudoers` rule limited to the exact commands they need, so you are
never asked again:

| Feature | Commands allowed |
|---|---|
| Low Power | `pmset -a lowpowermode 0` / `1` |
| Controlled | a fixed list of `pmset` display-sleep, Power Nap and wake-on-LAN arguments, plus `tmutil enable` / `disable` |
| Sentinel, system processes (optional) | `kill -STOP` / `-CONT` (pause and resume — never quit) and `taskpolicy -b` / `-B -p` (efficiency cores on and off) |

macOS handles the authorization, so MacBat never sees your password. It
installs no background daemon. Remove the rules any time by deleting
`/etc/sudoers.d/macbat-economia`, `/etc/sudoers.d/macbat-lowpowermode` and
`/etc/sudoers.d/macbat-sentinela-sistema`. Sentinel's rule can also be revoked
from the padlock in the Sentinel window.

---

## Uninstall

The quickest way: open the menu, choose **About MacBat**, then **Uninstall…**.
MacBat moves itself to the Trash and removes its administrator rules. Your data
and licence are kept, in case you come back.

To remove everything by hand:

1. Quit MacBat. Turn **Controlled** and **Low Power** off first so their system settings revert.
2. Remove the app: `brew uninstall --cask macbat`, or drag **MacBat.app** to the Trash.
3. Remove its data and preferences:
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Remove the administrator rules, only if you enabled Low Power, Controlled or Sentinel's system process control:
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode /etc/sudoers.d/macbat-sentinela-sistema
   ```
5. If the native battery icon is hidden, re-enable it in **System Settings → Control Center → Battery**.

After this, no MacBat file remains on your Mac.

---

## Support

**macbat@giomantovani.com.br**

---

## Licence

MacBat is proprietary software. Copyright © 2026 Gio Mantovani / 1architect.
All rights reserved. The source code is not public.

This repository holds the public releases, the update feed, and the documents
above. See [LICENSE](LICENSE) for the full terms.
