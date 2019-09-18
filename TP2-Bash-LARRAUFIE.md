
LARRAUFIE Tom

3A ICS

  

# Administration Système TP 2 - Bash

  

## Exercice 1. Variables d’environnement

  

### 1. Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur ?

Les commandes tapé par l'utilisateur ne sont pas toutes stockées au même endroit.

C'est pourquoi il existe une variable appelé **PATH** qui regroupe l'ensemble des chemins vers les fichiers contenant les commandes de l'utilisateur.

Voici ce que la commande **PATH** contient:
(commande ```echo $PATH```)

>tom@serveur:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin


### 2. Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans votre répertoire personnel ?
Nous pouvons afficher toutes les variables d’environnement avec la commande suivante:
```env```
On remarque dans ce fichier qu'une variable se nomme **HOME**
et qu'elle contient le chemin de notre répertoire personnel.
>HOME=/home/tom

On peut donc en déduire que la commande **cd** passé sans argument utilise le contenu de la variable d’environnement **HOME** pour nous ramener dans notre répertoire personnel.
  
  
### 3. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL et _.

**LANG**: Cette variable permet de déterminer la langue des messages à afficher et l'encodage à utiliser.
>tom@serveur:~$ echo $LANG
fr_FR.UTF-8

**PWD**: Cette variable permet d’afficher le chemin du répertoire courant.
>tom@serveur:~$ pwd
/home/tom

**OLDPWD**: Cette variable permet d’afficher le chemin du répertoire courant précédent.
>tom@serveur:~$ echo $OLDPWD
/bin

**SHELL**: Indique le chemin de l’interpréteur utilisé par défaut.
>tom@serveur:~$ echo $SHELL
/bin/bash

**_**: Cette variable permet de changé la langue ainsi que les 

  

### 4. Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe.
On crée une variable locale MY_VAR avec la commande suivante:
**MY_VAR="test"**
On peut tester la réussite avec la commande echo $MY_VAR:
>tom@serveur:~$ MY_VAR="test"
tom@serveur:~$ echo $MY_VAR
test

  
### 5. Tapez ensuite la commande bash. Que fait-elle ? La variable MY_VAR existe-t-elle ? Expliquez. A la fin de cette question, tapez la commande exit pour revenir dans votre session initiale.
La commande **bash** nous ouvre un **sous-shell**.
On tape alors la notre commande **MY_VAR** dans ce **sous-shell**.
On observe que la commande n'existe plus. Pourquoi ?
>tom@serveur:~$ bash
tom@serveur:~$ echo $MY_VAR
 
 La variable que nous avons créé est une variable locale ce qui indique qu'elle ne peut être présente dans le **sous-shell** mais uniquement dans le shell ou elle a été créé.
On revient dans notre session initial avec la commande exit.

  

### 6. Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Expliquez.
On crée alors une variable d’environnement.
>tom@serveur:~$ export MY_VAR="test"
tom@serveur:~$ echo $MY_VAR
test

Ensuite on recommence les étapes de la question précédente.
>tom@serveur:~$ bash
tom@serveur:~$ echo $MY_VAR
test

Cette fois ci la variable existe dans le **sous-bash**.

### 7. Créer la variable d’environnement NOMS ayant pour contenu vos noms de binômes séparés par un espace. Afficher la valeur de NOMS pour vérifier que l’affectation est correcte.
On crée la variable NOMS avec la commande suivante:
**tom@serveur:~$ export NOMS="LARRAUFIE LAPLUME"**
Et on vérifie que l'affectation est correct.
>tom@serveur:~$ echo $NOMS
LARRAUFIE LAPLUME

### 8. Ecrivez une commande qui affiche ”Bonjour à vous deux, binôme1 binôme2 !” (où binôme1 et binôme2 sont vos deux noms) en utilisant la variable NOMS.
>tom@serveur:~$ echo "Bonjour à vous deux, $NOMS !"
Bonjour à vous deux, LARRAUFIE LAPLUME !

### 9. Quelle différence y a-t-il entre donner une valeur vide à une variable et l’utilisation de la commande unset ?
Donner une valeur vide à une variable ne la supprime, cette dernière est donc gardé en mémoire.
La commande **unset** permet de supprimer définitivement la variable de la mémoire.

### 10. Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre dossier personnel d’après bash)
>tom@serveur:~$ echo '$HOME' = $HOME
$HOME = /home/tom

Vous enregistrerez vos scripts dans un dossier script que vous créerez dans votre répertoire personnel. Tous les scripts sont bien entendu à tester. Ajoutez le chemin vers script à votre PATH de manière permanente.

**tom@serveur:~/script$ export PATH=$PATH:/home/tom/script
tom@serveur:~/script$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/tom/script**

### Exercice 2. Contrôle de mot de passe Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par l’utilisateur ne doit pas s’afficher.

Pour commencer, création du script:
**tom@serveur:~/script$ touch testpwd.sh**

Ensuite nous devons rendre le script exécutable avec la commande suivante:
**tom@serveur:~/script$ chmod u+x testpdw.sh**
``` 
#!/bin/bash
PASSWORD=123 # variable avec le mot de passe en dur à tester

echo "Saississez votre mot de passe :" 
read -s mdp  # la variable mdp récupère la valeur saisie

if [ $PASSWORD = $mdp ]; # compare les deux variables
then
        echo "Le mot de passe est correct !"
else
        echo "Le mot de  passe est incorrect :( "
fi
```

**Si le mot de passe entré est le bon:**
>tom@serveur:~$ script/testpwd.sh
Saississez votre mot de passe :
Le mot de passe est correct !

