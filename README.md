
**Table des matières**
- Présentation
  - Fonctionalitées
  - Decodeur TV UHD
- Installation
  - Liste des modifications à faire
  - 1. Trouver le décodeur TV sur le LAN
  - 2. Modifier dans le fichier configuration.yaml
  - 3. Créer un fichier yaml contenant les commandes pour le décodeur.
  - 4. Rajouter une ou plusieurs cartes dans l'interface lovelace
      -  Télécommande simple
      -  Liste des chaines simple
      -  Télécommande nécessitant button-card


# Présentation
### Fonctionalitées

- Permet de piloter son décodeur **TV HD Orange** à partir de Home Assistant

### Decodeur TV UHD
Le **décodeur TV UHD** est fourni par Orange dans le cadre d&apos;une souscription à un abonnement Internet "grand public". C&apos;est un boitier séparé de la **Livebox**.
Dans ma configuration, on a un **Home Assistant **qui tourne sur un Raspberry sur le même LAN que le décodeur TV.
La communication se fait sur le port 8080 car on est sur le même LAN.
Pour une utilisation hors du LAN, il faut utiliser le port [8085](https://tv-orange.pourqui.com/site.html "8085").  

# Installation

### Liste des modifications à faire

1. Trouver le décodeur TV sur le LAN
2. Modifier dans le fichier *configuration.yaml*  
3. Créer un fichier yaml contenant les commandes pour le décodeur
4. Rajouter une ou plusieurs cartes dans l&apos;interface lovelace

### 1. Trouver le décodeur TV sur le LAN
Voila comment j&apos;ai trouvé le nom du décodeur sur le LAN.
Mon script utilise le nom du decodeur fourni par le DNS de la Livebox.
J&apos;ai découvert le nom "***pcmltvwhd94.home***" avec le logiciel "[Advanced IP Scanner](https://www.advanced-ip-scanner.com/fr/ "Advanced IP Scanner")"  .  
Sur ma **Livebox 3**, on peut trouver l&apos;adresse IP dans le menu de la Livebox.
Menu du haut "*Configuration Avancée*", bandeau de gauche "*Configuration réseau*" 
menu "*UPnP*", pour ma part, "adresse IP hote" est à 192.168.1.58.
En cas de doute sur le fait que votre décodeur est identique, vous  pouvez faire un "***ping pcmltvwhd94.home***" dans une ligne de commande.
Si vous nommer un équipement connecté en "*MonEquipement*" dans l&apos;interface de la livebox, vous pouvez l&apos;atteindre par le nom "*MonEquipement.home*"

### 2. Modifier dans le fichier *configuration.yaml*  

    # fichier des commandes pour le Decodeur TH  HD Orange
	rest_command: !include rest_command.yaml

### 3. Créer un fichier yaml contenant les commandes pour le décodeur.
Créer un fichier nommé "*rest_command.yaml*" dans le répertoire par défault "*config/*" avec "*File Editor*"

	# Pilotage du décodeur TV Orange    
	tv_off:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=116&mode=00'
	tv_up:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=103&mode=00'
	tv_vod:
	  url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=393&mode=00'
	tv_gauche:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=105&mode=00'
	tv_ok:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=352&mode=00'
	tv_droite:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=106&mode=00'
	tv_back:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=158&mode=00'
	tv_down:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=108&mode=00'
	tv_menu:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=139&mode=00'
	tv_volume_plus:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=115&mode=00'
	tv_volume_mute:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=113&mode=00'
	tv_volume_moins:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=114&mode=00'
	tv_programme_plus:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=402&mode=00'
	tv_pause:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=164&mode=00'
	tv_programme_moins:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=403&mode=00'
	tv_rewind:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=168&mode=00'
	tv_fastforward:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=159&mode=00'
	tv_record:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=01&key=167&mode=00'    
	tv_one_more_think:    
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=10' 
	tv_tf1:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******192&uui=1'
	tv_france_2:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*********4&uui=1'
	tv_france_3:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********80&uui=1'
	tv_canal_plus:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********34&uui=1'    
	tv_france_5:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********47&uui=1'    
	tv_m6:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******118&uui=1'    
	tv_arte:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******111&uui=1'    
	tv_c8:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******445&uui=1'    
	tv_w9:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******119&uui=1'    
	tv_tmc:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******195&uui=1'    
	tv_tfx:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******446&uui=1'    
	tv_nrj12:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******444&uui=1'    
	tv_lcp:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******234&uui=1'    
	tv_france_4:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********78&uui=1'    
	tv_bfm:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******481&uui=1'    
	tv_cnews:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******226&uui=1'    
	tv_cstar:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******458&uui=1'    
	tv_gulli:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******482&uui=1'    
	tv_france_o:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******160&uui=1'    
	tv_tf1_series:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******1404&uui=1'    
	tv_equipe:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******1401&uui=1'    
	tv_6ter:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******1403&uui=1'    
	tv_rmc_decouverte:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******1400&uui=1'    
	tv_cherie_25:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******1399&uui=1'    
	tv_lci:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******112&uui=1'    
	tv_france_info:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=******2111&uui=1'    
	    
	tv_bbc_world:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********19&uui=1'    
	tv_deutsche_well:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=********61&uui=1'    
	tv_france_3_bretagne:
	    url: 'http://pcmltvwhd94.home:8080/remoteControl/cmd?operation=09&epg_id=*******634&uui=1'

### 4. Rajouter une ou plusieurs cartes dans l&apos;interface lovelace 

Voila quelques exemples de cartes à rajouter dans l&apos;interface lovelace.
Le plus simple est de ce mettre sur une vue, de passer en mode modication (bouton en haut à droite ":"), rajouter  une carte en clickant sur le bouton "+" en bas à droite et de choisir une carte "Manuel".
On peut alors faire une copie du texte fourni ici à la palce de " *type: ''* ".

#### Télécommande simple
	cards:
	  - cards:
	      - icon: 'mdi:power-standby'
	        name: 'Off'
	        tap_action:
	          action: call-service
	          service: rest_command.tv_off
	        type: button
	      - icon: 'mdi:arrow-up-bold-outline'
	        name: Haut
	        tap_action:
	          action: call-service
	          service: rest_command.tv_up
	        type: button
	      - icon: 'mdi:video-vintage'
	        name: VOD
	        tap_action:
	          action: call-service
	          service: rest_command.tv_vod
	        type: button
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:arrow-left-bold-outline'
	        name: Gauche
	        tap_action:
	          action: call-service
	          service: rest_command.tv_gauche
	        type: button
	      - icon: 'mdi:stop'
	        name: Ok
	        tap_action:
	          action: call-service
	          service: rest_command.tv_ok
	        type: button
	      - icon: 'mdi:arrow-right-bold-outline'
	        name: Droite
	        tap_action:
	          action: call-service
	          service: rest_command.tv_droite
	        type: button
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:undo-variant'
	        name: Retour
	        tap_action:
	          action: call-service
	          service: rest_command.tv_back
	        type: button
	      - icon: 'mdi:arrow-down-bold-outline'
	        name: Bas
	        tap_action:
	          action: call-service
	          service: rest_command.tv_down
	        type: button
	      - icon: 'mdi:monitor-dashboard'
	        name: Menu
	        tap_action:
	          action: call-service
	          service: rest_command.tv_menu
	        type: button
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-plus'
	        name: Vol Plus
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_plus
	        type: button
	      - icon: 'mdi:arrow-up-bold-outline'
	        name: Prog+
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_programme_plus
	        type: button
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-mute'
	        name: Mute
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_mute
	        type: button
	      - icon: 'mdi:play-pause'
	        name: Pause
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_pause
	        type: button
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-minus'
	        name: Vol-
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_moins
	        type: button
	      - icon: 'mdi:arrow-down-bold-outline'
	        name: Prog-
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_programme_moins
	        type: button
	    type: horizontal-stack
	  - cards:
	      - cards:
	          - icon: 'mdi:numeric-1-box-outline'
	            name: TF1
	            tap_action:
	              action: call-service
	              service: rest_command.tv_tf1
	            type: button
	          - icon: 'mdi:numeric-2-box-outline'
	            name: France 2
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_2
	            type: button
	          - icon: 'mdi:numeric-3-box-outline'
	            name: France 3
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_3
	            type: button
	        type: horizontal-stack
	      - cards:
	          - icon: 'mdi:numeric-4-box-outline'
	            name: Canal+
	            tap_action:
	              action: call-service
	              service: rest_command.tv_canal_plus
	            type: button
	          - icon: 'mdi:numeric-5-box-outline'
	            name: France 5
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_5
	            type: button
	          - icon: 'mdi:numeric-6-box-outline'
	            name: M6
	            tap_action:
	              action: call-service
	              service: rest_command.tv_m6
	            type: button
	        type: horizontal-stack
	      - cards:
	          - icon: 'mdi:numeric-7-box-outline'
	            name: Arte
	            tap_action:
	              action: call-service
	              service: rest_command.tv_arte
	            type: button
	          - icon: 'mdi:numeric-8-box-outline'
	            name: C8
	            tap_action:
	              action: call-service
	              service: rest_command.tv_c8
	            type: button
	          - icon: 'mdi:numeric-9-box-outline'
	            name: W9
	            tap_action:
	              action: call-service
	              service: rest_command.tv_w9
	            type: button
	        type: horizontal-stack
	    type: vertical-stack
	  - cards:
	      - icon: 'mdi:rewind'
	        name: Rewind
	        tap_action:
	          action: call-service
	          service: rest_command.tv_rewind
	        type: button
	      - icon: 'mdi:pause'
	        name: Pause
	        tap_action:
	          action: call-service
	          service: rest_command.tv_pause
	        type: button
	      - icon: 'mdi:fast-forward'
	        name: Fastforward
	        tap_action:
	          action: call-service
	          service: rest_command.tv_fastforward
	        type: button
	      - icon: 'mdi:record-rec'
	        name: Record
	        tap_action:
	          action: call-service
	          service: rest_command.tv_record
	        type: button
	    type: horizontal-stack
	type: vertical-stack

####Liste des chaines simple

	cards:
	  - cards:
	      - hold_action:
	          action: none
	        name: TF1
	        tap_action:
	          action: call-service
	          service: rest_command.tv_tf1
	        type: button
	      - name: France 2
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_2
	        type: button
	      - name: France 3
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_3
	        type: button
	      - name: Canal +
	        tap_action:
	          action: call-service
	          service: rest_command.tv_canal_plus
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: France 5
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_5
	        type: button
	      - name: M6
	        tap_action:
	          action: call-service
	          service: rest_command.tv_m6
	        type: button
	      - type: button
	        name: Arte
	        tap_action:
	          action: call-service
	          service: rest_command.tv_arte
	      - name: C8
	        tap_action:
	          action: call-service
	          service: rest_command.tv_c8
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: W9
	        tap_action:
	          action: call-service
	          service: rest_command.tv_w9
	        type: button
	      - name: TMC
	        tap_action:
	          action: call-service
	          service: rest_command.tv_tmc
	        type: button
	      - name: TFX
	        tap_action:
	          action: call-service
	          service: rest_command.tv_tfx
	        type: button
	      - name: NRJ12
	        tap_action:
	          action: call-service
	          service: rest_command.tv_nrj12
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: LCP
	        tap_action:
	          action: call-service
	          service: rest_command.tv_lcp
	        type: button
	      - name: France 4
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_4
	        type: button
	      - name: BFM TV
	        tap_action:
	          action: call-service
	          service: rest_command.tv_bfm
	        type: button
	      - name: CNews
	        tap_action:
	          action: call-service
	          service: rest_command.tv_cnews
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: CStar
	        tap_action:
	          action: call-service
	          service: rest_command.tv_cstar
	        type: button
	      - name: Gulli
	        tap_action:
	          action: call-service
	          service: rest_command.tv_gulli
	        type: button
	      - name: France O
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_o
	        type: button
	      - name: TF1 Series
	        tap_action:
	          action: call-service
	          service: rest_command.tv_tf1_series
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: L'équipe
	        tap_action:
	          action: call-service
	          service: rest_command.tv_equipe
	        type: button
	      - name: 6TER
	        tap_action:
	          action: call-service
	          service: rest_command.tv_6ter
	        type: button
	      - name: RMC Découverte
	        tap_action:
	          action: call-service
	          service: rest_command.tv_rmc_decouverte
	        type: button
	      - name: Chérie 25
	        tap_action:
	          action: call-service
	          service: rest_command.tv_cherie_25
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: LCI
	        tap_action:
	          action: call-service
	          service: rest_command.tv_lci
	        type: button
	      - name: France Info
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_info
	        type: button
	      - name: FR3 Bretagne
	        tap_action:
	          action: call-service
	          service: rest_command.tv_france_3_bretagne
	        type: button
	    type: horizontal-stack
	  - cards:
	      - name: BBC World
	        tap_action:
	          action: call-service
	          service: rest_command.tv_bbc_world
	        type: button
	      - name: Deutsche Welle
	        tap_action:
	          action: call-service
	          service: rest_command.tv_deutsche_well
	        type: button
	    type: horizontal-stack
	type: vertical-stack

#### Télécommande nécessitant button-card
pour utiliser cette carte, il faut préalablement charger la custom card [button-card](https://github.com/custom-cards/button-card "button-card") dans [HACS](https://github.com/hacs/integration "HACS").

	cards:
	  - cards:
	      - icon: 'mdi:power-standby'
	        name: 'Off'
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_off
	        type: 'custom:button-card'
	      - icon: 'mdi:arrow-up-bold-outline'
	        name: Haut
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_up
	        type: 'custom:button-card'
	      - icon: 'mdi:video-vintage'
	        name: VOD
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_vod
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:arrow-left-bold-outline'
	        name: Gauche
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_gauche
	        type: 'custom:button-card'
	      - icon: 'mdi:stop'
	        name: Ok
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_ok
	        type: 'custom:button-card'
	      - icon: 'mdi:arrow-right-bold-outline'
	        name: Droite
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_droite
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:undo-variant'
	        name: Retour
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_back
	        type: 'custom:button-card'
	      - icon: 'mdi:arrow-down-bold-outline'
	        name: Bas
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_down
	        type: 'custom:button-card'
	      - icon: 'mdi:monitor-dashboard'
	        name: Menu
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_menu
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-plus'
	        name: Vol Plus
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_plus
	        type: 'custom:button-card'
	      - icon: 'mdi:arrow-up-bold-outline'
	        name: Prog+
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_programme_plus
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-mute'
	        name: Mute
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_mute
	        type: 'custom:button-card'
	      - icon: 'mdi:play-pause'
	        name: Pause
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_pause
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - icon: 'mdi:volume-minus'
	        name: Vol-
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_volume_moins
	        type: 'custom:button-card'
	      - icon: 'mdi:arrow-down-bold-outline'
	        name: Prog-
	        size: 20%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_programme_moins
	        type: 'custom:button-card'
	    type: horizontal-stack
	  - cards:
	      - cards:
	          - icon: 'mdi:numeric-1-box-outline'
	            name: TF1
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_tf1
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-2-box-outline'
	            name: France 2
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_2
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-3-box-outline'
	            name: France 3
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_3
	            type: 'custom:button-card'
	        type: horizontal-stack
	      - cards:
	          - icon: 'mdi:numeric-4-box-outline'
	            name: Canal+
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_canal_plus
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-5-box-outline'
	            name: France 5
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_france_5
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-6-box-outline'
	            name: M6
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_m6
	            type: 'custom:button-card'
	        type: horizontal-stack
	      - cards:
	          - icon: 'mdi:numeric-7-box-outline'
	            name: Arte
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_arte
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-8-box-outline'
	            name: C8
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_c8
	            type: 'custom:button-card'
	          - icon: 'mdi:numeric-9-box-outline'
	            name: W9
	            size: 15%
	            tap_action:
	              action: call-service
	              service: rest_command.tv_w9
	            type: 'custom:button-card'
	        type: horizontal-stack
	    type: vertical-stack
	  - cards:
	      - icon: 'mdi:rewind'
	        name: Rewind
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_rewind
	        type: 'custom:button-card'
	      - icon: 'mdi:pause'
	        name: Pause
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_pause
	        type: 'custom:button-card'
	      - icon: 'mdi:fast-forward'
	        name: Fastforward
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_fastforward
	        type: 'custom:button-card'
	      - icon: 'mdi:record-rec'
	        name: Record
	        size: 15%
	        tap_action:
	          action: call-service
	          service: rest_command.tv_record
	        type: 'custom:button-card'
	    type: horizontal-stack
	type: vertical-stack

