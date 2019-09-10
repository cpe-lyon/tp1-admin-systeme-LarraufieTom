LARRAUFIE TOM
COMPTE RENDU TP1 ADMIN SYSTEM
10/09/2019


# Exercice 2. Prise en main de l’interpréteur de commandes

## Manuel 

### 1. A l’aide du manuel, identifiez le rôle de la commande which.
    
Pour *cela*, on entre dans la console la commande man which.
    
La commande which sert donc à localiser une commande.

### 2. Quand on consulte cette page, comment peut-on rechercher, par exemple, le mot option?
    
Quand on consulte une page du manuel, on peut rechercher un mot avec la commande suivante: 
    
```/[mot a rechercher]```

Ensuite le le mot recherché apparaît en contraste avec le reste du manuel.

### 3. Comment quitte-t-on le manuel? 

Pour quitter le manuel, il suffit d'appuyer sur la touche ```q``` dans la console.

### 4. Chaque section du manuel a une première page, qui présente le contenu de la section. 
    
Aﬀicher la première page de la section 6; de quoi parle cette section?

Pour afficher la première page de la section 6 du manuel, il faut rentrer la commande suivante:

```man 6 intro```

Cette dernière nous ouvre le manuel à la section 6 qui parle de  ***Jeux, économiseurs d’écran, gadgets...***

## Navigation dans l’arborescence des fichiers 

### 1. allez dans le dossier /var/log 

pour aller dans le dossier ***/var/log*** il faut utiliser la commande **cd** qui signifie "change directory" et qui permet de se deplacer dans l'arborescence et dans les differents répertoires.

```cd /var/log```

Nous voila dans le dossier **/var/log**.

### 2. remontez dans le dossier parent (/var) en utilisant un chemin relatif 

Pour retourner dans le dossier parent **/var** en utilisant un chemin relatif, il suffit d'utiliser la même commande avec ***deux points***

```cd ..```

Cette commande nous permet de retourner dans le dossier parent du dossier courant.

>tom@serveur:/var _

### 3. retournez dans le dossier personnel 

Pour retourner dans le dossier personnel, il faut utiliser la commande suivante:

```cd $HOME``` ou ```cd ~``` ou  ```cd```

Cette commande nous permet de retourner dans le dossier personnel.

>tom@serveur:~$ _

### 4. revenez au dossier précédent (/var) 
Pour retourner au dossier précédent, il faut utiliser la commande suivante:

```cd -```

Cette commande permet de retourner au dossier dans lequel on était précédement.
>tom@serveur:/var _

### 5. essayez d’accéder au dossier /root; que se passe-t-il? 
On tape la commande pour acceder au dossier **/root** à partir du dossier personnel avec la commande suivante:

```cd /root```

Mais un message d'erreur affiche: *Permission denied*
Ce qui indique que le dossier n'est pas accessible avec notre compte utilisateur.

### 6. essayez la commande sudo cd /root; que se passe-t-il? Expliquez 
Lorsque l’on tape la commande **cd /root**
un message d'erreur apparait et nous indique que la commande n'a pas été trouvé.
>"command not found" 


### 7. à partir de votre dossier personnel, créez l’arborescence suivante :

Pour créer un dossier, il faut utilisé la commande suivante:
```mkdir```
Et pour créer un fichier la commande suivante:
```touch```
Puis on créer l'arborescence.

### 8. revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1; que se passe-t-il? 

On essaye de supprimer le Fichier1 et le dossier1 à partir du dossier personnel avec la commande ```rm``` qui signifie **remove**.

Pour le Dossier1, un message d'erreur indique:
>cannot remove 'Dossier1': Is a directory

Ce qui indique que le dossier1 ne peut etre supprimé car ce n'est pas un fichier mais un dossier.

Pour le Fichier1, un message d'erreur indique:
>cannot remove 'Fichier1' : No such file or directory