**Sinon**
>tom@serveur:~$ script/testpwd.sh
Saississez votre mot de passe :
Le mot de  passe est incorrect :(

### Exercice 3. Expressions rationnelles. Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre est un nombre réel : 
```
function is_number()
{
re='^[+-]?[0-9]+([.][0-9]+)?$'
if ! [[ $1 =~ $re ]] ; then
return 1
else
return 0
fi
}
```
Il affichera un message d’erreur dans le cas contraire

On utilise la fonction donné, l'utilisateur appelle le script avec une valeur en paramètre.
Cette valeur est alors analysé par la fonction qui retourne un **1** si la valeur n'est pas un réel et un **0** sinon.
```
#!/bin/bash
function is_number()
{
        re='^[+-]?[0-9]+([.][0-9]+)?$'
        if ! [[ $1 =~ $re ]] ; then
                return 1
        else
                return 0
        fi
}
is_number $1
if [ $? = 0 ] ; then
        echo "le paramètre entré est un réel"
else
        echo "le paramètre n'est pas un réel"
fi
```
**Si le paramètre entré est un réel:**
>tom@serveur:~/script$ bash exercice3.sh 15
le paramètre entré est un réel

**Si le paramètre entré n'est pas un réel:**
>tom@serveur:~/script$ bash exercice3.sh are
le paramètre n'est pas un réel

### Exercice 4. Contrôle d’utilisateur Écrivez un script qui vérifie l’existence d’un utilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation : nom_du_script nom_utilisateur”, où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement) 
```
#!/bin/bash
nb_user=$(cat /etc/passwd | wc -l)
for i in $(seq 1 $nb_user)
do
        user=$(cat /etc/passwd | cut -d : -f1 | sort | head -n $i | tail -n 1) #commande pour afficher la première colonne avec le séparater

        if ! [ $1 ]
        then
                echo "Utilisation : $0 nom_utilisateur"
                exit
        else
                if [ "$1" = "$user" ]
                then
                        echo "L'utilisateur $user existe"
                        exit
                fi
        fi
done
echo "L'utilisateur $1 n'existe pas"
exit
```

**user=$(cat /etc/passwd | cut -d : -f1 | sort | head -n $i | tail -n 1)**
Cette commande permet d'extraire la première colonne en coupant le reste au premier séparateur **:**, ce qui permet ensuite de comparé chaque utilisateur à celui entré en paramètre.
Car la variable $i dans la commande nous sert d'indice et permet de parcourir tout les utilisateurs qui sont ressorti du tri.

**Si le script est appelé sans nom :**
>tom@serveur:~/script$ bash user.sh
Utilisation : user.sh nom_utilisateur

**Si le script est appelé avec comme paramètre tom:**
>tom@serveur:~/script$ bash user.sh tom
L'utilisateur tom existe

### Exercice 5. Factorielle Écrivez un programme qui calcule la factorielle d’un entier naturel passé en paramètre (on supposera que l’utilisateur saisit toujours un entier naturel). 
```                                                                        #!/bin/bash

read -p  "Saisissez un nombre entier :"  ent
f=1
for i in $(seq 1 $ent) #boucle avec l'indice i de 1 à la valeur entré
do
        f=$(($f*$i)) # f prend la valeur de f fois l'indice i courant
done
echo " La factorielle de $ent est :"$f
```
Le code nous propose d'entré une valeur, puis le code nous calcule automatiquement la factorielle de cette valeur.

### Exercice 6. Le juste prix Écrivez un script qui génère un nombre aléatoire entre 1 et 1000 et demande à l’utilisateur de le deviner. Le programme écrira ”C’est plus !”, ”C’est moins !” ou ”Gagné !” selon les cas (vous utiliserez $RANDOM). 

Pour commencer, création du script:
**tom@serveur:~/script$ touch prix.sh**

Ensuite nous devons rendre le script exécutable avec la commande suivante:
**tom@serveur:~/script$ chmod u+x prix.sh**

Puis nous pouvons commencer à écrire notre script
les variables:
```
echelle=1000
nombre=$RANDOM
let "nombre %= $echelle"
```
Cette partie du code initialise les variables, 
```
#!/bin/bash
echelle=1000
nombre=$RANDOM
let "nombre %= $echelle"
echo "Saisir un nombre (entre 1 et 1000): "
read nb
while [ $nb -ne $nombre ]
do

        if [ $nb -lt $nombre ] ; then
                echo "c'est plus + !"
        elif [ $nb -gt $nombre ] ; then
                echo "c'est moins - !"

        fi

        echo -e "\nSaisir un nombre :"
        read new
        nb=$new
done
if [ $nb -eq $nombre ] ; then
        echo "BRAVO vous avez trouvé le juste prix ! --> $nombre <--"
fi
```
Ensuite nous pouvons tester le code en exécutant le script.
Avec l'appelle du script suivant :

>tom@serveur:~/script$ bash prix.sh

Puis le programme commence alors le jeu et nous demande de saisir un nombre entre 1 et 1000. On entre une valeur et le script nous répond si le nombre généré aléatoirement est supérieur ou inférieur.
>Saisir un nombre (entre 1 et 1000):
500
c'est moins - !

>Saisir un nombre :
250
c'est plus + !

>Saisir un nombre :
439
c'est moins - !

>Saisir un nombre :
436
BRAVO vous avez trouvé le juste prix ! -> 436 <--



### Exercice 7. Statistiques 

#### 1. Écrivez un script qui prend en paramètres trois entiers (entre -100 et +100) et affiche le min, le max et la moyenne. Vous pouvez réutiliser la fonction de l’exercice 3 pour vous assurer que les paramètres sont bien des entiers. 

#### 2. Généralisez le programme à un nombre quelconque de paramètres (pensez à SHIFT) 

#### 3. Modifiez votre programme pour que les notes ne soient plus données en paramètres, mais saisies et stockées au fur et à mesure dans un tableau.

