---
title: Statistiques pour les projets
toc: true
menu:
    main:
        parent: Guide utilisateur
---

Chaque projet dispose d'une section analytique. En fonction de la façon
dont vous utilisez Kanboard, vous pourrez voir les rapports suivants :

Répartition des utilisateurs
----------------------------

![Repartition des utilisateurs](/images/v1/fr/user-repartition.png)

Ce graphique circulaire affiche le nombre de tâches assignées par
utilisateur.

Distribution des tâches
-----------------------

![Distribution des tâches](/images/v1/fr/task-distribution.png)

Ce graphique circulaire donne une vue d'ensemble du nombre de tâches
ouvertes par colonne.

Diagramme de flux cumulé
------------------------

![Diagramme de flux cumulé](/images/v1/fr/cfd.png)

- Ce graphique affiche le nombre de tâches de façon cumulée pour chaque colonne en fonction du temps passé.
- La légende montre l'ordre de la pile.
- Chaque jour, le nombre total de tâches est enregistré pour chaque colonne.
- Si vous souhaitez exclure les tâches terminées, modifiez les [paramètres du projet global]({{< relref "projets.md" >}}).

Remarque : il faut au moins deux jours de données pour que le graphique apparaisse.

Graphique d'avancement
----------------------

![Graphique d'avancement](/images/v1/fr/burndown-chart.png)

Un [graphique d'avancement](http://en.wikipedia.org/wiki/Burn_down_chart) est disponible pour chaque projet.

- Il s'agit de la représentation graphique du travail qui reste à faire en fonction du temps restant.
- Kanboard utilise la complexité des estimations d'achèvement pour créer le graphique.
- Chaque jour, la somme des estimations pour chaque colonne est calculée.

Temps moyen passé pour chaque colonne
-------------------------------------

![Temps moyen passé pour chaque colonne](/images/v1/fr/average-time-spent-into-each-column.png)

Ce graphique affiche le temps moyen passé pour chaque colonne pour les 1000 dernière tâches.

- Kanboard utilise les transitions entre tâches pour calculer les données.
- Le temps passé est calculé jusqu'à la fin de la tâche.

Temps moyen de Lead et Cycle
----------------------------

![Temps moyen de Lead et Cycle](/images/v1/fr/average-lead-cycle-time.png)

Ce graphique affiche le temps moyen de lead et cycle pour les 1000 dernières tâches au cours du temps.

- Le *lead time* est le temps passé entre la création de la tâche et sa date d'achèvement.
- Le *cycle time* est le temps passé entre la date de début spécifiée et la date d'achèvement de la tâche.
- Si la tâche n'est pas close, la date courante est utilisée à la place de la date d'achèvement.

Ces métriques sont calculées et enregistrées chaque jour pour l'ensemble du projet.