Ce qui indique que le fichier1 est introuvable, en effet car nous ne somme pas au bon endroit pour pouvoir supprimer ce fichier.


### 9. quelle commande permet de supprimer un dossier?

La commande qui permet de supprimer un dossier est la suivante:

```rmdir [nom du dossier]``` ou ```rm -d [nom du dossier]```

Attention, le dossier doit être vide pour pouvoir être supprimé.

### 10. que se passe-t-il quand on applique cette commande à Dossier2? 
```mkdir Dossier2```

Un message d'erreur affiche:
>rmdir: failed to remove 'Dossier2': Directory not empty

Ce qui indique que la suppression est impossible car le Dossier2 n'est pas vide.

### 11. comment supprimer en une seule commande Dossier2 et son contenu?
Pour forcer la suppression d'un Dossier qui n'est pas vide et donc supprimer tout son contenu également, il faut utilisé la commande suivante:

```rm -r [nom du dossier]```


Ce qui permet de forcer la suppression du Dossier en question.

## Commandes importantes 

### 1. Quelle commande permet d’aﬀicher l’heure? A quoi sert la commande time? 
La commande qui permet d'afficher l'heure est la suivante:

```date```

qui permet d'afficher la **date complète** et **l'heure**.

La commande **time** , associé a une autre commande permet de voir les ressources utilisé par la commande en question et son temps d’exécution.

``` time [nom de la commande]```


### 2. Dans votre dossier personnel, tapez successivement les commandes ls puis la; que peut-on en déduire sur les fichiers commençant par un point? 

la commande ```ls``` nous affiche tout ce que contient  le répertoire courant.

Et la commande ```la ``` nous affiche également ce que contient le répertoire courant, mais cette commande affiche également les fichiers commençant par un point.

Les fichier commençant par un point sont en réalité des fichiers cachés.

### 3. Où se situe le programme ls? 

Le programme ls se situe dans le dossier bin.
On peut accéder a ce dossier avec le chemin suivant:
>../usr/bin

### 4. Que fait la commande ll? (indice : la commande alias peut vous aider) 
La commande ll est en réalité un **alias**.

Qu'est ce qu'un alias ? Les alias sont des raccourcis qui permettent de réduire la taille d'une commande pour gagner en vitesse.


Quand on tape alias dans la console voila ce que l'on peut observer:
>alias ll='ls -alF'

Donc la commande ll permet d'effectuer la commande ls avec 3 paramètres: a, l et F
qui servent respectivement a:

>-a: Afficher tous les fichiers des répertoires, y compris les fichiers cachés qui commencent par un « . »\
-l: En plus du nom, afficher le type du fichier, les permissions d'accès, le nombre de liens physiques, le nom du propriétaire et du groupe, la taille en octets, et l'horodatage.\
-F: Ajouter un caractère à chaque nom de fichier pour indiquer son type\



### 5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier /bin? 

La commande qui permet d'afficher les fichiers contenus dans le dossier /bin est la suivante:

```ls /bin```

### 6. Que fait la commande ls ..? 

La commande ```ls..``` permet d'afficher et lister tout les éléments du nœud supérieur au répertoire courant.
Les  ```..``` permettent de sélectionner le nœud supérieur de replacement courant


### 7. Quelle commande donne le chemin complet du dossier courant? 
La commande qui permet de donner le chemin complet du dossier courant est la suivante:

```pwd```

pwd qui signifie **p**rint  **w**orking  **d**irectory , donc qui indique le chemin du répertoire.
### 8. Que fait la commande echo 'yo' > plope exécutée 2 fois? 
La commande ```echo``` permet d’écrire dans un fichier des chaines de caractères.
Si le fichier n'existe pas, il est automatiquement créé.

>On peut le vérifier on tapant la commande ls, le fichier plope apparaît

