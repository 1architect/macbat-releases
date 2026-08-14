[English](README.md) · [Português](README.pt-BR.md) · [Español](README.es.md) · **Français**

# MacBat

**L'autonomie restante revient dans votre barre des menus — et votre Mac chauffe moins.**

MacBat estime la durée réelle de votre batterie, affiche les données d'énergie
que macOS cache et fait taire les processus en arrière-plan qui la vident. Il
utilise moins de 1% du processeur, ne demande aucun accès root et **ne collecte
aucune donnée sur vous**.

[**Télécharger MacBat**](#installation) ·
[Acheter une licence](https://giovaniman8.gumroad.com/l/macbat) ·
[Politique de confidentialité](PRIVACY.fr.md)

---

## Ce qu'il fait

**L'autonomie restante, de retour à sa place.** Apple a retiré l'estimation de
la barre des menus. MacBat la ramène avec son propre algorithme, et garde le
chiffre stable au lieu de sauter d'un extrême à l'autre.

**Mode Contrôlé.** Votre Mac gère déjà bien sa batterie. Ce qu'il ne gère pas
toujours, c'est un processus en arrière-plan qui brûle de l'énergie pour rien.
MacBat repère ces processus et réduit leur usage du processeur — sans toucher
aux performances CPU ou GPU de l'app que vous utilisez vraiment.

**Sentinelle.** Le moteur derrière le mode Contrôlé, disponible seul si vous
préférez garder l'icône de batterie d'origine. Choisissez les processus qu'il
gère, ou épinglez un processus sur les cœurs d'efficacité.

**Données avancées, pour votre Mac et votre iPhone.** Charge, santé, cycles,
température et consommation, enregistrés dans le temps pour voir ce qui a
changé. Branchez un iPhone ou un iPad par câble et MacBat suit aussi sa
batterie. Exportez le tout en CSV.

**Des informations utiles, jour et nuit.** MacBat présente l'essentiel sur la
consommation, la santé de la batterie et les processus gérés directement dans le
panneau, et s'efface le reste du temps.

**Une vraie interface, pas un menu de plus.** Des pastilles en Liquid Glass qui
placent les commandes que vous utilisez sous votre pointeur. Le clic droit ouvre
le menu avancé.

**Votre icône, votre choix.** La nouvelle icône de macOS 27 ou la classique.

**Quatre langues.** Français, anglais, portugais et espagnol. MacBat suit la
langue de votre système.

---

## Installation

### Homebrew (officiel)

```bash
brew install --cask 1architect/macbat/macbat
```

Homebrew est la méthode officielle d'installation de MacBat.

### Téléchargement direct (alternative)

N'utilisez cette option que si vous ne pouvez pas utiliser Homebrew.
Téléchargez le `MacBat-x.y.z.zip` le plus récent depuis
[Releases](https://github.com/1architect/macbat-releases/releases/latest),
décompressez-le et faites glisser **MacBat.app** dans votre dossier
Applications.

MacBat est signé en mode ad-hoc, pas avec un Developer ID payant : macOS bloque
donc la première ouverture. Pour l'autoriser :

1. Double-cliquez sur **MacBat.app**. macOS refuse et indique qu'il ne peut pas vérifier le développeur.
2. Ouvrez **Réglages Système → Confidentialité et sécurité**, descendez jusqu'à **Sécurité** et cliquez sur **Ouvrir quand même** dans le message concernant MacBat.
3. Confirmez avec Touch ID ou votre mot de passe.

macOS retient le choix — c'est une étape unique.

> Les anciens guides disent de faire un clic droit et de choisir **Ouvrir**. Ce
> raccourci a été retiré dans macOS 15 et ne fonctionne pas sur les versions
> prises en charge par MacBat.

### Configuration requise

- macOS 26 ou plus récent
- Apple Silicon ou Intel

### Mise à jour

MacBat ne cherche jamais de mise à jour tout seul. Choisissez **Rechercher les
mises à jour…** dans le menu quand vous voulez regarder, ou lancez
`brew upgrade --cask macbat`.

---

## Essayez, puis achetez

MacBat fonctionne entièrement pendant **7 jours**. Ensuite, une licence le
débloque à nouveau. Aucun compte à créer, aucun abonnement — vous l'achetez une
fois.

[**Acheter une licence**](https://giovaniman8.gumroad.com/l/macbat)

Pour activer : ouvrez le menu, choisissez l'élément de licence et saisissez
l'adresse e-mail et la clé reçues dans l'e-mail d'achat.

---

## Confidentialité

MacBat n'a ni statistiques d'usage, ni télémétrie, ni rapport de plantage. Votre
historique de batterie, votre liste de processus et les données de votre
appareil restent sur votre Mac.

MacBat touche au réseau exactement deux fois, et seulement quand vous le
demandez : à la recherche de mise à jour et à l'activation d'une licence. Il
n'établit aucune connexion au lancement, ni en arrière-plan.

Le détail complet — chaque fichier qu'il écrit, chaque champ qu'il envoie — est
dans la [Politique de confidentialité](PRIVACY.fr.md).

---

## Autorisations

Deux fonctions demandent une autorisation administrateur la première fois que
vous les activez — Touch ID ou votre mot de passe, selon ce que votre Mac
utilise. L'autorisation installe une règle `sudoers` limitée aux commandes
exactes dont elles ont besoin, et n'est plus redemandée :

| Fonction | Commandes autorisées |
|---|---|
| Économie d'énergie | `pmset -a lowpowermode 0` / `1` |
| Contrôlé | une liste fixe d'arguments `pmset` pour la veille de l'écran, Power Nap et le réveil par le réseau, plus `tmutil enable` / `disable` |

C'est macOS qui gère l'autorisation : MacBat ne voit jamais votre mot de passe.
Il n'installe aucun daemon en arrière-plan. Retirez les règles quand vous voulez
en supprimant
`/etc/sudoers.d/macbat-economia` et `/etc/sudoers.d/macbat-lowpowermode`.

---

## Assistance

**macbat@giomantovani.com.br**

---

## Licence

MacBat est un logiciel propriétaire. Copyright © 2026 Gio Mantovani /
1architect. Tous droits réservés. Le code source n'est pas public.

Ce dépôt contient les versions publiques, le flux de mise à jour et les
documents ci-dessus.
