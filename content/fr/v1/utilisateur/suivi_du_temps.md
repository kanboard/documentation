---
title: Suivi du temps
toc: true
menu:
    main:
        parent: Guide utilisateur
---

Les informations de la feuille de suivi du temps peuvent être définies au niveau des tâches ou des sous-tâches.

Suivi de temps des tâches
-------------------------

![Suivi de temps des tâches](/images/v1/fr/task-time-tracking.png)

Les tâches ont deux champs :

- Temps estimé.
- Temps passé.

Ces valeurs représentent des heures de travail et doivent être entrées manuellement.

Suivi de temps des sous-tâches
------------------------------

![Suivi de temps des sous-tâches](/images/v1/fr/subtask-time-tracking.png)

Les sous-tâches ont aussi les champs "temps passé" et "temps estimé".

Lorsque vous changez la valeur de ces champs, **le suivi des tâches est mis à jour automatiquement et devient la somme des sous-tâches**.

Kanboard enregistre le temps entre chaque changement de statut des sous-tâches dans une table séparée.

- Changer le statut de la sous-tâche de **À faire** à **En cours** marque le temps de début.
- Changer le statut de la sous-tâche de **En cours** à **À faire** marque le temps de fin, mais met également à jour le temps passé sur la sous-tâche et la tâche.

La répartition de tous les enregistrements est visible sur la page de la tâche :

![Feuille de temps](/images/v1/fr/task-timesheet.png)

Pour chaque sous-tâche, le chrono peut être arrêté/démarré à tout moment :

![Chrono](/images/v1/fr/subtask-timer.png)

- Le chrono ne dépend pas du statut de la sous-tâche.
- Chaque fois que vous démarrez le chrono, un nouvel enregistrement est créé dans la table de suivi des temps.
- Chaque fois que vous arrêtez le chrono, la date de fin est enregistrée dans la table de suivi des temps.
- Le temps passé est arrondi au quart d'heure le plus proche (seulement pour Kanboard < 1.0.32).
