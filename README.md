# PSU-Launcher
Le Launcher Minecraft de l'asso PlaySorbonne Université

## Téléchargement et utilisation
Pour télécharger le launcher [cliquez ici](https://github.com/PlaySorbonne/PSU-Launcher/releases/latest) 
- le .exe pour `windows`
- le .appimage pour `linux`
- le .dmg pour `macos`

## Compilation
### Pour lancer le launcher from source:
- telecharger la dernierre version de nodejs et npm
- telecharger les dernierre source disponible
- dans le repertoire ouvrez le terminal (ou cmd)
- faite `npm i`
- faite `npm start` (cela va compiler run le launcher sur les source)

### Pour compiler l'instalateur:
- au lieu de `npm start` faite `npm run dist`
- pour compiler sur une autre platform: `npm run dist:{win,linux,mac}` sans les accolade et avec seulement 1 d'entre eux attention le mac ne marchera pas sur linux et win et vice versa

### Config VScode:
Mettre cela dans `.vscode/launch.json`
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Main Process",
      "type": "node",
      "request": "launch",
      "cwd": "${workspaceFolder}",
      "program": "${workspaceFolder}/node_modules/electron/cli.js",
      "args" : ["."],
      "outputCapture": "std"
    },
    {
      "name": "Debug Renderer Process",
      "type": "chrome",
      "request": "launch",
      "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron",
      "windows": {
        "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/electron.cmd"
      },
      "runtimeArgs": [
        "${workspaceFolder}/.",
        "--remote-debugging-port=9222"
      ],
      "webRoot": "${workspaceFolder}"
    }
  ]
}
```
Puis faire ctrl F5 pour lancer

### Faire une release
Avant de push sur github vous devez:
- cree un draft release dans l'onglet release
- mettre un tag commencant par `v` et ayant 3 champ de chiffre : exemple `v0.9.0` pour une pre-release ajouter `-alpha.` avec un nombre apres le point a la fin exemple: `v0.0.1-alpha.1` et surtout faut cocher set as pre-release 
- nommez la version de manierre identique au tag
- faite votre changelog et cocher set as pre-release ou non suivant si alpha ou pas
- NE SURTOUT PAS CLIQUER SUR PUBLISH RELEASE
- cliquez sur `Save Draft`

Une fois la draft faite:
- sur votre projet changer la version de sorte qu'elle soit exactement identique a votre draft dans le fichier package.json et package-lock.json (attention dans ce dernier faut le changer a 2 endroit)
- faite votre git add commit et push
- allez a la page principal de votre projet github et attendez que la petite pastille orange devienne une coche verte
- retourner sur votre draft et rafraichissez la page
- verifier que vous avez bien le .exe .dmg et .appimage mais aussi les 3 .blockmap et les 3 .yml
- faite `Publish Release`

  Redemarer le launcher et attendez 10 sec et votre release sera trouver automatiquement
