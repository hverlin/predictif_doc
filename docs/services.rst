Description des services
========================

Méthodes de classe ``Services``
-------------------------------

.. tabularcolumns:: |p{6cm}|p{4cm}|p{5cm}|
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
| creerSigne(Signe signe)                                     | void                    | Permet d'insérer un signe dans la base de données      |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getClientById(long id)                                      | Client                  | Récupère un client grâce à son id                      |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getEmployeById(long id)                                     | Employe                 | Récupère un employe grâce à son id                     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getSigneById(long id)                                       | Signe                   | Récupère un signe grâce à son id                       |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getPredictionById(long id)                                  | Prediction              | Récupère un prediction grâce à son id                  |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getHoroscopeById(long id)                                   | Horoscope               | Récupère un horoscope grâce à son id                   |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| getMediumById(long id)                                      | Medium                  | Récupère un medium grâce à son id                      |
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
| connexionEmploye(String identifiant, String mdp)            | Employe                 | Connexion d'un employé                                 |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+
| listerMediumsClient(Client client)                          | List<Medium>            | Liste tous les mediums d'un client                     |
+-------------------------------------------------------------+-------------------------+--------------------------------------------------------+



Exemples d'utilisation
----------------------

Créer un client
^^^^^^^^^^^^^^^

.. tip:: La class `Calendar`_ est utilisée pour la gestion des dates.
.. _Calendar: http://docs.oracle.com/javase/7/docs/api/java/util/Calendar.html 


.. code-block:: java
	
	// on imagine que le client est né aujourd'hui
	Calendar DateNaissance = Calendar.getInstance();
	Client c = new Client("Nom", "Prénom","Mr", DateNaissance, 
		"rue de nullepart, 69 100 If_laville", "client@if.fr","06 26 30 29 ");
	services.creerClient(c);

Connexion d'un employé
^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java

    Employe employe = services.connexionEmploye(identifiant, mdp);


Lister tous les clients d'un employé
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java
    
    Employe employe = services.connexionEmploye(identifiant, mdp);

    for(Client element : employe.getClients() )
    {
        System.out.println(element);
    }
    // On peut vérifier qu'il a bien des clients
    if(choices.isEmpty())
    {
        System.out.println("Vous n'avez pas de clients !");
    }

.. tip:: La service *services.listerHistoriqueClient(client)* permet de récupérer un historique préformaté. Pour plus de souplesse, vous pouvez directement utiliser la liste des horoscopes du client, ou encore utiliser les attributs de la classe *horoscope*. 


Afficher l'historique des prédictions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java

	// Première Méthode
	List<Horoscope> historique = services.listerHistoriqueClient(client);

	//2ème méthode
    boolean vide = true;
    for(Horoscope h : client.horoscopes)				
    {
        if(h != null)
        {
            vide = false;
            System.out.println("_____________");
            System.out.println("\n\nLe "+
            h.getDateHoroscope().get(Calendar.DAY_OF_MONTH)+ " "
			+ ""+h.getDateHoroscope().getDisplayName(
			Calendar.MONTH,Calendar.LONG,Locale.FRANCE)+""
			+ " "+h.getDateHoroscope().get(Calendar.YEAR));
            System.out.println(h);
            System.out.println("\n\n By "+h.getNomMedium());
            System.out.println("_____________");
        }
    }
    if(vide)
    {
        System.out.println("Historique vide");
    }	


Ajouter une prédiction à un horoscope
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java
	
	// on liste une catégorie de prédictions
    List<PredictionAmour> pAmour = services.listerPredictionAmours();
    Horoscope horoscope = new horoscope();
    horoscope.setAmour(pAmour.get(0)); // si on veut la première de la liste


Mettre la date de l'horoscope et l'ajouter à un client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: java

    Calendar date = Calendar.getInstance();
    horoscope.setDateHoroscope(date);                
    services.creerHoroscope(horoscope, client);