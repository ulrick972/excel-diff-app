# diff.xlsx — Application de bureau

Application Windows pour comparer deux fichiers Excel (ancien vs nouveau) et visualiser les différences. Aucune donnée n'est envoyée sur internet : tout le traitement se fait localement sur l'ordinateur.

## Installer l'application (utilisateurs)

1. Va dans l'onglet **Actions** de ce repo GitHub
2. Clique sur le dernier run réussi (✅) du workflow **Build Windows App**
3. Dans la section **Artifacts** en bas de page, télécharge **diff-xlsx-setup**
4. Dézippe le fichier téléchargé, tu obtiens `diff.xlsx Setup x.x.x.exe`
5. Double-clique pour installer — **aucun droit administrateur requis**, l'application s'installe dans ton profil utilisateur (`%LOCALAPPDATA%`)
6. Une icône apparaît sur le Bureau et dans le menu Démarrer

## Mettre à jour l'application

Quand le code est modifié et repoussé sur la branche `main`, GitHub recompile automatiquement un nouveau `Setup.exe` (visible dans Actions → dernier run → Artifacts). Il suffit de le retélécharger et de relancer l'installeur ; il remplacera l'ancienne version.

## Développement

```bash
npm install
npm start          # lance l'app en mode développement
npm run dist       # compile l'installeur (nécessite Windows ou GitHub Actions)
```

Le cœur de l'application (`index.html`) est un outil web autonome qui fonctionne aussi seul dans un navigateur. Electron (`main.js`) l'encapsule dans une fenêtre native.

## Structure du projet

- `index.html` — l'application (interface + logique de comparaison)
- `xlsx.full.min.js` — librairie de lecture/écriture Excel (embarquée, fonctionne hors-ligne)
- `main.js` — point d'entrée Electron (création de la fenêtre)
- `preload.js` — script de préchargement (sécurité)
- `build/icon.ico` — icône de l'application
- `.github/workflows/build.yml` — compilation automatique du `Setup.exe`

## Licence

MIT
