# Tuto: Connection au grafana de la pool

Ce petit tuto (non complet pour le moment) va vous permettre de monter un setup-up pour vous connecter au grafana de la pool. Malheureusement pour le moment, ce n'est pas magique ni automatique, vous devez vous rapprocher de =<@242241376840974336> | @Mozquito | @Tocard pour avoir accès a grafana.


# Le package fournis par FenchFarmer

Vous pouvez télécharger le tout [ici](https://github.com/Tocard/FrenchFarmerMonitoring/releases) dans les assets. C'est le fichier zip mentionné durant le tuto.

# Telegraf

Afin de recolter des metriques sur votre ordinateur ([c'est quoi une métrique](https://fr.wikipedia.org/wiki/M%C3%A9trique_(logiciel))), on utilise [telegraf](https://www.influxdata.com/time-series-platform/telegraf/). Vous trouverez dans le zip une version de telegraf, libre à vous d'en prendre une autre, elle n'est pas modifié, c'est juste une question de simplicité.  Vous pouvez télécharger cela [ici](https://portal.influxdata.com/downloads/). Prenez soin de ne pas prendre de nighty buyild et de prendre une une version supérieur à la 1.18.0.

## Modification de la configuration de télégraf.

Dans le fichier.zip, vous trouverez un fichier telegraf.conf que vous allez devoir modifier. Pour le moment ce fichier est uniquement compatible windows, la version linux est assez simple a faire, rapprochez vous de <@242241376840974336> | @Mozquito | @Tocard au besoin.
Dans le fichier telegraf.conf, vous allez trouvez des champs avec les clefs au format **PUT_YOUR_VAL_HERE-valeur** comme par exemple **PUT_YOUR_VAL_HERE-USER** ou encore **PUT_YOUR_VAL_HERE-LAUCNHER_ID**. Ce sont des valeurs que vous allez devoir remplir.
	
	Ligne 2: launcher_id = "PUT_YOUR_VAL_HERE-LAUNCHER_ID"  => votre launcher_id
	Ligne 31:   username = "PUT_YOUR_VAL_HERE-USER" => le user que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	Ligne 32:   password = "PUT_YOUR_VAL_HERE-PASSWORD" => le password que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	Ligne 33:   index_name = "data-PUT_YOUR_VAL_HERE-USER" => le user que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	Ligne 47:   username = "PUT_YOUR_VAL_HERE-USER" => le user que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	Ligne 48:   password = "PUT_YOUR_VAL_HERE-PASSWORD" => le password que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	Ligne 49:   index_name = "chia-PUT_YOUR_VAL_HERE-USER" => le user que <@242241376840974336> | @Mozquito | @Tocard va vous donner
	
	Pour trouvez les valeurs suivante, il faut utiliser  "%HOMEPATH%/.chia/mainnet/config/ssl/full_node dans un explorer, ça vous donneras le path, par default, c'est C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node
    Il ne faut pas mettre le contune du fichier, juste le chemin.
	
	Ligne 186:   tls_cert = "PUT_YOUR_VAL_HERE-PATH/private_full_node.crt"  => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.crt
	Ligne 187:   tls_key = "PUT_YOUR_VAL_HERE-PATH/private_full_node.key" => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.key
	Ligne 209:   tls_cert = "PUT_YOUR_VAL_HERE-PATH/private_full_node.crt" => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.crt
	Ligne 210:   tls_key = "PUT_YOUR_VAL_HERE-PATH/private_full_node.key" C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.key
	Ligne 230:   tls_cert = "PUT_YOUR_VAL_HERE-PATH/private_full_node.crt" => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.crt
	Ligne 231:   tls_key = "PUT_YOUR_VAL_HERE-PATH/private_full_node.key" C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.key
	Ligne 253:   tls_cert = "PUT_YOUR_VAL_HERE-PATH/private_full_node.crt" => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.crt
	Ligne 254:   tls_key = "PUT_YOUR_VAL_HERE-PATH/private_full_node.key" C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.key

    Ligne 267:   "https://api.frenchfarmers.net/farmer/PUT_YOUR_VAL_HERE-LAUNCHER_ID_WITHOUT_0x" => mettre le launcher id sans le 0x devant

	Ligne 271:   tls_cert = "PUT_YOUR_VAL_HERE-PATH/private_full_node.crt" => C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.crt
	Ligne 272:   tls_key = "PUT_YOUR_VAL_HERE-PATH/private_full_node.key" C:\Users\\**Votre_User**\\.chia\mainnet\config\ssl\full_node\private_full_node.key

## Lancement du telegraf

Dans le zip vous allez trouver un fichier .bat qui fait `./telegraf.exe --config telegraf.conf` tout simplement, je vous recomande de créer un raccourci et de le mettre dans votre lanceur de démarrage.
Si vous ne savez pas comment y acceder, faite `Windows+R` et taper `shell:startup`. Tout ce que vous mettez ici sera lancé au démarrage de windows.

## Acceder à grafana

Vous trouverez l'adresse du grafana [ici](https://grafana.ether-source.fr/) (https://grafana.ether-source.fr/). Pour vous connecter, vous devez utiliser les identifiant que <@242241376840974336> | @Mozquito | @Tocard vous a donné.

## Metrique system

Pour consulter les metriques systems Windows, vous avez un dashboard déja fait regroupant toutes les informations de vos machines (cpu, ram, disque, network). Le liens est [ici](https://grafana.ether-source.fr/d/NrfbdEi7z/stats-windows)

Afin de retrouvez votre machine, vous avez deux mennu en haut à gauche, il vous suffit de selectionner dans **datasource**,  **data-user **  (le user fournit par <@242241376840974336> | @Mozquito | @Tocard ) et dans **node**, le nom de votre machine windows.


## Metrique Chia

Pour consulter les metriques chia, vous avez un dashboard déja fait regroupant toutes les informations de vos harvester. Le liens est [ici](https://grafana.ether-source.fr/d/vvrimum7k/chia-monitor?orgId=4)

Afin de retrouvez votre machine, vous avez deux menu en haut à gauche , il vous suffit de selectionner dans **datasource**,  **chia-user **  (le user fournit par <@242241376840974336> | @Mozquito | @Tocard ) et dans **launcher_id**, votre launcher_id


# Metrique GPU

Si vous avez un rig, et que vous souhaitez le monitorer avec cette solution c'est possible, rapprochez vous de <@242241376840974336> | @Mozquito | @Tocard


# Discord de l'équipe

https://discord.gg/Wp5Jg8kM
