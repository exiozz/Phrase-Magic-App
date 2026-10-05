# ✦ Phrases Magiques

> Une petite bibliothèque personnelle de réponses prêtes à
> copier-coller.

**Phrases Magiques** est une application web 100 % côté client qui
permet de stocker, organiser, rechercher et copier rapidement des
réponses/messages réutilisables.

L'application est contenue dans un seul fichier `index.html` et ne
nécessite ni serveur, ni base de données, ni installation de
dépendances.

------------------------------------------------------------------------

## 🚀 Démarrage

### La méthode la plus simple

1.  Télécharge ou récupère le fichier `index.html`.
2.  Ouvre-le directement avec ton navigateur.
3.  C'est tout : l'application fonctionne immédiatement.

Le projet charge ses données depuis le navigateur et utilise
`localStorage` pour conserver les phrases, les catégories, les
préférences d'interface et le thème.

> ⚠️ Comme les données sont stockées dans le navigateur, pense à
> utiliser **Exporter** régulièrement pour faire une sauvegarde.

------------------------------------------------------------------------

## 🧠 Comment ça fonctionne ?

L'application fonctionne entièrement en local :

``` text
┌─────────────────────┐
│      index.html     │
│                     │
│ HTML + CSS + JS     │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│     localStorage    │
│                     │
│ • phrases           │
│ • catégories        │
│ • thème             │
│ • préférences UI    │
└─────────────────────┘
```

Il n'y a pas de backend ni d'API nécessaire.

Les données sont enregistrées automatiquement après les modifications.

------------------------------------------------------------------------

## ✨ Fonctionnalités

### 📝 Gestion des phrases

Tu peux :

-   créer une nouvelle phrase ;
-   modifier une phrase existante ;
-   supprimer une phrase ;
-   dupliquer une phrase ;
-   ajouter ou retirer une phrase des favoris ;
-   ouvrir un aperçu complet ;
-   copier une phrase en un clic ;
-   voir combien de fois une phrase a été copiée ;
-   voir quand elle a été utilisée pour la dernière fois.

Une phrase possède notamment :

-   un **titre** ;
-   une **catégorie** ;
-   un **texte** ;
-   un statut **favori** ;
-   un compteur d'utilisations ;
-   une date de création ;
-   une date de dernière copie.

------------------------------------------------------------------------

## 🔎 Recherche

La recherche permet de retrouver rapidement une phrase à partir du
titre, du texte ou de la catégorie.

La recherche est :

-   insensible à la casse ;
-   insensible aux accents.

Par exemple, une recherche comme :

``` text
paiement
```

peut retrouver une phrase contenant `Paiement`.

Les termes recherchés sont également surlignés dans les résultats.

------------------------------------------------------------------------

## 🗂️ Catégories

Les phrases peuvent être organisées par catégorie.

Tu peux :

-   créer une catégorie ;
-   sélectionner une catégorie pour filtrer les phrases ;
-   renommer une catégorie ;
-   supprimer une catégorie.

Une nouvelle catégorie peut également être créée directement depuis
l'éditeur d'une phrase.

------------------------------------------------------------------------

## ⭐ Favoris

Une phrase peut être ajoutée aux favoris avec l'étoile `★`.

La vue **Favoris** permet ensuite de retrouver uniquement les phrases
importantes.

Le tri par défaut place les favoris en priorité.

------------------------------------------------------------------------

## 📋 Copier une phrase

Chaque carte possède un bouton **Copier**.

Lorsqu'une phrase est copiée :

1.  son texte est envoyé dans le presse-papiers ;
2.  son compteur d'utilisation est augmenté ;
3.  sa date de dernière utilisation est mise à jour ;
4.  l'interface confirme la copie.

L'application utilise `navigator.clipboard` et possède un mécanisme de
secours pour les navigateurs qui ne permettent pas cette méthode.

------------------------------------------------------------------------

## 🧩 Champs dynamiques

Une fonctionnalité importante permet de créer des phrases avec des
champs à remplir.

Il suffit d'écrire un élément entre crochets :

``` text
Bonjour [prénom],

Voici le devis concernant votre projet :
• Prestation : [description]
• Prix : [montant]
• Délai : [délai]
```

Lors de la copie, l'application détecte automatiquement ces champs et
affiche un formulaire permettant de les remplir.

