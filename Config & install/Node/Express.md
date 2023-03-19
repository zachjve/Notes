Express simplifie la création de serveurs HTTP et la gestion des routes, des requêtes et des réponses. Cela permet de réduire la quantité de code à écrire et d'accélérer le développement d'une application.

Se placer sur le repository du projet et pour créer le `package.json` rapidement. 

```bash
npm init -y
```

#### Installer Express & lancer le serveur

Création du fichier `package-lock.json` et du dossier `node_module`.

```bash
npm install express
```

Créer un fichier  `app.js` importer `express` et créer un listen du port 3000. 

```js
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Bonjour, bienvenue sur mon serveur Express !');
});

app.listen(port, () => {
  console.log(`Le serveur est en fonctionnement à l'adresse http://localhost:${port}`);
});
```

Lancer le serveur avec la commande puis aller sur http://localhost3000.

```bash
node app.js
```

Pour stopper le serveur faire `'ctrl'` `'C'