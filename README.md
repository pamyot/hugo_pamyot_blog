# hugo_pamyot_blog
Source du blog générable avec Hugo.

## Installation de l'environnement local

Suivre les étapes suivantes pour installer l'environnement localement : 

1. Installer [Hugo](https://github.com/spf13/hugo/releases)
2. Extraire ce projet-ci localement.
3. Extrait le projet [pamyot.github.io](https://github.com/pamyot/pamyot.github.io) dans le sous répertoire `pamyot.github.io` du projet source Hugo.

## Tester 

Pour afficher le site Web localement : 

```
hugo server -t blackburn --buildDrafts
```

Pour générer une version à jour du site Web : 

```
hugo server -t blackburn 
```

## Déployer

Étant donné la structure retenue, il est possible de mettre à jour de façon indépendante le code source du site Web sur 
Github et le site Web généré qui sont dans deux projets différents.


