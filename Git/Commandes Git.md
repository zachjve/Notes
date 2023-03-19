Pour connecter un repository distant avec le local pour push donc set un nouveau remote.

```bash
git remote add origin http://lien.git
```

Pour vérifier le remote.

```bash
git remote -v
```

```bash
git status
```

```bash
git add nom_du_fichier
```

```bash
git commit -m " "
```

Pour push vers un depot distant, -u va lier pour les futurs push le depot distant, cette commande est à faire après le `git remote add origin` ensuite on pourra utiliser git push. 

```bash
git push -u origin main
git push
```

Pour récupérer un depot distant vers son local

```bash
git clone http://lien.git
```


