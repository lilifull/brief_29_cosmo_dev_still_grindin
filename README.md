# brief_29_cosmo_dev_still_grindin

Compte rendu de l'étude de faisabilité : 

Feature extraction Text : 

Dans un premier temps j'ai nettoyé le texte, cette étape est visible dans le notebook : Nettoyage du texte.

Puis j'ai testé 4 techniques afin de créer de nouvelles features à partir du texte : bag of words (count et Tf-idf) et Word2Vec (un modèle entrainé sur les données du projet et un modèle pré-entrainé de google). Pour pouvoir comparer les modèles entre eux, je compare l'accuracy d'un modèle de classification SVC sur les feautres crées les différentes méthodes.

Les résultats de bag of words sont disponibles dans le notebook : Bag of words.

Les résultats sont les suivants : 
Accuracy avec la méthode Count et le colonne description : 80.48%
Accuracy avec la méthode Tf-idf et le colonne description : 92.38%
Accuracy avec la méthode Count et le colonne product name :  89.52%
Accuracy avec la méthode Tf-idf et le colonne product name : 91.43%
Accuracy avec la méthode Count et le colonne qui associe description et product name : 88.1%
Accuracy avec la méthode Tf-idf et le colonne qui associe description et product name : 94.29%

Nous pouvons en conclure que la méthode tf-idf donnent les meilleurs résultats avec la colonne qui associe la description et le product name.

Les résultats pour Word2Vec sont disponibles dans le notebook suivant : Word2Vec extraction

J'ai seulement utiliser la colonne qui associe description et product name car ces celle qui donne le plus d'information et donne de mailleurs résultats.

Les résultats sont les suivants :
Accuracy avec le modèle word2vec entrainé sur les données du projet : 45.71%
Accuracy avec le modèle word2vec-google-news-300 : 93.81%

Si on utilise un modèle pré-entrainé de word2vec il donne de très bons résultats aussi.

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
      
Les meilleurs résultats sont avec le transfert learning et le modèle VGG16, par contre il est assez long à extraitre les features, mobile-net est plus rapide mais donne des résultats en dessous. Cependant les résultats sont un trop bas pour toutes le techniques, ils sont à améliorer pour pouvoir utiliser les features des images pour faire de bonnes classifications.

Clustering : 


      




