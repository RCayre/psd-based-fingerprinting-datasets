# Jeux de données pour le fingerprinting basé sur la DSP

Ce dépôt contient les différents jeux de données utilisés pour les expériences de l'article "Fingerprinting basé sur la DSP contre le spoofing dans les réseaux sans-fil".

## Signaux

Signaux et sorties démodulées utilisées pour l'article.
Sauf indication contraire, les données proviennent d'un LimeSDR-Mini. Chaque capture a été réalisée avec une fréquence d'échantillonnage de 2MHz.

Pour chaque jeu de signaux, chaque dossier correspond à une trame reçue et isolée. Il contient les fichiers suivants:

* **iq.csv** : contient une suite d'entiers signés, un par ligne, correspondant aux échantillons IQ reçus. Une ligne sur deux correspond aux échantillons en phase (I), les autres correspondant aux échantillons en quadrature de phase (Q)
* **iq\_data.csv** : contient une sous-partie de **iq.csv**, correspondant aux échantillons utilisés pour démoduler la trame
* **iq\_start.csv** : contains a subset of **iq.csv**, correspondant aux échantillons précédant les données de la trame proprement dites
* **raw.txt** : contient la sortie brute du démodulateur


Les différents jeux inclus sont les suivants :

* **experience\_B1.tar.gz** contient les données utilisées pour la première partie de la première expérience, avec deux émetteurs BLE dont on reçoit les signaux depuis deux positions différentes
* **experience\_B2.tar.gz** contient les données utilisées pour la seconde partie de la première expérience, avec trois émetteurs BLE
* **experience\_C.tar.gz** contient les données utilisées pour la deuxième expérience, avec plusieurs émetteurs BLE différents
* **18NRF52\_hackrf.zip** and **18NRF52_lime.zip** contiennent les données de 18 émetteurs BLE identiques, reçues respectivement avec un HackRF One et un LimeSDR-Mini
* **20Xbee\_Lime.zip** contient les données de 20 émetteurs Zigbee identiques


## Résultats de l'algorithme

Les fichiers **databases\_\<experiment\>.tar.gz** contiennent les resultats de l'algorithme de détection de communauté ainsi que les DSPs des différents signaux des fichiers ci-dessus.

Pour chaque jeu de données, vous trouverez quatre fichiers au format CSV:

* **db\_\<experiment\>\_clusters.csv** : contient une liste de noms de fichiers associés chacun avec un numéro de cluster; chaque ligne contient d'abord le nom du fichier contenant le signal utilisé, puis le numéro de la communauté reconnue, séparés par une virgule
* **db\_\<experiment\>\_links.csv** : contient la matrice de similarité produite par notre algorithme pour le jeu de données concerné; la première ligne et la première colonne contiennent les noms des fichiers contenant les signaux
* **db\_\<experiment\>\_psds.csv** : contient les différentes DSP obtenues dans le jeu de données; chaque ligne correspond à la DSP d'un signal, dans le même ordre que les fichiers précédents
* **db\_\<experiment\>\_stats.csv** : contient les statistiques calculées sur les différentes communautés identifiées dans le jeu de données; chaque ligne contient un numéro de communauté, la moyenne des similarités moyennes avec d'autres membres de la communauté (voir l'article, équations 3 et 4), ainsi que l'écart type des ces similarités moyennes, séparés par des virgules
