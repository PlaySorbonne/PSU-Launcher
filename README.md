# PSU-Launcher
Le Launcher Minecraft de l'asso PlaySorbonne Université

## Téléchargement et utilisation
Pour télécharger le launcher [cliquez ici](launcher.playsorbonne.fr) 
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

### config VScode:
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
