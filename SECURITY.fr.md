[English](SECURITY.md) · [Português](SECURITY.pt-BR.md) · [Español](SECURITY.es.md) · **Français**

# Politique de sécurité

MacBat est un utilitaire de barre de menus pour macOS. Il s'exécute avec votre
compte utilisateur normal, n'installe aucun daemon en arrière-plan et ne collecte
aucune donnée sur vous. Ce document explique exactement ce qu'il touche sur votre
Mac et comment signaler un problème.

## Signaler une vulnérabilité

Écrivez à **macbat@giomantovani.com.br** avec les détails et les étapes pour
reproduire. N'ouvrez pas de ticket public pour un signalement de sécurité. Vous
recevez un accusé de réception sous quelques jours.

## Versions prises en charge

Les correctifs de sécurité ne vont que dans la dernière version. Mettez toujours
à jour vers la version la plus récente depuis
[Releases](https://github.com/1architect/macbat-releases/releases/latest)
ou avec `brew upgrade --cask macbat`.

## Ce que MacBat fait sur votre Mac

### Réseau

MacBat établit des connexions réseau dans exactement deux cas, et seulement quand
vous les lancez. Il n'établit aucune connexion au lancement, ni en arrière-plan.

1. **Rechercher les mises à jour.** Quand vous choisissez *Rechercher les mises à
   jour…* dans le menu, MacBat lit un flux de version hébergé avec les versions
   sur GitHub. Si vous acceptez une mise à jour, il télécharge la nouvelle version
   depuis GitHub Releases. Rien vous concernant n'est envoyé.
2. **Activer une licence.** Quand vous saisissez votre e-mail et votre clé de
   licence, MacBat les envoie à Gumroad
   (`POST https://api.gumroad.com/v2/licenses/verify`) pour vérifier la clé.
   C'est la seule fois où votre e-mail quitte le Mac, et seulement parce que vous
   avez demandé l'activation.

Il n'y a ni statistiques d'usage, ni télémétrie, ni rapport de plantage.

### Où vos données sont stockées

Tout reste sur votre Mac, dans votre compte utilisateur :

- `~/Library/Application Support/MacBat/` — historique de batterie et
  d'appareils (`battery-history.json`) et l'état de l'essai (`trial.json`).
- Préférences dans le domaine `com.giovanimanto.macbat`
  (`~/Library/Preferences/com.giovanimanto.macbat.plist`).

Rien de tout cela n'est téléversé où que ce soit.

### Comment Sentinelle agit

Sentinelle est le moteur derrière le mode Contrôlé. Pour les processus en
arrière-plan que vous la laissez gérer, elle réduit leur usage du processeur
sans les terminer, et le processus retrouve son fonctionnement normal dès qu'il
est libéré. Elle peut aussi maintenir un processus sur les cœurs d'efficacité,
et elle annule toujours cela quand le processus est libéré. Sentinelle ne change
jamais le comportement CPU ou GPU de l'app que vous avez au premier plan, et
elle ne touche jamais aux processus critiques du système.

### Autorisations administrateur

Deux fonctions demandent une autorisation administrateur la première fois que
vous les activez (Touch ID ou votre mot de passe). L'autorisation installe une
règle `sudoers` limitée aux commandes exactes dont la fonction a besoin, et n'est
plus redemandée :

| Fonction | Commandes autorisées |
|---|---|
| Économie d'énergie | `pmset -a lowpowermode 0` / `1` |
| Contrôlé | une liste fixe d'arguments `pmset` pour la veille de l'écran, Power Nap et le réveil par le réseau, plus `tmutil enable` / `disable` |

C'est macOS qui gère l'autorisation : MacBat ne voit jamais votre mot de passe,
et il n'installe aucun daemon en arrière-plan. Les règles se trouvent dans
`/etc/sudoers.d/macbat-lowpowermode` et `/etc/sudoers.d/macbat-economia`, et vous
pouvez les retirer à tout moment (voir Désinstaller ci-dessous).

### Signature de code

MacBat est signé en mode ad-hoc, pas avec un Apple Developer ID payant. Vérifiez
un téléchargement avant de lui faire confiance :

```bash
codesign -dv --verbose=4 /Applications/MacBat.app
```

## Désinstaller complètement

1. Quittez MacBat. Désactivez **Contrôlé** et **Économie d'énergie** d'abord,
   pour que les réglages système reviennent.
2. Retirez l'app :
   ```bash
   brew uninstall --cask macbat
   ```
   ou faites glisser **MacBat.app** depuis Applications vers la Corbeille.
3. Retirez les données et les préférences :
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Retirez les règles administrateur (seulement si vous avez déjà activé Économie
   d'énergie ou Contrôlé) :
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode
   ```
5. Si MacBat a masqué l'icône de batterie native, réactivez-la dans **Réglages
   Système → Centre de contrôle → Batterie**.

Après cela, aucun fichier MacBat ne reste sur votre Mac.
