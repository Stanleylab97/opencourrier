# opencourrier
Procedure de déploiement d’Opencourrier sur un serveur Debian 8  

> apt-get install apache2  
> apt-get install php5  
> apt-get install postgresql  postgresql-client  
> apt-get install sudo
> sudo-s –u postgres
> psql 
	> _password postgres
	> \password postgres
	> \q
	> exit
> apt-get install vim
> vim /etc/postgresql/9.4/main/main/pg_hba.conf
	changer le peer de  local de à md5
> apt-get install postgresql-contrib phppgadmin
>  vim /etc/apache2/conf-available/phppgadmin.conf
	Changer AllowOverride None à  AllowOverride ALL
	Changer Require local à Allow from All
>  vim	/etc/phppgadmin/config.inc.php
	$conf[‘extra_login_security’]=false ;
> cd  /var/www/html
> wget https://adullact.net/frs/download.php/file/7298/opencourrier-4.0.0.zip 
>apt-get install unzip
> unzip opencourrier-4.0.0.zip 
> mv opencourrier-4.0.0.zip opencourrier 
> /etc/init.d/postgresql  restart
> /etc/init.d/apache2  restart
> ifconfig pour optenir l’adresse ip du serveur
>Aller dans un navigateur et se connecter à phppgadmin via adresse_serveur/phppgadmin avec 
	Username : postgres et le mot de passe définit plus haut.
> ouvrir la base postgres et la remplir avec les données stockées dans les fichiers 
•	init.sql
•	init_metier.sql
•	init_parametrage.sql

Revenir au terminal
>  vim /var/www/html/opencourrier/dyn/database.inc.php
	Changer le mot de passe à  Opencourr!er, le nom de la base à postgres, le schéma à public
> /etc/init.d/postgresql  restart
> /etc/init.d/apache2  restart 
> exit
> Repartir dans un nouvel onglet du navigateur et  saisir adresse_serveur /opencourrier 
	Connectez-vous avec login : admin et password : admin
Déploiement terminé
