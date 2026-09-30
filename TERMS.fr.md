[English](TERMS.md) · [Português](TERMS.pt-BR.md) · [Español](TERMS.es.md) · **Français**

# Conditions d'utilisation — MacBat

**Dernière mise à jour : 30 septembre 2026 · S'applique à MacBat 1.0.0 et versions ultérieures**

Les présentes conditions régissent l'utilisation de MacBat, l'app de barre des
menus pour macOS publiée par Gio Mantovani / 1architect (« nous »), de son site
web et de son dépôt public de versions. En installant ou en utilisant MacBat,
vous les acceptez. Si vous ne les acceptez pas, n'installez pas et n'utilisez
pas MacBat.

---

## 1. La licence

MacBat est un logiciel propriétaire. Votre droit d'utilisation est défini par la
[Licence propriétaire de MacBat](LICENSE.fr.md) : un droit personnel, limité,
révocable, non exclusif et incessible d'installer et d'utiliser MacBat. Les
présentes conditions complètent la licence ; en cas de conflit, la licence
l'emporte pour la propriété intellectuelle et les présentes conditions pour tout
le reste.

## 2. Fonctions gratuites, essai et licence payante

- **Essai.** Toute nouvelle installation inclut 7 jours d'essai gratuit avec
  toutes les fonctions débloquées.
- **Après l'essai,** l'icône de la barre des menus, le pourcentage et le temps
  restant restent gratuits. Sentinelle, le mode Contrôlé, les Données de la
  batterie et les icônes supplémentaires nécessitent une licence.
- **Licence.** La licence est un achat unique, pas un abonnement. Elle
  s'active avec la clé que vous recevez de Gumroad et vaut pour **3 activations**
  au maximum. Ne partagez, ne revendez et ne publiez pas votre clé.
- **Achats et remboursements.** Les achats sont traités par Gumroad, vendeur
  responsable du paiement. Le paiement, les taxes et les remboursements suivent
  les conditions de Gumroad et les droits des consommateurs applicables là où
  vous vivez. Questions sur un achat : macbat@giomantovani.com.br.
- Nous pouvons modifier les prix et la répartition des fonctions gratuites et
  payantes dans les versions futures. Une modification ne retire jamais d'une
  licence déjà achetée une fonction de la version avec laquelle elle a été
  achetée.

## 3. Ce que MacBat fait sur votre Mac

MacBat est un utilitaire qui lit des données d'énergie et, lorsque vous activez
la fonction, modifie le comportement de votre Mac. Il est important de savoir
exactement ce que cela implique :

- **Sentinelle** met en pause et reprend des processus, ou les déplace vers les
  cœurs d'efficacité, pour réduire leur utilisation du processeur. Un processus
  mis en pause de façon trop agressive peut devenir lent, ne plus répondre ou
  perdre du travail non enregistré. Vous choisissez les processus qu'elle gère
  et pouvez la désactiver à tout moment.
- **Le mode Contrôlé et le mode Économie d'énergie** modifient des réglages
  d'énergie du système (`pmset`), et Contrôlé les rétablit lorsque vous le
  désactivez.
- **Le contrôle des processus système** (facultatif) permet à Sentinelle d'agir
  sur les processus d'autres utilisateurs et sur les services d'arrière-plan de
  macOS. Ne l'utilisez que si vous comprenez les processus que vous affectez.
- **Autorisation d'administrateur.** Ces fonctions demandent une fois Touch ID
  ou votre mot de passe, via macOS lui-même. MacBat ne voit jamais le mot de
  passe. Il installe des règles `sudoers` limitées aux commandes exactes de
  chaque fonction, que vous pouvez supprimer à tout moment, comme décrit dans la
  [Politique de confidentialité](PRIVACY.fr.md).
- **Les données de batterie et d'appareils** proviennent d'interfaces de macOS,
  dont certaines ne sont pas documentées par Apple et peuvent changer à chaque
  mise à jour. Le temps restant, la santé et les autres mesures sont des
  **estimations** et peuvent être inexactes. Ne vous fiez pas à MacBat pour quoi
  que ce soit de critique pour la sécurité.
- La lecture d'un iPhone ou d'un iPad connecté passe par le service local
  `usbmuxd` et ne lit que l'état de la batterie.

## 4. Utilisation acceptable

Vous vous engagez à ne pas : copier, modifier, redistribuer, louer ni revendre
MacBat ; tenter de le décompiler, sauf là où la loi l'autorise ; contourner,
altérer ou partager le mécanisme d'essai ou de licence ; ni utiliser MacBat pour
interférer avec des ordinateurs ou des données qui ne sont pas les vôtres ou que
vous n'êtes pas autorisé à gérer.

## 5. Mises à jour

MacBat ne recherche pas les mises à jour de lui-même. Vous décidez quand
utiliser **Rechercher les mises à jour…** ou `brew upgrade --cask macbat`. Nous
ne promettons aucun calendrier de versions, et les correctifs de sécurité ne
sont appliqués qu'à la dernière version (voir [Sécurité](SECURITY.fr.md)). Il
vous incombe de garder MacBat compatible avec votre version de macOS ; MacBat
nécessite macOS 26 ou ultérieur.

## 6. Confidentialité

MacBat ne collecte aucune donnée vous concernant. Son fonctionnement, ce qui
reste sur votre Mac et les deux seuls moments où il utilise le réseau sont
décrits dans la [Politique de confidentialité](PRIVACY.fr.md), qui fait partie
des présentes conditions.

## 7. Absence de garantie

MacBat est fourni **« en l'état » et « selon disponibilité »**, sans garantie
d'aucune sorte, expresse ou implicite, y compris d'adéquation à un usage
particulier, d'exactitude des estimations ou de fonctionnement ininterrompu et
sans erreur. Nous ne garantissons pas que MacBat économise une quantité précise
de batterie.

## 8. Limitation de responsabilité

Dans la mesure maximale permise par la loi, nous ne sommes pas responsables des
dommages indirects, accessoires ou consécutifs, de la perte de données, du
manque à gagner ni des dommages causés à votre Mac ou à d'autres appareils par
l'utilisation de MacBat ou l'impossibilité de l'utiliser. Notre responsabilité
totale pour toute réclamation est limitée au montant que vous avez payé pour
votre licence MacBat. Rien dans les présentes conditions ne limite la
responsabilité qui ne peut l'être par la loi, ni les droits impératifs des
consommateurs.

## 9. Résiliation

Vous pouvez cesser d'utiliser MacBat à tout moment en le supprimant et, si vous
le souhaitez, en effaçant ses données et les règles `sudoers`. Nous pouvons
révoquer une licence utilisée en violation des présentes conditions, par exemple
partagée ou revendue, ou obtenue par rétrofacturation ou paiement frauduleux. À
la résiliation, vous devez cesser d'utiliser MacBat et supprimer vos copies.

## 10. Modification des conditions

Si nous modifions ces conditions, ce document change avec elles et la date en
haut également. L'historique de ce fichier est public dans ce dépôt. Continuer à
utiliser MacBat après une modification vaut acceptation des nouvelles
conditions.

## 11. Droit applicable

Les présentes conditions sont régies par le droit brésilien, sans égard à ses
règles de conflit de lois. Les règles impératives de protection des
consommateurs du pays où vous vivez continuent de s'appliquer. Tout litige peut
être porté devant la juridiction où vous pouvez agir en vertu de ces règles et,
à défaut, devant les tribunaux du Brésil.

## 12. Contact

Questions sur ces conditions ou demandes d'autorisation :

**macbat@giomantovani.com.br**

Le texte anglais est la version de référence en cas de divergence entre les
traductions.
