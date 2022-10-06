# testgitfilterrepo
Utilisation de git filter-repo pour réécrire tous les messages de commit de son repo.

## Documentation

- [Installer git filter-repo](https://github.com/newren/git-filter-repo/blob/main/INSTALL.md)
- [Documentation](https://htmlpreview.github.io/?https://github.com/newren/git-filter-repo/blob/docs/html/git-filter-repo.html)
- [Repo GIT filter repo](https://github.com/newren/git-filter-repo)

La documentation git officielle elle même préconise d'[utiliser git filter-repo plutô que l'ancienne commande native git filter-branch](https://git-scm.com/docs/git-filter-branch)

Bonus mon alias d'history "glola" vient du plugin git de Oh-my-zsh : https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/git.plugin.zsh

[Video Live](https://youtu.be/KVEzLiVVeHw)

## Commandes

Pour convertir de #xxx vers TULEAP-xxx
```bash
git filter-repo --replace-message toTuleap
```

et 

Pour convertir de TULEAP-xxx vers #xxx
```bash
git filter-repo --replace-message fromTuleap
```

## Erreur

En cas d'erreur de type `fatal: replace depth too high for object ...`

Pas de panique tentez cette commande : 

```bash
git replace -d $(git replace | xargs)
```

Et tout devrait rentrer dans l'ordre.
Dans le cas contraire ce n'est pas très grave car vous avez respecté les consignes et vous avez travaillé sur un clone de votre repo de travail habituel donc rien n'est altéré.

## Disclaimer

/!\ Attention cette opération n'est pas sans conséquences potentiellement graves sur votre repository git. 

Travaillez toujours sur un *clone local frais*, ne poussez jamais vers le serveur sans avoir vérifié plusieurs fois que tout est en ordre. 

Prévenez vos collaborateurs et veillez a ce que tout le monde soit synchronisé avec tout son travail commit et push avant ces opérations.
