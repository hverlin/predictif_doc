Description des services
========================

Méthodes de classe services
---------------------------

+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| Méthode                                                     | Type de Retour          | Brève Description                                      |
+=============================================================+=========================+========================================================+
| creerClient(Client client)                                  | int                     | Permet d'insérer un client dans la base de données     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerEmploye(Employe employe)                               | void                    | Permet d'insérer un employé dans la base de données    |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerHoroscope(Horoscope horoscope, Client client)          | void                    | Permet d'insérer un horoscope dans la base de données, |
|                                                             |                         | et de l'attacher à un client.                          |
|                                                             |                         | Elle simule l'envoi du mail au client                  |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerMedium(Medium medium)                                  | void                    | Permet d'insérer un signe dans la base de données      |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerPredictionAmour(PredictionAmour predictionAmour)       | void                    | Permet d'insérer une prédiction de                     |
|                                                             |                         | type amour dans la base de données                     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerPredictionSante(PredictionSante predictionSante)       | void                    | Permet d'insérer une prédiction                        |
|                                                             |                         | de type santé dans la base de données                  |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerPredictionTravail(PredictionTravail predictionTravail) | void                    | Permet d'insérer une prédiction de type                |
|                                                             |                         | travail dans la base de données                        |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| creerSigne(Signe signe)                                     |                         | Permet d'insérer un signe dans la base de données      |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getClientById(long idClient)                                | Client                  | Récupère un client grâce à son id                      |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerClients()                                             | List<Client>            | Liste de toutes les clients de la base                 |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerHistoriqueClient(Client client)                       | List<Horoscope>         | Renvoie l'historique de l'horoscope d'un client        |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerMediums()                                             | List<Medium>            | Liste de tous les mediums de la base                   |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerMediumsClient(Client client)                          | List<Medium>            | Liste tous les mediums d'un client                     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerPredictionAmours()                                    | List<PredictionAmour>   | Liste de toutes les predictions amour de la base       |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerPredictionSantes()                                    | List<PredictionSante>   | Liste de toutes les predictions sante de la base       |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerPredictionTravails()                                  | List<PredictionTravail> | Liste de toutes les predictions travail de la base     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerSignes()                                              | List<Signe>             | Liste de toutes les signes de la base                  |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| updateEmp(Employe emp)                                      | void                    | Met à jour un employé dans la base                     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+


Exemples d'utilisation
----------------------

Créer un client
^^^^^^^^^^^^^^^

.. tip:: La class Calendar est utilisée pour la gestion des dates.

.. code-block:: java
	
	// on imagine que le client est né aujourd'hui
	Calendar DateNaissance = Calendar.getInstance();
	Client c = new Client("Nom", "Prénom","Mr", DateNaissance, 
			"rue de nullepart, 69 100 If_laville", "client@if.fr","06 26 30 29 ");
	services.creerClient(c);

Lister tous les clients de la base
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java
						
	List<Client> clients = services.listerClients();
	for(Client element : clients )
	{
	    System.out.println(element);
	}							

