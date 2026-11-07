# VPG Mustang GT3 plugin — modifications

## VPG Mustang GT3 plugin 1.0.0 — première version publique

Première release publique stable. Récapitulatif des fonctions :

- **3 rotatifs** : Multifonction (switch 12 positions), TC-LONG / TC-LAT en **Encodeur / Soft encoder / Soft multi**
  (sélecteur de fonction logiciel, pas ±1/±10, sortie rôles Control mapper ou boutons vJoy).
- **Anneaux LED** : surbrillance + clignotement de la position, luminosité / atténuation réglables, profil
  « VPG Mustang » fourni (joint à la release).
- **Onglet Advanced** : **palettes conditionnelles à la vitesse** (lecture directe des axes des palettes) ; option
  **axe vJoy embrayage qui se coupe au-dessus d'une vitesse** ; **brake magic** (tour de formation) déclenchable
  par bouton ou palette, slider bordeaux, sortie **axe vJoy** directe.
- **Volant live**, interface multilingue (9 langues), habillage bordeaux Porsche Motorsport.
- Prérequis (README + notes de release) : vJoy pour les sorties vJoy, Control mapper à configurer selon les besoins.

## VPG Mustang GT3 plugin 0.9.22 — brake magic : sortie axe vJoy directe (autonome)

- **Sortie axe vJoy dans le brake magic** : au lieu de mapper la propriété `BrakeMagic.Value` à la main, le plugin
  écrit le frein maintenu **directement sur un axe vJoy** (device Auto). Tu mappes juste le frein du jeu sur cet
  axe vJoy → autonome. Valeur affichée en live (device utilisé + vJoy OK). La propriété reste dispo au besoin.

## VPG Mustang GT3 plugin 0.9.21 — device vJoy automatique (plus autonome)

