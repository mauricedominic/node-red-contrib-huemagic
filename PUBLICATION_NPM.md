# Guide de publication sur npm

Ce guide vous explique comment publier votre fork de `node-red-contrib-huemagic` sur npm pour pouvoir l'utiliser en production.

## Prérequis

1. **Compte npm** : Si vous n'avez pas encore de compte npm, créez-en un sur [https://www.npmjs.com/signup](https://www.npmjs.com/signup)

2. **Node.js et npm installés** : Vérifiez que vous avez Node.js et npm installés :
   ```bash
   node --version
   npm --version
   ```

## Étapes de publication

### 1. Se connecter à npm

Ouvrez un terminal dans le répertoire du projet et connectez-vous à npm :

```bash
npm login
```

Vous devrez entrer :
- Votre nom d'utilisateur npm
- Votre mot de passe
- Votre adresse email

### 2. Vérifier la configuration du package

Le fichier `package.json` a été configuré avec :
- **Nom du package** : `node-red-contrib-huemagic-napadelice` (nom unique pour éviter les conflits)
- **Version** : `4.2.8`
- **Auteur** : napadelice
- **Repository** : Votre fork GitHub

### 3. Vérifier que tout est prêt

Avant de publier, vérifiez que :
- Tous vos changements sont commités
- Le package.json est correct
- Vous êtes dans le bon répertoire

```bash
# Vérifier le contenu du package.json
cat package.json

# Vérifier que vous êtes connecté
npm whoami
```

### 4. Tester la publication (optionnel mais recommandé)

Vous pouvez tester votre package localement avant de le publier :

```bash
# Créer un package local
npm pack

# Cela créera un fichier .tgz que vous pouvez tester
```

### 5. Publier sur npm

Une fois prêt, publiez votre package :

```bash
npm publish
```

Si vous utilisez un scope (nom commençant par `@`), utilisez :

```bash
npm publish --access public
```

### 6. Vérifier la publication

Après la publication, vérifiez que votre package est bien disponible :

```bash
npm view node-red-contrib-huemagic-napadelice
```

Vous pouvez aussi le voir sur le site npm : [https://www.npmjs.com/package/node-red-contrib-huemagic-napadelice](https://www.npmjs.com/package/node-red-contrib-huemagic-napadelice)

## Utilisation dans Node-RED

Une fois publié, vous pouvez installer votre package dans Node-RED de deux façons :

### Méthode 1 : Via l'interface Node-RED

1. Ouvrez Node-RED
2. Allez dans le menu (☰) > **Manage palette**
3. Cliquez sur l'onglet **Install**
4. Recherchez `node-red-contrib-huemagic-napadelice`
5. Cliquez sur **Install**

### Méthode 2 : Via la ligne de commande

```bash
cd ~/.node-red  # ou le répertoire de votre installation Node-RED
npm install node-red-contrib-huemagic-napadelice
```

Puis redémarrez Node-RED.

## Mettre à jour le package

Quand vous voulez publier une nouvelle version :

1. **Mettez à jour la version** dans `package.json` :
   ```bash
   npm version patch  # pour 4.2.8 -> 4.2.9
   # ou
   npm version minor  # pour 4.2.8 -> 4.3.0
   # ou
   npm version major  # pour 4.2.8 -> 5.0.0
   ```

2. **Commitez et poussez** les changements :
   ```bash
   git add package.json
   git commit -m "Bump version to X.X.X"
   git push
   ```

3. **Publiez** :
   ```bash
   npm publish
   ```

## Notes importantes

- **Nom unique** : Le nom `node-red-contrib-huemagic-napadelice` est unique et vous appartient. Si vous préférez un autre nom, modifiez-le dans `package.json` avant la première publication.

- **Version** : Assurez-vous d'incrémenter la version à chaque publication pour que les utilisateurs puissent obtenir les mises à jour.

- **Licence** : Le package conserve la licence Apache-2.0 du projet original, ce qui est conforme pour un fork.

- **Dépendances** : Toutes les dépendances sont déjà listées dans `package.json` et seront installées automatiquement lors de l'installation du package.

## Dépannage

### Erreur : "You do not have permission to publish"
- Vérifiez que vous êtes connecté avec `npm whoami`
- Vérifiez que le nom du package n'est pas déjà pris par quelqu'un d'autre

### Erreur : "Package name too similar"
- Choisissez un nom plus différent dans `package.json`

### Le package n'apparaît pas dans Node-RED
- Assurez-vous que le nom du package commence par `node-red-contrib-` pour qu'il soit reconnu par Node-RED
- Redémarrez Node-RED après l'installation

## Support

Pour toute question ou problème, vous pouvez :
- Ouvrir une issue sur votre repository GitHub
- Consulter la documentation npm : [https://docs.npmjs.com/](https://docs.npmjs.com/)

