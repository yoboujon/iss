- BLERP : 
    - **Bandwidth**: Can we send large amounts of data ?
    - **Latency**: Do we need a fast response ?
    - **Economics**: Is transmission costy ? Is it better to process locally ?
    - **Reliability**: How much trust in our system do we need ?
    - **Privacy**: Is data sensitive ?

## Qualitative Features
On cherche une corrélation entre deux attributs qui sont différents en colonne et en ligne notamment.
Example avec une population aux cheveux d'une couleur et yeux d'une autre qui nous permet d'avoir un profil moyen et d'observer une corrélation entre les deux.
Autre exemple avec un accéléromètre à 3 axes, qui nous permet d'observer une corrélation entre les 3 axes dans des scénarios définis.

### What about Emedded IA ?
Les plus grands problèmes dans l'IA en embarqué c'est la qualité des donnés, si celles-là sont bruités c'est un problème. La taille aussi des donnés est limité. Les resources ne sont pas illimtés.

### Data Cleaning
#### Binarisation
La methode de la binarisation consiste à donner un nombre, le plus souvent un nombre binaire. Mettre des entiers peut poser problème lors du calcul de la `loss`: Si des classes sont plus proches que les autres (0,1,2,3 -> 3-1 = 2, poids plus important) cela peut poser des problèmes car les poids seront différent alors qu'il n'y a pas forcément de sens lié à cela.
#### Scaling
Normaliser les datasets, standardiser les variables pour avoir un écart type de 1. Prenons un exemple: le nombre de pas de 0 à 8'000'000, l'age de 0 à 100 ans. Les deux devraient être normalisés.
$$\tilde{x}=\frac{\bar{x}-x}{\sigma_s}$$
#### Erroneous data
Dans un set de donné, certaines fréquences sont considérées comme du bruit. Une technique est la réduction de dimension pour réduire ce dernier. 

Pour jouer avec: https://playground.tensorflow.org/

On observe donc que plus les données ainsi que le bruit sont élevées, plus il est compliqué pour un modèle de correctement labéliser.

### Feature selection
Parfois certaines donnés ne servent pas. Il faut faire attention et choisir quelles données peuvent être corrélés ou non. 