- **Device vJoy « Auto »** (par défaut) : le plugin **choisit tout seul** un device vJoy libre (en évitant ceux
  qu'une autre app possède) — plus besoin de choisir un numéro. Le device réellement utilisé est affiché en live
  (« vJoy OK #2 »), et s'il n'y a aucun device libre il le dit (« active-en un dans vJoyConf »).

## VPG Mustang GT3 plugin 0.9.20 — affichage live de la valeur vJoy (aide à vérifier)

- **Valeur de sortie vJoy affichée en direct** à côté de l'axe vJoy de chaque palette : on voit la valeur bouger
  avec la palette (sous le seuil) et tomber à 0 (au-dessus), + l'état **vJoy OK / non acquis**. Facile à vérifier.
- Rappel : **SimHub utilise déjà le vJoy device 1** — le plugin doit donc utiliser un **device vJoy différent**
  (device 2…), un seul feeder par device vJoy étant autorisé.

## VPG Mustang GT3 plugin 0.9.19 — palette → axe vJoy qui se coupe au-dessus du seuil

- **Sortie axe vJoy sur une palette conditionnelle** : la palette pilote un **axe vJoy** (X/Y/Z/RX/RY/RZ/SL0/SL1,
  device réglable) **sous la vitesse**, et le plugin **force cet axe à 0 au-dessus** → un axe embrayage
  « disparaît » au-dessus de la vitesse du tour de formation. Tu mappes l'embrayage du jeu sur cet axe vJoy.
  Chargé par réflexion (repli silencieux si vJoy absent).

## VPG Mustang GT3 plugin 0.9.18 — onglet LEDs réorganisé + disclaimer brake magic

- **Onglet LEDs rangé en 3 sections** (habitude SimHub) : **1 · Luminosité & clignotement** (dim, luminosité,
  surbrillance, clignotement du Multi), **2 · LEDs du volant** (page SimHub : préréglages boutons + LEDs
  individuelles → importer le profil « VPG Mustang »), **3 · Options des anneaux (avancé)** (offset, barre, filtre
  device, délai démarrage). Beaucoup moins de texte.
- **Note firmware** : l'anneau du Multi marche à fond ; sur TC-LONG/LAT les LEDs 11-12-1 sont pilotées ensemble →
  barre LED par position pas encore possible (maj firmware côté VPG).
- **Disclaimer brake magic** (orange) : prévu pour chauffer les freins au tour de formation, à utiliser avec
  précaution, à couper avant le départ et les zones de freinage.

## VPG Mustang GT3 plugin 0.9.17 — brake magic déclenchable directement par une palette (axe lu en direct)

- **Déclencheur du brake magic au choix** : **un bouton** (sélecteur SimHub) **ou directement la palette gauche /
  droite**. En mode palette, le plugin **lit l'axe directement** — plus besoin de transformer la palette en bouton
  dans le Control mapper (fini l'astuce « Axis X MinToMax → bouton simulé »). Tire la palette = bascule brake magic.

## VPG Mustang GT3 plugin 0.9.16 — sortie vJoy en option (rôles ou boutons vJoy)

- **Sortie vJoy optionnelle** : un champ de rôle − / + peut valoir **`vJoy:N`** (ou `vJoy:device:bouton`) → le
  plugin **presse un vrai bouton vJoy** au lieu d'un rôle Control mapper. Dispo dans la liste des rôles
  (`vJoy:1`…`vJoy:24`). Idéal pour les jeux qui ne lisent que des boutons (façon SOELPEC hardware).
- **Chargé par réflexion** : si vJoy n'est pas installé / device occupé, ça échoue en silence (repli sur les
  rôles, aucun crash). Aucune dépendance de compilation ajoutée.

## VPG Mustang GT3 plugin 0.9.15 — lisibilite : titres jaune Motorsport, % du brake magic lisible

- **Titres de section en jaune Motorsport + gras** (soulignés bordeaux) : « 1 · … », « 2 · … », et
  **TC-LONG / TC-LAT / Multi** — on voit tout de suite qu'il s'agit de fonctions différentes.
- **% du brake magic en blanc** (au lieu du bordeaux sombre, illisible sur fond noir).

## VPG Mustang GT3 plugin 0.9.14 — onglet Advanced clarifie + habillage bordeaux

- **Onglet Advanced plus clair** : 2 sections numérotées **« 1 · Palettes conditionnelles »** et
  **« 2 · Brake magic »** (mention « throttle hold » retirée, on ne l'a pas encore faite).
- **Trigger du brake magic derrière un bouton** : clic → ouvre le sélecteur d'input SimHub (appui court/long),
  au lieu de l'afficher en permanence (moins brouillon).
- **Habillage bordeaux Porsche Motorsport** : le **choix du mode encodeur** (Encoder / Soft encoder / Soft multi)
  est un sélecteur segmenté bordeaux ; le **slider du brake magic** est un slider bordeaux avec % (fini le bleu SimHub).

## VPG Mustang GT3 plugin 0.9.13 — correctif compilation du mode Soft encoder MULTI

- Corrige une erreur de compilation (CS0136 : variable `binds` en double) introduite en 0.9.12. Le mode
  **Soft encoder MULTI** compile et fonctionne.

## VPG Mustang GT3 plugin 0.9.12 — mode « Soft encoder MULTI » (sélecteur de fonction, inédit)

- **3ᵉ mode sur les encodeurs : « Soft encoder MULTI »**. L'encodeur devient un **sélecteur de fonction** : le
  tourner choisit la fonction (position 1, 2, 3 …), et les **boutons − / + bindables** règlent la fonction
  sélectionnée. Multifonction logiciel piloté par un encodeur — personne ne le fait.
- **Nombre de positions réglable** (2 / 3 / 4 / 6 / 12), **label + rôles − / + par position**, **pas ×10** optionnel.
  Sortie en **rôles Control mapper** : pas besoin de 12 bindings par fonction, juste + / − (le jeu compte).
- Boutons − / + **au choix** (sélecteur d'input SimHub), comme le Multi / le P1Sim.

## VPG Mustang GT3 plugin 0.9.11 — brake magic : bind direct dans l'onglet (popup SimHub)

- **Brake magic bindable directement dans l'onglet Advanced** via le **sélecteur d'input natif de SimHub**
  (le popup avec appui court / long). On choisit la palette gauche/droite **ou n'importe quel bouton** sans
  passer par Contrôles / Évènements. (Les actions `BrakeMagic.On` / `.Off` restent dispo pour un fonctionnement
  maintenu plutôt que bascule.)

## VPG Mustang GT3 plugin 0.9.10 — cadran TC tourne (12 en haut comme le volant)

- L'aperçu du **cadran TC Long / TC Lat** place maintenant **12 en haut (midi), puis 1 à 1 h**, comme le rotary
  physique (avant : 1 en haut). Le Multi garde sa position « 0 » en haut.

## VPG Mustang GT3 plugin 0.9.9 — numeros des TC alignes sur le cadran (12 en haut)

- Les cadrans **TC Long / TC Lat** du VPG sont numerotes **12 en haut (midi), puis 1, 2…** : le decalage de
  position passe a **−1 par defaut** sur les deux TC pour que le numero affiche colle au volant (ta position en
  haut = 12). Reglable dans l'onglet Encodeurs (« Décalage de position ») si besoin.
- Texte du reset du soft encoder mis a jour : on realigne sur **le haut (12)**.

## VPG Mustang GT3 plugin 0.9.8 — delai de demarrage a 0 par defaut

- Le rebranchement du volant au demarrage de SimHub s'est avere **independant du plugin** (il arrive meme plugin
  desactive) : c'est un comportement USB/Windows. Le **« Délai au démarrage » repasse donc a 0 par defaut** (il
  reste reglable si besoin). A corriger cote Windows : gestion d'alimentation USB, demarrage rapide, port USB.

## VPG Mustang GT3 plugin 0.9.7 — axes des palettes preregles par defaut (plus de menu)

- **Axes des palettes préréglés** pour le VPG Mustang : gauche = `JoystickPlugin.Mustang_GT3_by_VPG_Y`,
  droite = `JoystickPlugin.Mustang_GT3_by_VPG_X`. Appliqué automatiquement quand aucun axe n'est défini.
- **Menu de sélection d'axe retiré** de l'onglet Advanced : on garde juste la **valeur live** par palette. Le
  seuil, le sens, la vitesse et le rôle restent réglables.

## VPG Mustang GT3 plugin 0.9.6 — palettes conditionnelles lues en AXE (les palettes du haut sont des axes)

- **Correction de fond** : les palettes du haut du VPG sont des **axes** (croix X/Y), pas des boutons. Le plugin
  les **lit maintenant directement comme un axe** — plus besoin de binder quoi que ce soit.
- Par palette : **choix de l'axe** (bouton « … » = liste des propriétés, ex. `JoystickPlugin.Mustang_GT3_by_VPG_X`/`_Y`),
  **valeur live en %** + **voyant** qui s'allume quand le plugin voit la palette tirée, **seuil de tir** (% de course)
  et **sens inversé**. Au-dessus de la vitesse, tirer la palette déclenche le rôle choisi ; en dessous, rien.
- Le voyant fonctionne **même sans jeu lancé** (lu par le timer interne).

## VPG Mustang GT3 plugin 0.9.5 — detection du volant au demarrage (temporisation)

- **Fix : le volant devait etre rebranche a chaque redemarrage de SimHub.** Le plugin accrochait les entrees
  immediatement dans Init, ce qui pouvait court-circuiter l'enumeration du VPG par SimHub. Il attend desormais
  **quelques secondes** (defaut 3 s) avant de hooker les entrees et de demarrer ses timers, le temps que SimHub
  detecte le volant. Delai reglable (onglet LEDs RGB, « Délai au démarrage »).

## VPG Mustang GT3 plugin 0.9.4 — brake magic (tour de formation)

- **Brake magic** : maintient un petit % de frein pendant le tour de formation. Action bindable
  `BrakeMagic.Toggle` (+ `.On` / `.Off`), **slider bordeaux + %** reglable (0–30 %, defaut 12 %, viser < 15 %),
  **vitesse max** reglable (defaut 80 km/h) au-dela de laquelle ca se **relache tout seul**. Le plugin expose
  `MustangPlugin.VPGMustang.BrakeMagic.Value` (0–100) a mapper sur l'axe frein (option sans dependance, via le
  Control mapper) et `.Active` (0/1). Throttle hold / double-input embrayage : a suivre.

## VPG Mustang GT3 plugin 0.9.3 — voyant lumineux par palette (gauche/droite)

- **Voyant lumineux** à côté de chaque palette (gauche jaune / droite bleu) : il s'allume quand la palette est
  actionnée, pour confirmer visuellement qu'on commande la bonne. Nouvelles proprietes `Context.1` / `Context.2`
  (utilisables aussi dans un dashboard ou un profil LED).

## VPG Mustang GT3 plugin 0.9.2 — soft encoder double sens + decalage, palettes gauche/droite reperees

- **Soft encoder : les deux sens marchent toujours** (l'encodeur boucle 12↔1 dans les deux directions). Fini le
  blocage au point haut et le decalage qui obligeait a reset. L'ancienne case « Boucler » est retiree (toujours actif).
- **Decalage de position** reglable (ex. −1) pour aligner le numero affiche avec le volant (ta position 1 = position 1).
- **Palettes conditionnelles — version simple** : seulement **2 lignes, GAUCHE (jaune) et DROITE (bleu)**, avec des
  **reperes de couleur traces sur la photo du dos du volant** pour viser la bonne palette. Chaque palette :
  au-dessus du seuil → devient l'input choisi (ex. « TC off »). Une ligne peut rester vide (ex. si tu gardes la
  palette droite pour le brake magic). Bind sur ContextPaddle.1 (gauche) / .2 (droite).

## VPG Mustang GT3 plugin 0.9.1 — onglet Advanced simplifie + photo VPG, section brake magic/throttle hold

- **Palettes conditionnelles simplifiees** : on ne configure plus que ce que la palette **devient au-dessus** du
  seuil (en dessous, rien ne change — la palette reste l'axe mappe dans le Control mapper). Choix de l'input via
  le menu deroulant. Photo du **dos du volant VPG** ajoutee pour illustrer les palettes du haut.
- **Nouvelle section « Brake magic & throttle hold (tour de formation) »** dans l'onglet Advanced (placeholder,
  implementation a suivre : palette embrayage en double input + palette pilotant un axe frein/gaz).

## VPG Mustang GT3 plugin 0.9.0 — 4 onglets (habillage bordeaux Porsche), onglet Advanced (palettes conditionnelles)

- **Interface en 4 onglets** : **Multifonction** (le rotatif 12 positions + volant live + guide), **Encodeurs**
  (TC-LONG / TC-LAT), **Advanced**, **LEDs RGB**. Onglets habilles en **rouge bordeaux Porsche Motorsport**
  (bande de tete + onglet actif), a la place du SHTabControl bleu de SimHub.
- **Onglet Advanced — palettes conditionnelles a la vitesse** (tout dans SimHub) : 4 actions bindables
  `ContextPaddle.1…4`. Bind une palette/bouton sur l'action dans le Control mapper, choisis le role declenche
  **en dessous** et **au-dessus** d'un seuil de vitesse (ex. < 30 km/h = limiteur, au-dessus = overtake). Le role
  peut etre un role Control mapper ou une commande du plugin (ex. `ResetSoftEncoder.TcLat`). Propriete de vitesse
  choisissable (bouton « … » = liste complete des proprietes SimHub).

## VPG Mustang GT3 plugin 0.8.9 — reset soft encoder utilisable comme role d'une position

- **Reset du soft encoder depuis un role de position** : on peut mettre `ResetSoftEncoder.TcLong` ou
  `ResetSoftEncoder.TcLat` dans le champ « Role sur − / + » d'une position (ex. une position « RST » du Multi).
  Le plugin reconnait ces commandes et execute le reset directement, au lieu de les envoyer au Control mapper
  (qui n'a pas ce role). Les deux commandes apparaissent aussi dans la liste deroulante des roles. `ResetSoftEncoder`
  seul reinitialise les deux TC. (Les actions bindables dans Controles / Evenements de 0.8.8 restent valables.)

## VPG Mustang GT3 plugin 0.8.8 — reset soft encoder bindable, Multi en mode position (anti-piege clignotement)

- **Reset du soft encoder bindable sur un bouton** : nouvelles actions SimHub `ResetSoftEncoder.TcLong` et
  `ResetSoftEncoder.TcLat` (Contrôles / Évènements). On peut realigner le soft encoder en jeu sans ouvrir SimHub :
  ramener la valeur du jeu au mini, tourner le rotary sur 1, appuyer sur le bouton bind.
- **Rotatif multifonction toujours en mode position** : l'option « Barre LED » est retiree pour le Multi (un
  selecteur 12 positions n'a pas de barre). Evite le piege ou le Multi, laisse en mode barre, n'affichait plus la
  surbrillance / le clignotement de la position. Les deux TC gardent la barre LED.

## VPG Mustang GT3 plugin 0.8.7 — position active clignotante, luminosite/surbrillance reglables, selecteur de propriete

- **Position active clignotante** (couleur <-> blanc) pour la retrouver dans le noir — comme avant. Activable
  dans l'onglet LEDs RGB (actif par defaut).
- **Luminosite rotary 0-500 %** (gain global) et **surbrillance de la position active 50-100 %** reglables
  a cote du menu d'attenuation. >100 % booste les couleurs sombres (plafonne au max par canal).
- **Attenuation** : choix etendu jusqu'a 100 %.
- **Selecteur de propriete** pour la barre LED : bouton « … » qui liste **toutes les proprietes SimHub
  disponibles avec un filtre par nom** (certains jeux n'exposent pas les memes). Si la liste est vide (jeu non
  lance), on peut toujours taper le nom. La liste est trouvee par reflexion -> robuste selon la version de SimHub.

## VPG Mustang GT3 plugin 0.8.6 — selecteur de couleur integre, profil LED fourni, aide soft encoder

- **Selecteur de couleur integre** (palette + hex visible, fond sombre facon SimHub) au lieu de la boite
  Windows : apercu, palette rapide (rouge VPG, couleurs des positions), hex toujours lisible, et la roue
  Windows complete reste accessible via un bouton. Clic sur la pastille de couleur de chaque position.
- **Plus de scripts a copier** dans l'onglet LEDs RGB : le profil LED « VPG Mustang » fourni allume les
  anneaux tout seul (a importer dans les reglages LEDs RGB du volant). Les couleurs restent reglables par position.
- **Aide du soft encoder** reformulee : elle n'explique plus la methode interne, seulement « reset puis
  boutons − / + » (9 langues).

## VPG Mustang GT3 plugin 0.8.5 — attenuation defaut 50 %, propriete barre en liste

- Attenuation des positions inactives par defaut a **50 %** (l'active a 100 % ressort, les autres restent visibles).
- La propriete de la barre LED se choisit dans une **liste** (TCLevel, ABSLevel, EngineMap, BrakeBias...) ou en texte libre.

## VPG Mustang GT3 plugin 0.8.4 — attenuation par defaut plus visible

- Defaut de l'attenuation des positions inactives porte de 15 % a 35 % (les anneaux paraissaient presque eteints).
  Reglable dans l'onglet LEDs RGB.

## VPG Mustang GT3 plugin 0.8.3 — nom de propriete corrige (prefixe de classe SimHub)

- SimHub prefixe les proprietes avec le nom de classe : le vrai nom est `MustangPlugin.VPGMustang.<rotatif>.RingNN`
  (idem Press, etc.). Le script d'anneau et les aides utilisent desormais ce nom complet → les anneaux lisent bien
  les couleurs du plugin. Textes d'aide (noms de proprietes) mis a jour.

## VPG Mustang GT3 plugin 0.8.2 — script d'anneau defensif (plus de FormatException)

- Le script « scripted content » des anneaux valide chaque couleur (#RRGGBB / #AARRGGBB) et ignore toute valeur
  invalide au lieu de faire planter l'effet (`System.FormatException: Token is not valid`).

## VPG Mustang GT3 plugin 0.8.1 — couleurs VPG (rouge/gris), textes corriges

- Palette **VPG / Porsche** : accent **rouge** sur fond sombre (fini le bleu et le lime). Bouton reset en rouge.
- Textes du soft encoder **raccourcis et clarifies** ; correction d'un melange FR/EN dans l'aide du reset.
- Presentation un peu aeree.

## VPG Mustang GT3 plugin 0.8.0 — reset soft encoder + anti-diaphonie

- **Bouton « Soft encoder reset »** (lime) dans la section soft encoder : remet la position virtuelle sur 1. A faire
  a chaque demarrage de SimHub si l'encodeur n'est pas sur sa position de reference (un encodeur est relatif).
- **Anti-diaphonie** : apprendre une entree pour un encodeur l'efface automatiquement des autres (fini les deux TC
  qui bougeaient ensemble). Ré-apprendre les entrees + / − de chaque TC.

## VPG Mustang GT3 plugin 0.7.2 — multi en Switch uniquement, avertissement soft encoder

- Le rotatif **multifonction** ne propose plus que **Switch (positions)** (les modes encodeur n'ont pas de sens pour
  un switch 12 positions). Les TC ne proposent que **Encodeur** / **Soft encoder**.
- **Avertissement soft encoder** : un encodeur est relatif, le plugin ne peut pas connaître la vraie position au
  démarrage de SimHub (dérive possible). Pour un affichage fiable, préférer la **barre LED depuis la valeur du jeu**.

## VPG Mustang GT3 plugin 0.7.1 — propriete barre TC par defaut

- La barre LED des TC est pre-remplie avec `DataCorePlugin.GameData.TCLevel` (valeur barre pleine 11) ; a adapter
  selon le sim via la liste des proprietes SimHub.

## VPG Mustang GT3 plugin 0.7.0 — barre LED depuis une valeur du jeu (type BavarianSimTec)

- **Anneau en barre** (option par rotatif, onglet LEDs) : au lieu d'afficher la position sélectionnée, l'anneau
  allume les LED 1..N dans leurs couleurs de position, N venant d'une **propriété SimHub bindable** (ex. ton plugin
  simrace) avec sa valeur lue en jeu, et une valeur « barre pleine ». Mise a jour en direct (DataUpdate).
- Les couleurs par position (ex. 1-6 jaune, 7-12 bleu) se reglent dans l'onglet Rotatifs ; le mode Encodeur simple
  expose aussi ces 12 couleurs pour la barre.

## VPG Mustang GT3 plugin 0.6.0 — 3 modes : Switch / Encodeur / Soft encoder

- Trois modes par rotatif : **Switch (positions)** (switch matériel 12 positions), **Encodeur** (le jeu gère − / + ;
  label pour dashboards — défaut des TC), et **Soft encoder** (option avancée, **pas par défaut**) : le plugin compte
  une **position virtuelle** depuis les deux entrées − / + apprises, avec label + couleur + anneau LED par position
  (comme un plugin « mode switch »).
- Soft encoder : apprentissage des entrées + / −, option boucler 12→1, roue et anneau suivent la position comptée.

## VPG Mustang GT3 plugin 0.5.0 — mode Encodeur simplifie, retrait du paragraphe LED d'appui

- **Mode Encodeur simplifie** : plus de roles − / + ni de boutons − / + a binder (un encodeur envoie deja − / + au jeu
  lui-meme). Il ne reste qu'un **label** (ex. « TC LAT », « ABS »), publie en `VPGMustang.<rotatif>.Name` pour les dashboards.
- **Retrait** de la section « Faire clignoter le LED du bouton » de l'interface : le clignotement se met directement
  dans le profil LED (effets CustomStatus, comme TC PLUS / TC MINUS).

## VPG Mustang GT3 plugin 0.4.1 — modes renommes « Encodeur » / « Switch (positions) »

- Vocabulaire clarifie : « Pas a pas » devient **Encodeur** (tourner envoie − / +), « Roles » devient
  **Switch (positions)** (chaque position a un label et son role − / +). Intro reecrite en consequence.

## VPG Mustang GT3 plugin 0.4.0 — couleurs par position sur la 1re page, palette Windows

- **Choix des couleurs directement dans le tableau de chaque rotatif** (onglet Rotatifs) : une pastille de couleur
  par position, comme une legende, a cote du label.
- **Clic = palette de couleurs Windows** (`ColorDialog`, comme le plugin Asetek) — plus besoin de taper du code hex.
- L'onglet LEDs RGB ne gere plus que le decalage d'anneau, l'attenuation, le script a copier et les reglages LEDs
  SimHub de l'appareil ; l'edition des couleurs y a ete retiree (renvoi vers l'onglet Rotatifs).

## VPG Mustang GT3 plugin 0.3.1 — version visible, temoin d'appui, LED bouton, nettoyage

- Numero de version affiche en haut de la page du plugin.
- **LED du bouton + / −** : proprietes `VPGMustang.Press.Minus` / `.Plus` qui clignotent ~450 ms a l'appui, section
  dediee avec le script Scripted content a coller, et un **temoin en direct** (deux points − / +) pour verifier
  que le plugin reagit sans attendre le cablage LED.
- **Retrait** de la fonction « − / + sur le dernier rotatif tourne » (peu claire, redondante).
- Volant en direct : axe sous `JoystickPlugin.VNM_Direct_Drive_X`, affichage simplifie (retrait du `raw`).
  (0.2.3 / 0.2.4 / 0.3.0 : lecture de l'axe, retrait du -/+ partage, clignotement initial.)

## VPG Mustang GT3 plugin 0.2.2 — volant suit l'axe physique de la base

- Le volant en direct suit l'**axe brut de la base** via une propriété SimHub réglable (défaut `VNM_Direct_Drive_X`) :
  il tourne **même sans jeu**. Repli télémétrie si vide ; valeur brute affichée pour repérer le bon axe.

## VPG Mustang GT3 plugin 0.2.1 — rotatif central en premier + clarifications

- **Rotatif multifonction affiché en premier** (le plus utile en mode « encoder remap »), avant TC-LONG et TC-LAT.
- **Mode Pas à pas** : note « dépend du jeu » (fonctionne là où le sim expose un contrôle +/- pour ça, ex. ACC ;
  pas dans Le Mans Ultimate).
- **Boutons − / + partagés** : explication revue avec exemple (une seule paire agissant sur le dernier rotatif tourné).

## VPG Mustang GT3 plugin 0.2.0 — volant animé

- **Volant en direct** (onglet Rotatifs) : la photo du volant tourne selon l'angle de braquage lu dans SimHub,
  angle total réglable (défaut 540°).

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