### Exemple

Phrase enregistrée :

``` text
Bonjour [prénom], le montant total est de [montant] €.
```

Au moment de copier :

``` text
prénom  → Thomas
montant → 450
```

Résultat copié :

``` text
Bonjour Thomas, le montant total est de 450 €.
```

Il est également possible de **copier sans remplir les champs**.

------------------------------------------------------------------------

## ↕️ Tri des phrases

Plusieurs modes de tri sont disponibles :

  Mode                    Fonctionnement
  ----------------------- -----------------------------------------
  **Favoris d'abord**     Favoris, puis nombre d'utilisations
  **Plus utilisées**      Les phrases les plus copiées en premier
  **Récemment copiées**   Les dernières phrases utilisées
  **Plus récentes**       Les phrases récemment créées
  **A → Z**               Tri alphabétique par titre

------------------------------------------------------------------------

## 🌗 Thème clair / sombre

L'application démarre en thème sombre.

Le bouton de thème permet de passer entre :

-   🌙 thème sombre ;
-   ☀️ thème clair.

Le choix est mémorisé dans le navigateur.

------------------------------------------------------------------------

## 💾 Stockage des données

Les données sont stockées avec `localStorage`.

Les clés utilisées par l'application sont :

``` text
phrases-magiques-v1
phrases-magiques-cats
phrases-magiques-theme
phrases-magiques-ui
```

### Important

Les données sont liées au navigateur utilisé.

Par exemple, les phrases enregistrées dans Chrome sur un ordinateur ne
seront pas automatiquement disponibles dans un autre navigateur ou sur
un autre appareil.

C'est pour cette raison que la fonction d'export est importante.

------------------------------------------------------------------------

## 📤 Exporter

Le bouton **Exporter** génère un fichier JSON contenant les phrases.

Le fichier est nommé automatiquement selon la date :

``` text
phrases-magiques-AAAA-MM-JJ.json
```

Exemple :

``` text
phrases-magiques-2026-10-05.json
```

L'export permet notamment de :

-   sauvegarder ses phrases ;
-   transférer ses phrases vers un autre navigateur ;
-   conserver une copie de secours ;
-   partager une bibliothèque de phrases.

------------------------------------------------------------------------

## 📥 Importer

Le bouton **Importer** permet de charger un fichier JSON précédemment
exporté.

Deux possibilités sont proposées :

### Ajouter

Les nouvelles phrases sont ajoutées aux phrases existantes.

Les doublons correspondant au même titre et au même texte sont ignorés.

### Tout remplacer

Les phrases actuellement présentes sont remplacées par celles du fichier
importé.

> ⚠️ Utilise cette option avec attention.

Si le fichier n'est pas un export valide, l'application refuse l'import.

------------------------------------------------------------------------

## ⌨️ Raccourcis clavier

### Général

  Raccourci    Action
  ------------ ---------------------------
  `/`          Ouvrir la recherche
  `Ctrl + K`   Ouvrir la recherche
  `N`          Créer une nouvelle phrase
  `?`          Afficher les raccourcis
  `Ctrl + Z`   Annuler une suppression

### Dans la recherche

  Raccourci   Action
  ----------- ----------------------------
  `Entrée`    Copier le premier résultat
  `↓`         Aller aux résultats
  `Échap`     Effacer la recherche

### Sur une phrase sélectionnée

  Raccourci   Action
  ----------- -------------------------------
  `← ↑ → ↓`   Naviguer entre les phrases
  `Entrée`    Copier
  `Espace`    Ouvrir l'aperçu
  `E`         Modifier
  `F`         Ajouter / retirer des favoris
  `Suppr`     Supprimer

------------------------------------------------------------------------

## 📱 Responsive

L'interface est prévue pour fonctionner sur :

-   ordinateur ;
-   tablette ;
-   mobile.

Sur les petits écrans :

-   le menu de navigation est réduit ;
-   les cartes passent sur une seule colonne ;
-   les fenêtres deviennent des panneaux depuis le bas de l'écran ;
-   un bouton flottant permet de créer rapidement une phrase.

------------------------------------------------------------------------

## 🎨 Technologies utilisées

Le projet repose uniquement sur des technologies natives du navigateur :

