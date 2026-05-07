# QualPack V24 — Multi-client + essai 30 jours

Version préparée à partir de QualPack V23 Public.

## Objectif V24

Cette version permet d'utiliser une seule application GitHub Pages avec un seul projet Supabase QUALPACK, tout en séparant les données par client grâce au champ `site_id`.

Exemples de liens :

- Traiteur de la Thur : `https://ton-lien-github/qualpack/?site_id=traiteur_de_la_thur`
- Moulin des Moines : `https://ton-lien-github/qualpack/?site_id=moulin_des_moines`

## Modifications intégrées

### 1. Lecture automatique du `site_id` depuis l'URL

L'application lit automatiquement le paramètre :

```text
?site_id=moulin_des_moines
```

Si le paramètre est présent, il devient le site actif.

### 2. Mémorisation locale du `site_id`

Le `site_id` est mémorisé dans le navigateur via `localStorage`.

Si l'utilisateur revient sans paramètre URL, l'application réutilise le dernier `site_id` connu.

Si aucun `site_id` n'est trouvé, la valeur de compatibilité est :

```text
traiteur_de_la_thur
```

### 3. Filtrage Supabase par `site_id`

Les lectures Supabase du catalogue sont filtrées par `site_id` :

- `clients`
- `produits`
- `lignes`
- `operateurs`

Cela évite de mélanger les catalogues entre plusieurs sociétés.

### 4. Import Excel affecté au bon `site_id`

Le template Excel reste universel.

Le client ne doit pas saisir `site_id` dans le fichier Excel.

Lors de l'import, QualPack ajoute automatiquement le `site_id` actif aux données envoyées dans Supabase.

Le fichier peut être renommé librement, par exemple :

```text
QualPack_Template_Traiteur_de_la_Thur.xlsx
QualPack_Template_Moulin_des_Moines.xlsx
```

Le nom du fichier n'a pas d'impact technique sur l'import.

### 5. Synchro pesées + détecteurs avec `site_id`

Les synchronisations vers Supabase ajoutent automatiquement le `site_id` actif dans :

- `pesees`
- `detecteurs`

### 6. Essai gratuit 30 jours

Un essai de 30 jours est activé localement par site.

- Le début d'essai est enregistré au premier lancement du site.
- Une alerte apparaît dans les 7 derniers jours.
- Après 30 jours, l'accès est bloqué avec un message invitant à contacter CODEX EXPERTISE.

Limite volontaire de la V24 : ce contrôle est local au navigateur. Il est suffisant pour des tests terrain, mais pourra être remplacé plus tard par une vraie gestion de licence Supabase.

### 7. Mise à jour du cache PWA

Le cache du service worker a été mis à jour :

```js
const CACHE_NAME = 'qualpack-v24-siteid-trial-1';
```

Cela force un rafraîchissement propre après déploiement.

## Fichiers modifiés

- `index.html`
- `sync.js`
- `sw.js`

## Fichiers non modifiés volontairement

- `db.js`
- `pdf-v2.js`
- `xlsx.full.min.js`
- `jspdf.umd.min.js`
- structure du template Excel
- noms des tables et colonnes Supabase

## Checklist de test après déploiement

### Test Traiteur de la Thur

1. Ouvrir : `https://ton-lien-github/qualpack/?site_id=traiteur_de_la_thur`
2. Importer le template Traiteur de la Thur.
3. Saisir 20 pesées.
4. Faire un test détecteur.
5. Vérifier dans Supabase que les nouvelles lignes ont :

```text
site_id = traiteur_de_la_thur
```

### Test Moulin des Moines

1. Ouvrir : `https://ton-lien-github/qualpack/?site_id=moulin_des_moines`
2. Importer le template Moulin des Moines.
3. Saisir 20 pesées.
4. Faire un test détecteur.
5. Vérifier dans Supabase que les nouvelles lignes ont :

```text
site_id = moulin_des_moines
```

## Important

Ne pas utiliser le même lien sans `site_id` pour un nouveau client.

Toujours envoyer un lien contenant le bon paramètre, par exemple :

```text
https://ton-lien-github/qualpack/?site_id=moulin_des_moines
```