La commande ***echo 'yo' > plope*** indique d’écrire le mot **yo** dans le fichier **plope**.
Cependant écrire une chaîne de caractère avec un seul chevron **( > )** signifie que le contenu du fichier va être écrasé avant l’écriture.
Cela signifie qu'en effectuant 2 fois la commande **echo 'yo' > plope**, la deuxième commande va écrasé le premier **yo** pour faire apparaître le second.

**Résultat:**
>yo


### 9. Que fait la commande echo 'yo' >> plop exécutée 2 fois? 
En effectuant la commande avec deux chevrons **(>>)**, les chaines de caractères ne seront alors pas écrasé lors d'une réécriture mais ajouté à la ligne.

**Résultat:**
>yo
>yo

### 10. A quoi sert la commande file? Essayez la sur des fichiers de types différents. 

La commande file est une commande qui permet de déterminer le type d'un fichier.
**exemple avec la commande ```file Dossier1```:**
>Dossier1: directory

**exemple avec la commande ```file plop```:**
>plop: ASCII Text
### 11. Créez un fichier toto qui contient la chaîne Hello Toto !; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi: qu’observe-t-on? Supprimez le fichier toto; quelle conséquence cela a-t-il sur titi? 

On commence par créer le fichier toto a l'aide de la commande suivante:
```touch toto```
Puis, on inscrit une chaîne de caractère a l’intérieur de ce fichier toto avec la commande suivante:
```echo "hello toto" > toto```
Ensuite on créer un lien titi vers le fichier toto à l'aide de la commande 
```ln toto titi```

On modifie le fichier toto en inscrivant une nouvelle chaîne de caractère avec les commande vu précédemment.
>hello modification

Qu'observe-t-on ?

>On observe que le fichier de titi s'est modifié automatiquement après la modification du fichier toto

A présent, nous allons supprimer le fichier toto avec la commande 
**rm toto**


Le fichier toto est donc bien supprimé, mais on observe que le fichier titi est toujours existant et contient toujours la chaîne de caractère écris précédemment.


### 12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. 
Nous allons créer un lien symbolique a l'aide de la commande suivante:
```ln -s titi tutu```
On remarque un nouveau fichier **tutu** se créer 
#### Modifiez le contenu de titi; quelle conséquence pour tutu? 
On modifie le fichier titi:
```echo "test lien symbo" > titi```
On remarque après modification du fichier titi que le fichier tutu contient la même chaîne de caractère que titi.

#### Et inversement? 
On modifie le fichier tutu:
```echo "test tutu lien" > tutu```
On remarque après modification du fichier tutu que le fichier titi est automatiquement modifié également et contient la même chaîne de caractère que tutu.
#### Supprimez le fichier titi; quelle conséquence cela a-t-il sur tutu? 
On supprime le fichier titi:
```rm titi```
On remarque après suppression du fichier titi que le fichier tutu est toujours existant mais que lien lien entre les deux fichiers est brisé et donc un message d'erreur s'affiche et son contenant a disparu.
>

### 13. Aﬀichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran? 
On affiche à l’écran le fichier /var/log/syslog :
```cat /var/log/syslog```
Les raccourcis clavier qui permettent d'interrompre et reprendre le défilement à l’écran sont les suivants:
**Ctrl + s**   arrête le défilement.
**Ctrl + q** Reprend le défilement.

### 14. Aﬀichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20. 
Plusieurs commandes existent pour afficher seulement les lignes nécessaire a notre besoin:
**head -n**   affiche les n premières lignes.
**tail -n**    affiche les n dernières lignes.

**Pour afficher les 5 premières lignes on utilise:**\
```head -5 /var/log/syslog```\
**Pour afficher les 15 dernières lignes on utilise:**\
```tail -15 /var/log/syslog```\
**Pour afficher les lignes 10 à 20:**\
```sed -n '10,20p' /var/log/syslog```

### 15. Que fait la commande dmesg | less? 
La commande **dmesg**  permet d'obtenir tous les messages du noyau.
Associé a la commande **| less** qui permet d'afficher un texte pages par pages.

