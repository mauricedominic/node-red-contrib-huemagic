# Workflow de publication recommandé

## État actuel
- Vous êtes sur la branche `feature/bridgepro` avec des améliorations
- Des modifications du `package.json` sont en attente
- La branche `master` n'a pas encore les changements de `feature/bridgepro`

## Étapes recommandées avant publication

### Option 1 : Merger dans master puis publier (RECOMMANDÉ)

```bash
# 1. Retourner sur feature/bridgepro
git checkout feature/bridgepro

# 2. Commiter les modifications du package.json et du guide
git add package.json PUBLICATION_NPM.md
git commit -m "Configure package for npm publication with napadelice branding"

# 3. Pousser les changements
git push origin feature/bridgepro

# 4. Basculer sur master
git checkout master

# 5. Merger feature/bridgepro dans master
git merge feature/bridgepro

# 6. Pousser master
git push origin master

# 7. Publier sur npm depuis master
npm login
npm publish
```

### Option 2 : Publier directement depuis feature/bridgepro (si vous préférez)

```bash
# 1. Commiter les modifications
git add package.json PUBLICATION_NPM.md
git commit -m "Configure package for npm publication with napadelice branding"

# 2. Pousser les changements
git push origin feature/bridgepro

# 3. Publier depuis feature/bridgepro
npm login
npm publish
```

## Pourquoi merger dans master ?

✅ **Avantages** :
- Master reste la branche de référence stable
- Facilite la maintenance future
- Meilleure pratique Git
- Les autres développeurs savent où trouver la version publiée

⚠️ **Si vous publiez depuis feature/bridgepro** :
- La branche de développement devient la version publiée
- Peut créer de la confusion plus tard
- Moins standard mais fonctionnel

## Recommandation

**Je recommande l'Option 1** : merger dans master puis publier. Cela garde votre workflow propre et professionnel.

