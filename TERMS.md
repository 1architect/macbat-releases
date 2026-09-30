**English** · [Português](TERMS.pt-BR.md) · [Español](TERMS.es.md) · [Français](TERMS.fr.md)

# Terms of Service — MacBat

**Last updated: 30 September 2026 · Applies to MacBat 1.0.0 and later**

These terms govern your use of MacBat, the macOS menu-bar app published by
Gio Mantovani / 1architect ("we", "us"), its website and its public releases
repository. By installing or using MacBat you agree to them. If you do not
agree, do not install or use MacBat.

---

## 1. The licence

MacBat is proprietary software. Your right to use it is set out in the
[MacBat Proprietary Licence](LICENSE): a personal, limited, revocable,
non-exclusive and non-transferable right to install and use MacBat. These
terms add to that licence; if they conflict, the licence prevails on
intellectual property and these terms prevail on everything else.

## 2. Free features, trial and paid licence

- **Trial.** Every new installation includes a free 7-day trial with all
  features unlocked.
- **After the trial,** the menu-bar icon, the percentage and the time remaining
  stay free. Sentinel, Controlled mode, Battery Data and the extra icons
  require a licence.
- **Licence.** A licence is a one-time purchase, not a subscription. It is
  activated with the licence key you receive from Gumroad and is valid for up
  to **3 activations**. Do not share, resell or publish your key.
- **Purchases and refunds.** Purchases are processed by Gumroad, the seller of
  record for payment. Payment, taxes and refunds follow Gumroad's terms and
  the consumer rights that apply where you live. Questions about a purchase:
  macbat@giomantovani.com.br.
- We may change prices and which features are free or paid in future versions.
  A change never removes a feature from a licence you already bought for the
  version you bought it with.

## 3. What MacBat does on your Mac

MacBat is a utility that reads power data and, when you turn the feature on,
changes how your Mac behaves. You should know exactly what that means:

- **Sentinel** pauses and resumes processes, or moves them to the efficiency
  cores, to reduce their CPU usage. A process that is paused too aggressively
  can become slow, unresponsive or lose unsaved work. You choose which
  processes it manages, and you can turn it off at any time.
- **Controlled mode and Low Power mode** change system power settings
  (`pmset`), and Controlled mode restores them when you turn it off.
- **System process control** (optional) lets Sentinel act on processes that
  belong to other users and on macOS background services. Use it only if you
  understand the processes you are affecting.
- **Administrator authorization.** These features ask once for Touch ID or
  your password through macOS itself. MacBat never sees the password. It
  installs `sudoers` rules limited to the exact commands each feature needs,
  which you can remove at any time, as described in the
  [Privacy Policy](PRIVACY.md).
- **Battery and device data** come from macOS interfaces, some of which are not
  documented by Apple and can change with any macOS update. Time-remaining
  figures, health and other readings are **estimates** and can be wrong. Do
  not rely on MacBat for anything safety-critical.
- Reading a connected iPhone or iPad uses the local `usbmuxd` service and only
  reads battery status.

## 4. Acceptable use

You agree not to: copy, modify, redistribute, rent or resell MacBat; attempt to
reverse engineer it except where the law allows; bypass, tamper with or share
the trial or licence mechanism; or use MacBat to interfere with computers or
data that are not yours or that you are not authorised to manage.

## 5. Updates

MacBat does not check for updates on its own. You decide when to use
**Check for Updates…** or `brew upgrade --cask macbat`. We do not promise a
release schedule, and security fixes go into the latest release only (see
[Security](SECURITY.md)). You are responsible for keeping MacBat compatible
with your macOS version; MacBat requires macOS 26 or later.

## 6. Privacy

MacBat collects no data about you. How it works, what stays on your Mac and
the only two moments it uses the network are described in the
[Privacy Policy](PRIVACY.md), which is part of these terms.

## 7. No warranty

MacBat is provided **"as is" and "as available"**, without warranty of any
kind, express or implied, including fitness for a particular purpose,
accuracy of estimates, or uninterrupted and error-free operation. We do not
guarantee that MacBat will save a particular amount of battery.

## 8. Limitation of liability

To the fullest extent permitted by law, we are not liable for indirect,
incidental or consequential damages, loss of data, loss of profits, or damage
to your Mac or other devices arising from the use of or inability to use
MacBat. Our total liability for any claim is limited to the amount you paid
for your MacBat licence. Nothing in these terms limits liability that cannot
be limited by law, or any mandatory consumer rights you have.

## 9. Termination

You may stop using MacBat at any time by deleting it and, if you wish,
removing its data and `sudoers` rules. We may revoke a licence that is used in
breach of these terms, for example one that is shared or resold, or obtained
through a chargeback or fraudulent payment. On termination you must stop using
MacBat and delete your copies.

## 10. Changes to these terms

If we change these terms, this document changes with it and the date at the
top changes too. The history of this file is public in this repository.
Continuing to use MacBat after a change means you accept the new terms.

## 11. Governing law

These terms are governed by the laws of Brazil, without regard to conflict-of-
law rules. Mandatory consumer-protection rules of the country where you live
still apply to you. The courts of the place where you can legally sue under
those rules, and otherwise the courts of Brazil, may hear any dispute.

## 12. Contact

Questions about these terms, or requests for authorisation:

**macbat@giomantovani.com.br**

The English text is the reference version in case of any discrepancy between
translations.
