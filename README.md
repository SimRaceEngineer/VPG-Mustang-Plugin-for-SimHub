# VPG Mustang GT3 — plugin SimHub

Plugin SimHub (C# .NET Framework 4.8) pour le volant **VPG Sim Ford Mustang GT3**. Décliné du plugin P1Sim Arnage.

Le volant n'a pas d'écran. Il a trois rotatifs Elma 12 positions, chacun avec un anneau de 12 LEDs RGB, deux funky switches 7 directions et des boutons.

| Rotatif | Rôle par défaut |
|---|---|
| **TC-LONG** (bleu) | mode *Pas à pas* : chaque cran envoie `TractionControl Slip+` / `TractionControl Slip-` |
| **TC-LAT** (blanc) | mode *Pas à pas* : chaque cran envoie `TractionControl Cut+` / `TractionControl Cut-` |
| **Multifonction** (bas) | mode *Rôles* : MAP, 0, AC, EPAS, ALT, DIM, THR, F3, F2, F1, WIP, PAGE. Les boutons − / + déclenchent le rôle de la position choisie. |

Tous ces réglages sont modifiables dans la page du plugin.

## Prérequis (à lire avant utilisation)

- **SimHub** — le plugin tourne dedans.
- **vJoy doit être installé** si tu utilises les sorties **axe vJoy** (embrayage qui se coupe au-dessus d'une vitesse, brake magic en sortie vJoy, rôles `vJoy:N` du Soft multi). Active **au moins un device vJoy libre** dans *vJoyConf* — celui que SimHub occupe déjà ne compte pas (un seul feeder par device). Sans vJoy, ces fonctions sont simplement **inactives** ; **tout le reste du plugin marche sans vJoy**.
- **Control mapper SimHub à configurer selon tes besoins** : les rôles − / + (TC, ABS, MAP, TCS, embrayage, frein…) doivent être **liés au jeu, selon l'usage de chacun**, comme n'importe quel mapping SimHub. Le plugin **déclenche** les rôles / presse les boutons / pilote les axes ; c'est à **toi** de décider à quoi ils correspondent dans **ton** jeu (et de mapper tes axes vJoy côté jeu). C'est ce qui rend le plugin universel.

## Installation

1. Télécharger `VpgMustangPlugin.dll` depuis la [dernière release](../../releases/latest).
2. Fermer SimHub.
3. Copier `VpgMustangPlugin.dll` dans `C:\Program Files (x86)\SimHub2\SimHub`, à côté de `SimHub.Plugins.dll`.
4. Relancer SimHub, activer **VPG Mustang GT3**, cocher *Afficher dans le menu de gauche*.

## Mise en route

1. **Onglet Rotatifs**, pour chaque rotatif : cliquer sur **Apprendre** sur une ligne, puis tourner le rotatif sur cette position. Recommencer pour les 12 positions. Le bouton ✕ annule l'apprentissage ou efface l'entrée apprise.
2. **Mode du rotatif :**
   - *Pas à pas* : choisir le rôle envoyé en tournant vers la gauche (−) et vers la droite (+). La case *Inverser le sens* corrige un rotatif câblé à l'envers.
   - *Rôles* : pour chaque position, choisir le rôle Control mapper déclenché par − et par +.
3. **Boutons − / + :** associer les funky switches (haut / bas) avec la fenêtre de bind SimHub. Deux possibilités :
   - sur le rotatif multifonction ;
   - sur la paire *− / + sur le dernier rotatif tourné*.

   Choisir des entrées qui n'ont pas de rôle direct dans le Control mapper.
4. Les rôles doivent être liés dans le jeu comme d'habitude. Le plugin les déclenche par impulsions de 100 ms, sans jamais laisser de rôle bloqué enfoncé.

## Anneaux LED

Pour chaque rotatif, le plugin publie `VPGMustang.<TcLong|TcLat|Multi>.Ring01` à `Ring12` :

- la position choisie s'affiche dans sa couleur ;
- les autres positions sont atténuées (pourcentage réglable) ou éteintes.

Pour brancher un anneau :

1. Dans le profil LEDs du volant (onglet **LEDs RGB** du plugin, ou Devices → LEDs), ajouter un effet **Scripted content** de 12 LEDs sur l'anneau.
2. Coller le script fourni par le bouton *Copier le script*.
3. Si la LED allumée n'est pas en face de la bonne position, corriger avec le réglage *LED de la position 1*.

## Propriétés pour les dashboards

- `VPGMustang.<rotatif>.Position` (1-12), `.Label`, `.Color`, `.SlotNN.Label`, `.RingNN`
- `VPGMustang.LastMoved.Switch`, `.Label`, `.Position`
- `VPGMustang.LastAction.Role`, `.Label`

## Fichiers

- Réglages : `%APPDATA%\VpgMustangPlugin\settings.json`
- Journal : `%APPDATA%\VpgMustangPlugin\log.txt`
