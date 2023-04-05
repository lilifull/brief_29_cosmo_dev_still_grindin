# brief_29_cosmo_dev_still_grindin

Compte rendu de l'étude de faisabilité : 

Feature extraction Text : 

Dans un premier temps j'ai nettoyé le texte, cette étape est visible dans le notebook : Nettoyage du texte.

Puis j'ai testé 4 techniques afin de créer de nouvelles features à partir du texte : bag of words (count et Tf-idf) et Word2Vec (un modèle entrainé sur les données du projet et un modèle pré-entrainé de google). Pour pouvoir comparer les modèles entre eux, je compare l'accuracy d'un modèle de classification SVC sur les features crées par les différentes méthodes.

Les résultats de bag of words sont disponibles dans le notebook : Bag of words.

Les résultats sont les suivants : 
Accuracy avec la méthode Count et le colonne description : 80.48%
Accuracy avec la méthode Tf-idf et le colonne description : 92.38%
Accuracy avec la méthode Count et le colonne product name :  89.52%
Accuracy avec la méthode Tf-idf et le colonne product name : 91.43%
Accuracy avec la méthode Count et le colonne qui associe description et product name : 88.1%
Accuracy avec la méthode Tf-idf et le colonne qui associe description et product name : 94.29%

Nous pouvons en conclure que la méthode tf-idf donne les meilleurs résultats avec la colonne qui associe la description et le product name.

Les résultats pour Word2Vec sont disponibles dans le notebook suivant : Word2Vec extraction

J'ai seulement utilisé la colonne qui associe description et product name car c'est celle qui donne le plus d'informations et qui donne de meilleurs résultats.

Les résultats sont les suivants :
Accuracy avec le modèle word2vec entrainé sur les données du projet : 45.71%
Accuracy avec le modèle word2vec-google-news-300 : 93.81%

Si on utilise un modèle pré-entrainé de word2vec il donne de très bons résultats également. Conclusion, pour le texte il est possible de classifier les produits à partir de leurs description.

Pour la feature extraction du texte nous pouvons utiliser Tf-idf ou word2vec-google-news-300 qui donnent de bon résultats.

Feature extraction image :

La première technique testée est la méthode SIFT dans le notebook : Pretraitement des images SIFT
Ensuite j'ai testé la méthode ORB dans le notebook : Pretraitement des images ORB
Puis la méthode transfert learning et le modèle VGG16 : Pretraitement des images transfert learning VGG16
Et enfin la méthode transfert learning et le modèle mobile_net : Pretraitement des images transfert learning-mobile net

Résultats : 

SIFT : clustering, score ARI : 0.0012 
       classification, accuracy : 17.62%
       
ORB : clustering, score ARI : 0.00059
      classification, accuracy : 10.48%
      
VGG16 : clustering, score ARI : 0.24012
      classification, accuracy : 56.67%
      
mobile-net : clustering, score ARI : 0.2027
      classification, accuracy : 50.95%
      
Les meilleurs résultats sont produits en utilisant le transfert learning avec le modèle VGG16, bien qu'il soit assez long pour extraire les features. Le modèle mobile-net est quant à lui plus rapide mais donne des résultats inférieurs. Cependant les résultats sont trop bas pour toutes les techniques, ils sont à améliorer pour pouvoir utiliser les features des images pour faire de bonnes classifications.

Pour améliorer les resultats j'ai essayé d'augmenter la taille des images en entrée de vgg16 de 280 à 500 dans le notebook : VGG16-amélioration-test-1

VGG16 : clustering, score ARI : 0.1360
      classification, accuracy : 53.33%
 
Bien que cela prenne plus de temps les scores des différents tests ont diminués.

Je n'ai pas le temps d'aller plus loins dans le projet. 

Voici les étapes qui me reste à faire : 

- améliorer un peu l'extraction de feature pour le texte en testant d'autres modèles comme BERT et USE.
- améliorer beaucoup l'extraction de feature pour les images en testant d'autres modèles de transfert learning ou en réglant les hyperparamètres du modèle VGG16 ou mobile-net.
- réunir les features des images et des textes dans un seul dataframe et ajouter la catégorie. 
- faire un test de clustering et conclure, si le score API est supérieur à 0.6 l'étude de faisabilité sera positive.
- utiliser une API pour augmenter les données et pouvoir mieux entrainer les modèles.


      




