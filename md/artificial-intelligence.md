- BLERP : 
    - **Bandwidth**: Can we send large amounts of data ?
    - **Latency**: Do we need a fast response ?
    - **Economics**: Is transmission costy ? Is it better to process locally ?
    - **Reliability**: How much trust in our system do we need ?
    - **Privacy**: Is data sensitive ?

Quantitative: c'est les chiffres, Qualitatif c'est les labels.
Superviser c'est labeliser. **MNIST**: le `Hello, world!` du ML. 

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

> Theorème de continuation universel

## Reduction de dimension

- Théorie probabiliste
- Réseaux de neurones
- Vecteurs propres

La reduction de dimension permet d'observer plus efficacement des résultats, des groupes avec trop de dimension est absolument impossible à visualiser ou trier. Il est possible de décomposer comme une analyse de Fourier des dataset: il est possible d'extraire du sens dans des données qui semblent très différente.

Il existe aussi la **DCT**: Transformation Cosinus Discret, on réaliser une FFT sur un plus grand échantillon: le `.jpg` utilise cette transformation, on perd peu d'information notamment le bruit. **Transformation Gabor** est utilisé pour la musique: elle garde le temporel. **Transformation Wavelet**: elle permet de récupérer des signaux très spécifiques, appelés *wavelets*.

## Faire du ML avec des données temporelles

**k-Nearest Neighbors (k-NN)**: On classifie chaque point et on trouve une corrélation entre eux: les cas plus près. Le nouveau point est donc déterminé à partir de cela. On détermine cela à partir de la distance euclidienne entre chaque point dans le dataset.

Dans le temporel, c'est une suite de valeur qui peut être défini par label, donc $N$ vecteurs = un individu/un sample.

## Convolutional Neural Networks
La taille du réseau de neuronnes ne dépend pas sde la taille de l'image, mais plus de la taille du filtre. Une image avec 3 dimensions: RGB par exemple. On utilise plutôt des GPU pour les CNN, car elle permettent des tâches parallèles, notamment des filtres de convolution sur une même plage. Cependant, la GPU est meilleure pour le temps de calculation, pas le chargement en mémoire -> Ce n'est pas adapté pour le Machine Learning.

On peut ajouter du padding autour des bordures pour ne pas perdre de l'information, en général c'est $2p$.Le Max-pooling prend les valeures maximales sur des zones de $2\times{2}$, cela permet de réduire la taille de l'image. **L'average pooling** permet lui de supprimer du bruit en moyennant les sous-patches *(zone de $2\times{2}$)*. Batch normalization est une autre méthode de 2015 elle permet de normaliser entre chaques couches du réseau, cela induit:
- Même echelle entre gradiants
- Convergeance plus rapide
- Moins d'erreurs de valeurs

Le réseau convolutionnel est le seul qui permet de déterminer de manière correcte la classification d'image.