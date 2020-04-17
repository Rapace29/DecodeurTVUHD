
**Table des matières**

[TOCM]

[TOC]
# Présentation
### Fonctionalitées

- Permet de piloter son décodeur **TV HD Orange** à partir de Home Assistant

### Decodeur TV UHD
Le **décodeur TV UHD** est fourni par Orange dans le cadre d&apos;une souscription à un abonnement Internet "grand public". C&apos;est un boitier séparé de la **Livebox**.
Dans ma configuration, on a un **Home Assistant **qui tourne sur un Raspberry sur le même LAN que le décodeur TV.

# Installation

###liste des modifications à faire

1. Modifier dans le fichier *configuration.yaml*  
2. Créer un fichier yaml contenant les commandes pour le décodeur
3. Rajouter une ou plusieurs cartes dans l&apos;interface lovelace


### 1. Modifier dans le fichier *configuration.yaml*  

    # fichier des commandes pour le Decodeur TH  HD Orange
	rest_command: !include rest_command.yaml

### 2. Créer un fichier yaml contenant les commandes pour le décodeur.

	# Pilotage du décodeur TV Orange    
	#  https://tv-orange.pourqui.com/commandes.html 
	#   et https://tv-orange.pourqui.com/site.html
	tv_off:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=116&mode=00'
	tv_up:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=103&mode=00'
	tv_vod:
	  url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=393&mode=00'
	tv_gauche:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=105&mode=00'
	tv_ok:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=352&mode=00'
	tv_droite:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=106&mode=00'
	tv_back:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=158&mode=00'
	tv_down:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=108&mode=00'
	tv_menu:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=139&mode=00'
	tv_volume_plus:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=115&mode=00'
	tv_volume_mute:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=113&mode=00'
	tv_volume_moins:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=114&mode=00'
	tv_programme_plus:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=402&mode=00'
	tv_pause:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=164&mode=00'
	tv_programme_moins:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=403&mode=00'
	    
	tv_rewind:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=168&mode=00'
	tv_fastforward:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=159&mode=00'
	tv_record:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=01&key=167&mode=00'    
	    
	tv_one_more_think:    
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=10' 
	tv_tf1:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******192&uui=1'
	tv_france_2:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*********4&uui=1'
	tv_france_3:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********80&uui=1'
	tv_canal_plus:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********34&uui=1'    
	tv_france_5:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********47&uui=1'    
	tv_m6:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******118&uui=1'    
	tv_arte:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******111&uui=1'    
	tv_c8:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******445&uui=1'    
	tv_w9:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******119&uui=1'    
	tv_tmc:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******195&uui=1'    
	tv_tfx:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******446&uui=1'    
	tv_nrj12:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******444&uui=1'    
	tv_lcp:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******234&uui=1'    
	tv_france_4:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********78&uui=1'    
	tv_bfm:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******481&uui=1'    
	tv_cnews:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******226&uui=1'    
	tv_cstar:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******458&uui=1'    
	tv_gulli:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******482&uui=1'    
	tv_france_o:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******160&uui=1'    
	tv_tf1_series:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******1404&uui=1'    
	tv_equipe:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******1401&uui=1'    
	tv_6ter:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******1403&uui=1'    
	tv_rmc_decouverte:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******1400&uui=1'    
	tv_cherie_25:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******1399&uui=1'    
	tv_lci:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******112&uui=1'    
	tv_france_info:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=******2111&uui=1'    
	    
	tv_bbc_world:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********19&uui=1'    
	tv_deutsche_well:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=********61&uui=1'    
	tv_france_3_bretagne:
	    url: 'http://192.168.1.58:8080/remoteControl/cmd?operation=09&epg_id=*******634&uui=1'    


### 3. Rajouter une ou plusieurs cartes dans l&apos;interface lovelace 

Voila quelques exemples de cartes à rajouter dans l&apos;interface lovelace.
Le plus simple est de passer en mode modication, rajouter  une carte en clickant sur le bouton "+" en bas à droite et de choisir une carte "Manuel".
On peut alors faire une copie du texte fourni ici.

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

