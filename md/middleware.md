## TP3

### Introduction

On git clone `ACME-oneM2M-CSE` ainsi que `onem2m-jupyter-notebooks`. Pour installer la suite ACME OneM2M. Il faut ensuite tester le IN-CSE pour observer que tout fonctionne correctement.

```bash
python3.10 -m pip install -r requirements.txt
python3.10 setup.py install
python3.10 -m acme
```

Nous pouvons nous connecter sur l'interface web avec le port 8080. CSE ou Common Service Entity permet de gérer des ressources et des entités, plus particulièrement leur communication intrasec. Il est possible d'intéragir avec des requêtes POST et GET.

Le CSE-IN ou *Infrastructure Node* est un serveur qui permet de gérer chaque entité du système OneM2M. Il gère une base de donnée avec les capteurs, applications et configurations des différentes ressources.

### Jupyter Notebook

#### Chapitre 1: Intrdouction
On lance donc une requête REST qui demande depuis le CSE un simple test de connexion avec le nom et l'identifier. On reçoit une réponse OK. Il existe comme expliqué dans ce notebook de nombreux attributs pour pouvoir récupérer diverses informations.

#### Chapitre 2: Ressources et Requêtes
Dans ce notebook, il a été possible de créer une ressource cette fois-ci, avec un nom, un id, et d'autres champs permettant la connectivité. Ensuite il est possible de créer un conteneur directement dans la ressource précedemment créer, avec la variable "to" et des paramètres dans "primitiveContent". Il est ensuite possible dans ce container encore une fois à l'aide de "to" de rajouter une instance, notamment des informations comme ici "Hello World". Tout cela a été utilisé avec "*CREATE*".

Ensuite nous pouvons récupérer ces informations avec "*RETRIEVE*" la requête curl est la suivante:
```
requete
```
Avec la réponse suivante:
```
reponse hello world mécouilles
```

Il est aussi possible de lancer "*UPDATE*": cela permet de mettre à jour une ressource.

"*DELETE*" permet à son tour de supprimer une ressource. Il est possible de faire cela avec une requête curl ou directement en python.