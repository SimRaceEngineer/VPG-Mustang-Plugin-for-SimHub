# VPG Mustang GT3 plugin — modifications

## VPG Mustang GT3 plugin 0.1.1

- Photo du volant embarquée (`Resources/mustang.png`, vue de face) : la notice affiche les repères sur la vraie photo.

## VPG Mustang GT3 plugin 0.1.0 — nouveau plugin SimHub (dossier `VpgMustangPlugin/`)

- Décliné du plugin P1Sim Arnage pour le volant **VPG Sim Ford Mustang GT3** (pas d'écran, 3 rotatifs Elma 12 positions,
  76 LEDs RGB dont un anneau de 12 LEDs par rotatif).
- **3 rotatifs × 12 positions** (TC-LONG, TC-LAT, multifonction) : « momentary to latching » intégré (Apprendre / ✕),
  un label par position, roue des positions en direct.
- **Mode par rotatif** : *Rôles* (− / + déclenchent le rôle Control mapper de la position, comme l'Arnage — défaut du
  multifonction, labels MAP, 0, AC, EPAS, ALT, DIM, THR, F3, F2, F1, WIP, PAGE pré-remplis) ou *Pas à pas* (chaque cran
  tourné envoie une impulsion du rôle − ou +, sens inversable — défaut de TC-LONG / TC-LAT). Impulsions en file
  (`StartStopRole` 100 ms + 60 ms d'écart) : plusieurs crans = plusieurs appuis distincts.
- Boutons − / + bindables par rotatif + une paire « dernier rotatif tourné » (pour les funky switches).
- **Anneaux LED** : couleur par position, autres positions atténuées (%) ou éteintes, décalage de l'anneau ; propriétés
  `VPGMustang.<TcLong|TcLat|Multi>.Ring01..12` et script « Scripted content » à copier. Onglet LEDs hébergeant aussi
  les réglages LEDs SimHub de l'appareil (filtre « Mustang »).
- **Notice illustrée** : photo `Resources/mustang.png` (embarquée si présente) avec repères numérotés ; schéma dessiné sinon.
- Propriétés : `VPGMustang.<rotatif>.Position/.Label/.Color/.SlotNN.Label/.RingNN`, `VPGMustang.LastMoved.*`, `VPGMustang.LastAction.*`.
- UI en 9 langues. Exclu de `SimRaceEngineer.csproj`. Compilation vérifiée contre des stubs de l'API SimHub ; essai sur le volant à faire.