-   **HTML5**
-   **CSS3**
-   **JavaScript**
-   **Web Storage API / `localStorage`**
-   **Clipboard API**
-   **`<dialog>`**
-   **IntersectionObserver**
-   **CSS animations**

Aucune bibliothèque JavaScript ou framework n'est nécessaire.

Les polices utilisées dans l'interface sont **Inter** et **Michroma**
via Google Fonts.

------------------------------------------------------------------------

## 📁 Structure du projet

Le projet actuel peut rester extrêmement simple :

``` text
.
└── index.html
```

Tout est regroupé dans le fichier :

``` text
index.html
```

Le fichier contient :

``` text
HTML
├── structure de l'application
├── navigation
├── formulaires
├── dialogues
└── cartes de phrases

CSS
├── thème sombre
├── thème clair
├── responsive
├── animations
└── composants UI

JavaScript
├── stockage local
├── gestion des phrases
├── catégories
├── recherche
├── tri
├── favoris
├── copier / coller
├── champs dynamiques
├── import / export
├── raccourcis clavier
└── gestion du thème
```

------------------------------------------------------------------------

## 🛠️ Modifier le projet

Pour modifier le contenu ou le comportement de l'application, ouvre :

``` text
index.html
```

Le code JavaScript est situé à la fin du fichier, dans :

``` html
<script>
    ...
</script>
```

### Ajouter des phrases par défaut

Les phrases initiales sont définies dans :

``` javascript
const DEFAULTS = [
    ...
];
```

Tu peux y ajouter tes propres phrases.

Exemple :

``` javascript
{
  title: "Ma nouvelle phrase",
  category: "Ma catégorie",
  text: `Bonjour [prénom],

Voici mon message.`
}
```

------------------------------------------------------------------------

## 🧪 Développement

Comme l'application est entièrement côté client, il n'est pas
obligatoire d'utiliser un serveur de développement.

Pour tester rapidement une modification :

``` text
1. Modifier index.html
2. Enregistrer
3. Ouvrir / actualiser index.html dans le navigateur
```

Pour un développement plus confortable, tu peux aussi utiliser un
serveur local comme **Live Server** dans VS Code.

------------------------------------------------------------------------

## 🔐 Vie privée

Les phrases sont enregistrées localement dans le navigateur.

L'application ne nécessite pas de compte utilisateur ni de base de
données distante.

Cependant :

-   vider les données du site peut supprimer les phrases locales ;
-   changer de navigateur peut donner accès à une bibliothèque
    différente ;
-   changer d'appareil ne transfère pas automatiquement les données.

➡️ **Toujours exporter la bibliothèque avant une migration ou une
réinstallation.**

------------------------------------------------------------------------

## 📝 Données d'import/export

Les exports utilisent le format JSON.

Une phrase ressemble notamment à ceci :

``` json
{
  "id": "identifiant",
  "title": "Envoi du devis",
  "text": "Bonjour ! Voici mon devis...",
  "category": "Devis & Budget",
  "fav": true,
  "uses": 12,
  "lastUsed": 1760000000000,
  "createdAt": 1760000000000
}
```

Lors d'un import, l'application vérifie que les éléments nécessaires
(`title` et `text`) sont présents avant de les ajouter.

------------------------------------------------------------------------

## ⚠️ À savoir

### Les données ne sont pas synchronisées

Il n'y a actuellement pas de compte utilisateur ni de synchronisation
cloud.

### L'application dépend du navigateur

Si le `localStorage` est supprimé, les données locales peuvent
disparaître.

### L'export est donc la sauvegarde principale

Prendre l'habitude d'exporter régulièrement sa bibliothèque est
recommandé.

------------------------------------------------------------------------

## 💡 Résumé

**Phrases Magiques**, c'est une mini-app locale pour :

``` text
📝 Écrire
   ↓
🗂️ Organiser
   ↓
🔎 Rechercher
   ↓
✏️ Personnaliser
   ↓
📋 Copier
   ↓
🚀 Répondre rapidement
```

Tout fonctionne directement dans le navigateur, sans backend.

------------------------------------------------------------------------

## 📄 Licence

Aucune licence spécifique n'est définie dans le projet actuel.

Si ce projet doit être publié ou partagé, ajoute une licence adaptée,
par exemple MIT.
