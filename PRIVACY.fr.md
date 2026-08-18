[English](PRIVACY.md) · [Português](PRIVACY.pt-BR.md) · [Español](PRIVACY.es.md) · **Français**

# Politique de confidentialité — MacBat

**Dernière mise à jour : 14 août 2026 · S'applique à MacBat 1.0.0 et versions suivantes**

MacBat ne collecte, ne stocke et ne transmet aucune donnée d'usage. Il n'y a ni
statistiques, ni télémétrie, ni rapport de plantage, ni publicité. MacBat n'a
pas de système de comptes : vous ne créez jamais de profil et ne vous connectez
jamais.

Ce document décrit exactement ce que MacBat lit, où il le garde, et les deux
seuls moments où il utilise le réseau.

---

## Ce qui reste sur votre Mac

MacBat lit des données de batterie et d'énergie, et les écrit sur votre propre
machine. Rien de tout cela ne quitte votre Mac.

| Donnée | Où elle est conservée |
|---|---|
| Historique de batterie de votre Mac — charge, santé, cycles, température, consommation | `~/Library/Application Support/MacBat/` |
| Historique de batterie d'un iPhone ou iPad connecté | `~/Library/Application Support/MacBat/` |
| Nom et consommation des processus gérés par Sentinelle | En mémoire, et dans un journal local dans le même dossier |
| Vos réglages et les dates de la période d'essai | Préférences macOS (`UserDefaults`) de MacBat |
| Votre reçu de licence — adresse e-mail, identifiant de produit, date d'activation | `~/Library/Application Support/MacBat/license-receipt.json` |

Vous pouvez tout supprimer quand vous voulez. Retirez le dossier `MacBat` de
`~/Library/Application Support/` et l'app revient à son état initial.

L'export CSV est écrit à l'emplacement que vous choisissez. MacBat ne l'envoie
jamais nulle part.

### iPhone et iPad connectés

MacBat lit l'état de la batterie d'un appareil iOS que vous branchez par câble.
Il communique avec l'appareil via `usbmuxd`, le service local de macOS que le
Finder utilise aussi, à travers un socket Unix sur votre Mac. **La connexion ne
quitte jamais votre machine.** MacBat ne lit ni vos messages, ni vos photos, ni
vos contacts, ni vos sauvegardes, ni aucun autre contenu de l'appareil —
uniquement l'état de la batterie.

---

## Quand MacBat utilise le réseau

MacBat établit des connexions réseau dans deux situations seulement. **Les deux
ont lieu parce que vous l'avez demandé.** MacBat n'établit aucune connexion au
lancement, ni en arrière-plan.

### 1. Quand vous recherchez une mise à jour

La recherche automatique est désactivée. MacBat n'accède au réseau que lorsque
vous choisissez **Rechercher les mises à jour…** dans le menu. Il demande alors
un fichier de version à GitHub :

```
https://raw.githubusercontent.com/1architect/macbat-releases/refs/heads/main/appcast.xml
```

Comme pour toute requête web, GitHub peut voir votre adresse IP et la version de
MacBat qui interroge. MacBat n'envoie aucun profil système, aucune information
matérielle et aucun identifiant. Le traitement de cette requête par GitHub
relève de la
[Déclaration de confidentialité de GitHub](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement).

### 2. Quand vous activez votre licence

Quand vous saisissez votre clé de licence, MacBat envoie une requête à Gumroad,
la boutique qui traite les achats de MacBat :

```
POST https://api.gumroad.com/v2/licenses/verify
```

Cette requête contient trois champs, et rien d'autre :

- l'identifiant du produit MacBat
- la clé de licence que vous avez saisie
- un indicateur qui compte l'activation

**L'adresse e-mail que vous saisissez n'est pas envoyée.** MacBat la compare sur
votre Mac avec l'adresse que Gumroad renvoie pour cette clé. Votre adresse reste
sur votre machine.

L'achat lui-même — nom, e-mail, informations de paiement — est traité par
Gumroad, pas par MacBat. Consultez la
[Politique de confidentialité de Gumroad](https://gumroad.com/privacy) pour
savoir ce qu'ils conservent et pendant combien de temps.

---

## Ce que MacBat ne fait jamais

- Il n'envoie jamais votre historique de batterie, votre liste de processus ou les données de votre appareil où que ce soit.
- Il ne lit jamais de fichiers hors de son propre dossier, sauf ceux que vous lui indiquez.
- Il n'exécute jamais de service en arrière-plan ni de daemon auxiliaire privilégié.
- Il ne demande pas d'accès root pour fonctionner.

### À propos de l'autorisation administrateur

Deux fonctions demandent une autorisation administrateur la première fois que
vous les activez : **Économie d'énergie** et **Contrôlé**. C'est macOS qui
affiche la demande — Touch ID ou votre mot de passe, selon ce que votre Mac
utilise — et **MacBat ne voit jamais le mot de passe**. L'autorisation installe
une règle `sudoers` limitée aux commandes exactes dont la fonction a besoin, une
liste courte et fixe d'arguments `pmset` et `tmutil`, et n'est plus redemandée.
La règle n'accorde rien au-delà de ces commandes. Vous
pouvez retirer les règles en supprimant `/etc/sudoers.d/macbat-economia` et
`/etc/sudoers.d/macbat-lowpowermode`.

---

## Enfants

MacBat est un utilitaire pour macOS et ne s'adresse pas aux enfants. Il ne
collecte aucune information personnelle, de qui que ce soit, à tout âge.

## Modifications de cette politique

Si le comportement de MacBat change, ce document change avec lui, et la date en
haut également. L'historique de ce fichier est public dans ce dépôt : vous
pouvez voir exactement ce qui a changé et quand.

## Contact

Questions sur la confidentialité, ou sur tout point de ce document :

**macbat@giomantovani.com.br**