### 16. Aﬀichez à l’écran le fichier /etc/passwd; que contient-il? Quelle commande permet d’aﬀicher la page de manuel de ce fichier? 
Le fichier contient toutes les informations relative aux utilisateurs:
**logins, mot de passes...l'entier qui identifie l'utilisateur pour le système d'exploitation (UID=User ID, identifiant utilisateur) l'entier qui identifie le groupe de l'utilisateur (GID=Group ID, identifiant de groupe)**

La commande qui permet d'afficher le manuel est la suivante:
```man passwd```
 
 ### 17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse
 Pour réaliser un tri par ordre alphabétique inverse on utilise la commande suivante:
 ```sort -k 1 -d -r```
 
### 18. Quelle commande nous donne le nombre d’utilisateurs ? 
Pour connaitre le nombre d'utilisateurs connectés on peut utiliser les commandes suivantes:
```who``` ou ```w```


### 19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ? 
Pour trouver le nombre de pages qui comportent le mot-clé **conversion** dans leur description, on utilise la commande suivante:
```man -k conversion```

**resultat de la commande:**
>4 pages comportent le mot-clé conversion dans leur resumé.


### 20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine 
Pour rechercher tous les fichiers se nommant passwd présent sur la machine, on utilise la commande suivante:
```find / -name passwd```

### 21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null 

```find / -name passwd >> ~/list_passwd_files.txt 2>> /dev/null```

### 22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment 
On se place donc dans notre dossier personnel et l'on chercher où est défini l'alias **ll** avec la commande suivante:
```grep "ll" -r```
On trouve l'alias dans le fichier **.bashrc**


### 23. Utilisez la commande locate pour trouver le fichier history.log. 
Nous utilisons la commande locate pour trouver history.log:
>/var/log/apt/history.log


### 24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?
On commence par créer un fichier:
```touch fichier```
Puis on tente de le trouver à l'aide de la commande locate:
```locate fichier```
On constate que la commande n'a pas pu aboutir et affiche une erreur car la base n'a pas été mis à jour via la commande **updatedb** .
Le fichier créé ne peut donc pas être retrouvé avec cette commande.

#### Travailler avec plusieurs shells 
On peut utiliser jusqu’à 6 shells en parallèle. Ils portent les noms ttyX (où X va de 1 à 6) et sont accessibles via Alt + FX



# Exercice 3. Découverte de l’éditeur de texte nano

Nano est un éditeur de texte rudimentaire, où toutes les commandes évidemment se font au clavier. Les raccourcis clavier les plus courants sont aﬀichés en bas de l’écran, mais sous une forme peut-être inhabituelle :
 • ^G signifie **Ctrl + G** 
 • M-U signifie **ALT+U**

Quelques raccourcis utiles :
| Raccourci |Description   
|--|--|
| F1 ou Ctrl + G |  Aﬀichage de l’aide  
| Ctrl + X |  Quitter nano / Fermer une fenêtre / Exécuter une commande  
| Ctrl + R |  Ouvrir un fichier  
| Ctrl + O | Enregistrer sous   
| Ctrl + S | Enregistrer   
| Ctrl + K | Couper   
| Ctrl + U |  Coller  
| Ctrl + W | Rechercher  
|Ctrl + \  |  Remplacer  
| Ctrl + C | Aﬀicher des informations sur la position du curseur (numéro de ligne, de colonne)  
| Alt + U  |  Annuler  
|Alt + E  | Refaire   

# Exercice 4. Personnalisation du shell 
 
 Création d'une copie du fichier ~/.bashrc_bak avec la commande suivante:
 ```cp ~/.bashrc .bashrc_bak```
Ensuite on utilise la commande **source .bashrc** pour éviter de se déconnecter et se reconnecter pour pouvoir afficher les couleurs dans l'invite de commande.
