Modèle du domaine
=================

Liste des entity
----------------

L'analyse des besoins concernant cette application nous a permis de définir ces différentes classes :

+-------------------+--------------------------------------------------------------------+
| Nom               | Fonction                                                           |
+===================+====================================================================+
| Client            | Client de predict'if                                               |
+-------------------+--------------------------------------------------------------------+
| Employe           | Employe de Predict'if                                              |
+-------------------+--------------------------------------------------------------------+
| Medium            | Medium fictif                                                      |
+-------------------+--------------------------------------------------------------------+
| Horoscope         | Horoscope contenant un ensemble de 3 prédictions de type différent |
+-------------------+--------------------------------------------------------------------+
| Prédiction        | Classe abstraite qui sert de base pour les 3 types de prédictions  |
+-------------------+--------------------------------------------------------------------+
| PrédictionAmour   | Prédiction de catégorie Amour,                                     |
|                   | indique un signe partenaire                                        |
+-------------------+--------------------------------------------------------------------+
| PrédictionTravail | Prédiction de catégorie Travail                                    |
+-------------------+--------------------------------------------------------------------+
| PrédictionSante   | Prediction de catégorie Santé, contient un conseil pour le client  |
+-------------------+--------------------------------------------------------------------+
| Signe             | Réprésente un signe astrologique simplifié                         |
|                   | (correspond à un mois de l'année)                                  |
+-------------------+--------------------------------------------------------------------+

L'ensemble des classes dispose d'une méthode ``toString()`` pour permettre son affichage.

Diagramme de Classes
--------------------

.. only:: html

	Le diagramme de classes ci-dessous reprend les différentes classes présentés ci-dessus.

	- Télécharger le document du modèle UML : :download:`UML <uml.pdf>`


