# Débuter un projet avec webpack

### Architecture :

```
dossier-projet/
+ node_modules/
+ src/
+ dist/
+ package.json
+ .gitignore
+ .babelrc
+ yarn.lock
```

- src : contiendra le code de développement, là où je vais coder
- dist : contiendra le code final, le code de production, là où webpack va écrire, je n'y touche pas manuellement
- package.json  : la carte d'identité du projet, contient la liste des dépendances nécessaires à mon projet
- node_modules : contient les dépendances, on n'a pas besoin de les partager puisqu'elles sont listées dans package.json, se construit automatiquement quand j'appelle la commande `yarn`
- .gitignore : contient les choses à ne pas partager sur github en autre node_modules
- .babelrc : fichier de configuration de babel, on y précise quelle "langues" babel doit comprendre (es6 et jsx)
- yarn.lock : fichier créé par yarn et nécessaire à son fonctionnement

### Outils :
- "@babel/core": le noyaux de babel, notre traducteur,
- "@babel/preset-env": dictionnaire pour parler ES6+,
- "@babel/preset-react": dictionnaire pour parler JSX,
- "babel-loader": le lien entre webpack et babel, ce qui permet à webpack de faire travailler babel quand on l'appelle,
- "webpack": le chef d'orchestre qui reprend tout monde de dev dans src pour le rassembler dans dist, il pourra sous traiter certaines actions à d'autres outils,
- "webpack-cli": nécessaire au fonctionnement de webpack dans le terminal,
- "webpack-dev-server": outil qui regarde en live en continu mes modifs dans src, chaque fois que je fais une modif il rassemble en direct mes modifications et me permet de les voir dans le navigateurs

### Scripts : 

```json
"scripts": {
    "build": "webpack --mode production --module-bin",
    "start": "webpack-dev-server --open --mode development --module js=babel-loader --content-base dist/"
}
```

Les scripts sont des raccourcis pour executer certaines commandes

- Ici le raccourci build pourra être lancé avec la commande `yarn build` il aura pour effet de lancer le travail de webpack
- ici start lancera le travail de webpack-dev-server
