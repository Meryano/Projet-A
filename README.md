# Projet
-
Ce projet consiste à faire un code Arduino permettant de reconnaitre les gestes Oui et Non d'un utilsateur auquel on pose trois questions.
Pour le faire, on suit trois étapes que sont l'entrainement du modèle avec TensorFlow, l'intégration du modèle avec Arduino et l'implémentation des questions.
On téléverse le code "generate_data_to_train.ino" dans notre carte Arduino. On utilise git bash pour le code python "serial_data_to_csv". Dans git bash on utilise la commande "nano serial_data_to_csv.py" pour vérifier que le port de la carte est bien renseigné, puis la commande "py serial_data_to_csv" pour effectuer les gestes. 
On effectue 10 gestes "yes". Un fichier "output" apparait dans nos dossiers qu'on renomme en "yes". On refait la meme commande avec des gestes "no". Un autre fichier "output" apparait et on le renomme en "no". Ceci nous permet d'avoir nos données "yes" et "no" pour entrainer le modèel.
Cette étape réalisée, nous allons dans googgle colab pour l'entrainement. On ouvre le fichier "Tiny ML for Arduino" pour ce faire. Dans "content", on ajoute nos fichiers excel "yes" et "no". On exécute ensuite le code et après exécution complète un fichier "model.h" apparait qu'on télécharge et qu'on ajoute dans un dossier "classify_imu".
Le dossier "classify_imu" contient deux éléments: le fichier "model.h" et le code arduino "classify_inu.ino". On ouvre ce dernier code arduino et nous vérifions que le code fonctionne et détecte bien les gestes "yes" et "no". Nous allons ensuite modifier ce code pour réaliser notre projet

Explication du code Arduino:
  -On commence par ajouter les bibliothèques nécessaires à notre projet
  -On ajoute le fichier model.h
  -Dans la fonction void setup on fait des Serialprintln pour:
      -Afficher un message quand la carte Arduino est détectée
      -Poser les trois questions
  -A la fin du code on fait des if pour faire un test sur la réponse de l'utilisateur
  -Le code du if est une sturcture de controle pour interpreter les sorties de notre modèle. 
  -Si "tflOutputTensor->data.f[1]" est inférieur à tflOutputTensor->data.f[2] alors il imprime "mauvaise reponse" sinon il imprime "bonne réponse"
En somme, il s'agit d'un projet de reconnaissance gestuelle TensorFlowLite sur une carte Arduino Nano 33BLE. Le code attend un mouvement détecté par l'accéléromètre; Il capture les données d'accélération et de gyroscope pour les normaliser et les utiliser en entrée pour le modèle TensorFlow Lite. Il classifie deux gestes que sont "yes" et "no" et sort une probabilité pour chaque classe. Il compare les probabilités et en fonction de cette comparaison affiche s'il s'agit d'une bonne ou mauvaise réponse.
PS: Je n'ai pas pu tester le fonctionnement complet du code sur la carte Arduino. Le port de la carte s'est arraché lors de mes tests et il faudrait que je la soude
  
