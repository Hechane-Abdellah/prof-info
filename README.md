# Site personnel — [NOM DU PROFESSEUR]

Site web personnel et pédagogique pour un professeur d'informatique au collège : portfolio professionnel + espace de cours, exercices et ressources pour les élèves.

## 1. Présentation du projet

Ce site statique présente :
- un **portfolio professionnel** (accueil, à propos) ;
- un **espace pédagogique** : cours par niveau, exercices filtrables, ressources téléchargeables ;
- un **formulaire de contact**.

Il est **100 % gratuit**, fonctionne **sans backend ni base de données**, et est prêt à être hébergé sur **GitHub Pages**.

Tous les contenus (nom, établissement, photo, email, parcours) sont des **placeholders** à remplacer par vos propres informations : `[NOM DU PROFESSEUR]`, `[EMAIL]`, `[ÉTABLISSEMENT]`, `[PHOTO]`, `[ANNÉE]`, `[FORMATION / EXPÉRIENCE]`.

## 2. Technologies utilisées

- HTML5 sémantique
- CSS3 (variables CSS, Grid, Flexbox, animations)
- JavaScript vanilla (aucune dépendance, aucun framework)
- Polices [IBM Plex Mono / IBM Plex Sans](https://fonts.google.com/) via Google Fonts (gratuit)

Aucun outil de build n'est nécessaire : les fichiers peuvent être ouverts et modifiés directement.

## 3. Structure du projet

```
mon-site/
│
├── index.html            → Page d'accueil
├── about.html             → À propos
├── cours.html              → Cours par niveau (1ère, 2ème, 3ème année)
├── exercices.html          → Exercices, TP, activités, évaluations (filtrables)
├── ressources.html          → PDF, Word, Excel, présentations, liens utiles
├── contact.html             → Formulaire de contact
│
├── css/
│   └── style.css          → Toute la feuille de style (design, responsive, animations)
│
├── js/
│   └── script.js           → Menu mobile, animations au scroll, filtres, formulaire
│
├── assets/
│   ├── images/              → Vos images (photo de profil, illustrations…)
│   ├── icons/                → favicon.svg
│   └── documents/            → Vos fichiers PDF / Word / Excel / présentations
│
└── README.md
```

### Ajouter un nouveau cours
Dans `cours.html`, dupliquez une balise `<article class="card ...">` à l'intérieur du bloc de niveau concerné (`#niveau-1`, `#niveau-2` ou `#niveau-3`), puis modifiez le titre, la description, la durée et le lien.

### Ajouter un nouvel exercice
Dans `exercices.html`, dupliquez une carte dans `#exercices-list` en adaptant les attributs `data-niveau` et `data-theme` (utilisés par les filtres) ainsi que le contenu.

### Ajouter une nouvelle ressource
1. Déposez le fichier dans `assets/documents/`.
2. Dans `ressources.html`, dupliquez une carte dans `#ressources-list`, en adaptant `data-niveau`, `data-theme`, le badge de type de fichier et le lien `href` vers votre fichier.

## 4. Lancer le site en local

Aucune installation n'est nécessaire.

**Option simple :** double-cliquez sur `index.html` pour l'ouvrir dans votre navigateur.

**Option recommandée** (pour un rendu identique à celui en ligne) : lancez un petit serveur local depuis le dossier du projet.

Avec Python (déjà installé sur la plupart des systèmes) :
```bash
cd mon-site
python3 -m http.server 8000
```
Puis ouvrez `http://localhost:8000` dans votre navigateur.

Avec l'extension VS Code **Live Server** : clic droit sur `index.html` → « Open with Live Server ».

## 5. Publier le site avec GitHub Pages (gratuit)

1. Créez un dépôt GitHub (par exemple `mon-site`) et poussez-y le contenu de ce dossier :
   ```bash
   cd mon-site
   git init
   git add .
   git commit -m "Premier déploiement du site"
   git branch -M main
   git remote add origin https://github.com/[VOTRE-UTILISATEUR]/mon-site.git
   git push -u origin main
   ```
2. Sur GitHub, ouvrez le dépôt → **Settings** → **Pages**.
3. Dans **Build and deployment**, choisissez **Deploy from a branch**, sélectionnez la branche `main` et le dossier `/ (root)`.
4. Enregistrez : votre site sera publié à l'adresse
   `https://[VOTRE-UTILISATEUR].github.io/mon-site/`
   (la publication prend en général 1 à 2 minutes).

Chaque nouveau `git push` sur la branche `main` met automatiquement à jour le site en ligne.

## 6. Activer réellement le formulaire de contact (gratuit)

Sans backend, le formulaire de `contact.html` affiche pour l'instant un message de démonstration. Pour recevoir réellement les messages par email, deux options gratuites, sans serveur à gérer :

**Option A — [Formspree](https://formspree.io/) (recommandé, simple)**
1. Créez un compte gratuit et un formulaire sur Formspree.
2. Dans `contact.html`, remplacez la balise d'ouverture du formulaire :
   ```html
   <form id="contact-form" novalidate>
   ```
   par :
   ```html
   <form id="contact-form" action="https://formspree.io/f/VOTRE_ID" method="POST">
   ```
3. Dans `js/script.js`, retirez ou adaptez le `e.preventDefault()` du gestionnaire `initContactForm` si vous souhaitez laisser Formspree gérer l'envoi et la redirection.

**Option B — [Web3Forms](https://web3forms.com/)**
Fonctionne de manière similaire : une clé d'accès gratuite est ajoutée dans un champ caché du formulaire, qui est ensuite envoyé en `POST` vers leur API.

Les deux services proposent une offre gratuite largement suffisante pour un site de professeur.

## 7. Accessibilité et SEO

Le site inclut déjà : balises `title` et `meta description` par page, favicon, structure sémantique (`header`, `nav`, `main`, `section`, `article`, `footer`), hiérarchie de titres cohérente, lien d'évitement clavier (« Aller au contenu principal »), focus clavier visible, labels associés aux champs de formulaire, et respect de `prefers-reduced-motion`.

Pensez à ajouter des attributs `alt` descriptifs dès que vous insérez de vraies images (photo de profil, captures d'écran de cours, etc.).
