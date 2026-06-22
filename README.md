# Baromètre conjoncture AACC — auto-positionnement des agences

Mini-site autonome, en une seule page, qui permet à un dirigeant d'agence de se
situer parmi quatre typologies issues du baromètre conjoncture de l'AACC, à partir
de sept questions.

- **Aucune donnée n'est envoyée ni stockée** : tout le calcul se fait dans le navigateur.
- **Zéro dépendance** : HTML + CSS + JavaScript vanilla, sans framework, sans build,
  sans CDN. Fonctionne hors ligne.
- Modes clair et sombre, responsive (mobile d'abord), accessible.

## Contenu

- `index.html` — le site complet (ouvrez-le directement dans un navigateur pour le tester).
- `README.md` — ce fichier.

## Mettre à jour les données à chaque vague

Tout est regroupé dans le **bloc de configuration**, en haut de la balise `<script>`
de `index.html` :

- `SHOW_COHORT_DATA` (booléen, défaut `false`) : passez-le à `true` pour afficher les
  effectifs et pourcentages par typologie ; laissez-le à `false` pour ne montrer que
  les noms de profils, descriptions et conseils.
- `DATA` : pour chaque type (A, B, C, D), son nom, sa position sur la carte
  `[dynamisme ; exposition]`, son effectif et son texte de conseil.

## Mise en ligne

### Option rapide — Netlify Drop (URL immédiate, sans compte technique)

1. Rendez-vous sur **https://app.netlify.com/drop**.
2. Glissez-déposez le **dossier** contenant `index.html` dans la zone indiquée
   (ou seulement le fichier `index.html`).
3. Netlify génère aussitôt une URL publique (type `https://nom-aleatoire.netlify.app`).
   Vous pouvez la renommer ou la sécuriser ensuite en créant un compte gratuit.

Aucune build, aucune configuration : le fichier est servi tel quel.

### Option versionnée — GitHub Pages

Prérequis : `git` et la CLI GitHub `gh` installés et authentifiés (`gh auth login`).

Depuis le dossier du projet :

```bash
git init
git add index.html README.md
git commit -m "Baromètre conjoncture AACC — auto-positionnement"

# Crée le dépôt (public) et pousse la branche par défaut
gh repo create barometre-aacc --public --source=. --remote=origin --push

# Active GitHub Pages sur la branche main, à la racine
gh api -X POST repos/:owner/barometre-aacc/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

L'URL finale sera de la forme :

```
https://<votre-compte>.github.io/barometre-aacc/
```

La première publication peut prendre une ou deux minutes. Vous pouvez vérifier
l'état avec `gh api repos/:owner/barometre-aacc/pages`.

## Méthode et limites

Outil à visée pédagogique : il ne remplace pas le classement officiel de l'AACC.
Les effectifs par typologie sont petits et doivent se lire comme des signaux
qualitatifs. Analyse dérivée du baromètre conjoncture de l'AACC d'avril 2026.
