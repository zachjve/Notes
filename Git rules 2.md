Organisation du projet sur GitHub pour un groupe de 5 personnes en utilisant une branche principale, des branches de fonctionnalités et des forks.

#### Branche principale (`main`)
Elle contiendra le code stable et fonctionnel.

#### Utiliser des forks
Un fork est une copie du dépôt d'origine dans le compte GitHub du contributeur. Les contributeurs travaillent sur leur fork, puis soumettent des pull requests pour proposer des modifications à intégrer dans le dépôt d'origine.

Pour créer son fork :

1. Se rendre sur l'organisation et cliquer sur le repo.
2. Cliquer sur fork en haut a gauche.
3. Créer un fork.

Dans votre fork :

##### Créer des branches de fonctionnalités

Chaque membre de l'équipe doit créer des branches de fonctionnalités pour développer de nouvelles fonctionnalités ou résoudre des problèmes spécifiques. Pour créer une nouvelle branche à partir de `main` :

Créer et basculer vers une nouvelle branche pour votre fonctionnalité (remplacer `<feature-branch>` par le nom de votre branche) :  

```bash
git checkout -b <feature-branch>
```

Pour verifier que vous êtes sur votre branch de fonctionnalitée :

```bash
git branch
```  

Pour bien faire en sorte que la branche contient tout les MAJ du fork main :

```bash
git merge main
```

###### Commencer à travailler votre fonctionnalitée sur la branch.

Une fois que la branche est créé et contient toute les MAJ `travailler sur votre fonctionnalitée`. Pendant que vous travaillez vous devez faire vos `add` vos `commit` et `push` toujours sur la branche de fonctionnalitée en s'assurant de bien push vers la fork.

Pour cela verifier le remote (l'endroit ou sera push le travail) :

```bash
git remote -v
```  

Pour changer le remote si nécéssaire (new URL c'est l'URL de votre fork, changer `zachjve` par votre `pseudo` github) :

```bash
git remote set-url origin https://github.com/zachjve/Smart-Garden-Repo.git
```

Pour push une branch la première fois il faut `upstream` la branche (remplacer `<feature-branch>` par un nom de votre branche) :

```bash
git push --set-upstream origin <feature-branch>
```

Pour les push suivant sur cette même branche :

```bash
git push
```

Maintenant vous pouvez voir votre travail sur github sur la branche que vous avez créée :)  

Une fois le travail sur la branche terminé (la fin d'une fonctionnalité) et une fois que tout fonctionne sur la branche il faut `merge` votre branche avec votre `main` (du fork) mais si *avant on va mettre à jour le fork avec le repository de l'organisation :* (si il y a eu des modifications)

##### Mettre à jour le fork

Pour ajouter le lien "upstream" donc la connection avec le depot distant de l'organisation et ainsi pouvoir récupérer les MAJ (`set-url` au lieu de `add`) pour le modifier :

```bash
git remote add upstream https://github.com/smart-garden-itakademy/Smart-Garden-Repo.git
```

Avec le git remote -v on verifie que le remote origin est bien le fork et le remote upstream est bien celui de l'organisation (avec votre pseudo pour le `origin`)

```bash
origin https://github.com/zachjve/Smart-Garden-Repo.git (fetch)
origin https://github.com/zachjve/Smart-Garden-Repo.git (push)
upstream https://github.com/smart-garden-itakademy/Smart-Garden-Repo.git (fetch)
upstream https://github.com/smart-garden-itakademy/Smart-Garden-Repo.git (push)
```

**À finir**  

##### Merge une branche de fonctionnalité avec la branche main  

1. Se replacer sur le `main` (du fork)

```bash
git checkout main
```
  
2. Merge la branche sur la branche main, (remplacer `<feature-branch>` par un nom descriptif pour votre branche) :

```bash
git merge <feature-branch>
```

Faire une pull requests pour merge son fork avec l'upstream (repository de l'organisation)