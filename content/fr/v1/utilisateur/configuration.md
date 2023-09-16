---
title: Configuration
toc: true
menu:
    main:
        parent: Guide utilisateur
---

Paramètres de l'application
---------------------------

Certains paramètres de l'application peuvent être modifiés sur la page
des paramètres. Seuls les administrateurs peuvent modifier ces
paramètres.

Allez au menu **Paramètres**, puis choisissez **Paramètres de
l'application** sur la gauche.

![Paramètres de l'application](/images/v1/fr/application-settings.png)

### URL de l'application

Ce paramètre est utilisé pour les notifications par mail. Le pied de
page du mail contiendra un lien vers la tâche du Kanboard.

### Langue

La langue de l'application peut être modifiée à tout moment. Elle sera
définie pour tous les utilisateurs.

### Fuseau horaire

Par défaut, Kanboard utilise le TUC comme fuseau horaire, mais vous pouvez définir votre propre fuseau horaire. La liste contient tous les fuseaux horaires pris en charge par votre serveur web.

### Format de date

Format d'entrée utilisé pour les champs de saisie de date, par exemple la date d'échéance pour les tâches.

Kanboard propose 4 différents formats:

- `JJ/MM/AAAA`
- `MM/JJ/AAAA` (par défaut)
- `AAAA/MM/JJ`
- `MM.JJ.AAAA`

Le format [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) est toujours accepté (`AAAA-MM-JJ` ou `AAAA_MM_JJ`).

### Feuille de style personnalisée

Écrivez votre propre CSS pour remplacer ou améliorer le style par défaut de Kanboard.

Paramètres du projet
--------------------

Aller dans le menu **Préférences**; puis choisissez **Paramètres du
projet** sur la gauche

![Paramètres du projet](/images/v1/fr/project-settings.png)

### Colonnes par défaut pour les nouveaux projets

Vous pouvez changer le nom des colonnes par défaut. C'est utile si vous
créez toujours des projets comprenant les même colonnes

Chaque nom de colonne doit être séparé par une virgule.

Par défaut, Kanboard utilise les noms de colonne suivants : en attente,
prêt, en cours, terminé.

### Catégories par défaut pour les nouveaux projets

Les catégories ne sont pas globales à l'application mais rattachées à un
projet. Chaque projet peut avoir plusieurs catégories.

De plus, si vous créez toujours la même catégorie pour tous vos projets,
vous pouvez définir ici la liste des catégories à créer automatiquement

### Autoriser une seule sous-tâche en cours à la fois pour un utilisateur

Lorsque cette option est sélectionnée, un utilisateur ne peut travailler
que sur une seule sous-tâche à la fois

Si une autre sous-tâche possède le statut « en cours », l'utilisateur
verra cette boite de dialogue :

![Restrictions](/images/v1/fr/subtask-user-restriction.png)

### Déclencher automatiquement le suivi du temps pour les sous-tâches

- Si activé, lorsque le statut d'une sous-tâche devient « en cours », le chrono va démarrer automatiquement
- Désactivez cette option si vous n'utilisez pas le suivi du temps.

### Inclure les tâches fermées dans le diagramme de flux cumulé

- Si l'option est activée, les tâches fermées seront incluses dans le diagramme de flux cumulé
- Si l'option est désactivée, seules les tâches ouvertes seront incluses dans le diagramme de flux cumulé
- Cette option affecte la colonne "total" de la table `project_daily_column_stats`

Paramètres du tableau
---------------------

Allez dans le menu **Paramètres** puis choisissez **Paramètres du tableau** sur la gauche

![Paramètres du tableau](/images/v1/fr/board-settings.png)

### Mise en avant d'une tâche

Cette fonctionnalité affiche une ombre autour de la tâche lorsqu'une tâche à été déplacée récemment.

Initialisez la fonctionnalité à 0 pour la désactiver, par défaut 2 jours (172800 secondes).

Toutes les tâches qui ont été déplacées depuis 2 jours seront entourées d'une ombre.

### Intervalle pour rafraîchir un tableau public

Lorsque vous partagez un tableau, la page sera, par défaut, automatiquement rafraîchie toutes les 60 secondes.

### Intervalle pour rafraîchir un tableau privé

Lorsque votre navigateur web est ouvert sur un tableau, Kanboard vérifie toutes les 10 secondes si quelque chose à été modifié par un autre utilisateur.

Techniquement, ce processus est fait par Ajax polling.

Paramètres du calendrier
------------------------

Allez au menu **Paramètres**, puis choisissez **Paramètres du calendrier** sur la gauche.

![Paramètres du calendrier](/images/v1/fr/calendar-settings.png)

il existe deux calendriers distincts dans Kanboard :

- le calendrier du projet
- le calendrier de l'utilisateur, disponible dans le tableau de bord

### Le calendrier du projet

Ce calendrier affiche les tâches avec les dates d'échéance et les tâches
selon leur date de création ou de début.

#### Afficher les tâches selon leur date de création

- La date de début d'un évènement du calendrier est la date de
    création de la tâche.
- la date de fin de l'évènement est la date d'achèvement de la tâche.

#### Afficher les tâches selon leur date de début

- La date de début d'un évènement du calendrier est la date du
    démarrage effectif de la tâche.
- Cette date ne peut pas être définie manuellement.
- La date de fin de l'évènement est la date de l'achèvement de la
    tâche.
- S'il n'existe pas de date de début la tâche ne figurera pas sur le
    calendrier .

### Calendrier de l'utilisateur

Ce calendrier n'affiche que les tâches assignées à l'utilisateur et de
façon facultative des informations sur les sous-tâches.

#### Afficher les sous-tâches selon le suivi du temps passé

- Affiche les sous-tâches dans le calendrier d'après les informations
    recueillies dans l afeuille de suivi du temps.
- Le croisement des données avec l'emploi du temps de l'utilisateur
    est également calculé.

#### Afficher les estimations des sous-tâches (anticipation sur le travail à venir)

- Affiche l'estimation du travail à venir pour les sous-tâches qui ont
    le statut « à faire » et avec une valeur définie à « estimé ».

Paramètres des liens
--------------------

Les relations entre les tâches peuvent être modifiées depuis les paramètres de l'application (**Paramètres > Paramètres des liens**)

![Libellés des liens](/images/v1/fr/link-labels.png)

Chaque nom du libellé peut avoir un nom du libellé opposé.

Si il n'y a pas d'opposé, le nom du libellé sera considéré comme étant bidirectionnel.

![Creation d'un libellé](/images/v1/fr/link-label-creation.png)
