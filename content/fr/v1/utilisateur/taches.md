---
title: Tâches
toc: true
menu:
    main:
        parent: Guide utilisateur
---

Créer des tâches
----------------

Depuis le tableau, cliquez sur le signe plus + à côté du nom de la
colonne :

![Création de tâches](/images/v1/fr/task-creation-board.png)

Le formulaire de création de tâche apparaît :

![Formulaire de création](/images/v1/fr/task-creation-form.png)

Le seul champ obligatoire est le titre.

Description des champs :

- **Titre** : le titre de votre tâche, tel qu'il sera affiché sur le tableau.
- **Description** : vous permet d'ajouter davantage d'informations sur la tâche. Le contenu peut être écrit en Markdown.
- **Libellés**: Liste de libellés associés à la tâche.
- **Créer une autre tâche** : cochez cette case si vous souhaitez créer une tâche similaire (les champs seront pré-remplis).
- **Assigné** : la personne qui va travailler sur la tâche.
- **Catégorie** : une seule catégorie peut être assignée à une tâche.
- **Colonne** : la colonne dans laquelle la tâche sera créée. La tâche sera positionnée en bas de cette colonne.
- **Couleur** : Choisissez la couleur de la carte.
- **Complexité** : utilisée dans la gestion de projet agile (Scrum), la complexité des points d'étape est un nombre qui montre à l'équipe le degré de difficulté de l'avancement du projet. Les utilisateurs se servent souvent des suites de Fibonacci.
- **Référence** : Identifiant externe, par exemple cela peut-être un numéro de ticket qui vient d'un système externe.
- **Estimation originale** : estimation du nombre d'heures nécessaire pour terminer les tâches.
- **Date d'échéance** : les tâches dont la date d'échéance est dépassée auront une date d'échéance en rouge et les dates suivantes seront en noir dans le tableau. Plusieurs formats de date sont acceptés, outre le sélecteur de date.

Avec le lien d'aperçu (« Prévisualiser »), vous pouvez voir la description de la tâche convertie depuis la syntaxe Markdown.

Vous créer une tâche de plusieurs manières :

- Avec l'icône avec le signe plus sur le board
- Avec le raccourci clavier "n"
- Depuis le menu déroulant en haut à gauche

Dupliquer et déplacer des tâches
--------------------------------

### Dupliquer une tâche dans le même projet

Allez à la vue par tâche et choisissez **Dupliquer** sur la gauche.

![Dupliquer une tâche dans le même projet](/images/v1/fr/task-duplication.png)

Une nouvelle tâche sera créée avec les mêmes propriétés que celles de la
tâche originale.

### Dupliquer une tâche vers un autre projet

Allez à la vue par tâches et choisissez **Dupliquer dans un autre
projet**.

![Dupliquer une tâche vers un autre projet](/images/v1/fr/task-duplication-another-project.png)

Seuls les projets dont vous êtes membre apparaîtront dans le menu
déroulant.

Avant de copier les tâches, Kanboard vous demandera les propriétés de la
destination qui ne sont pas communes entre les projets source et
destination.

Vous devez essentiellement définir :

- La swimlane de destination
- La colonne
- La catégorie
- L'assigné

### Déplacer une tâche vers un autre projet

Allez à la vue par tâches et choisissez **Déplacer vers un autre
projet**.

Déplacer vers un autre projet est semblable à l'opération de
duplication, vous devez choisir les nouvelles propriétés de la tâche.

### Liste des champs dupliqués

Voici la liste des champs dupliqués :

- `title`
- `description`
- `date_due`
- `color_id`
- `project_id`
- `column_id`
- `owner_id`
- `score`
- `category_id`
- `time_estimated`
- `swimlane_id`
- `recurrence_status`
- `recurrence_trigger`
- `recurrence_factor`
- `recurrence_timeframe`
- `recurrence_basedate`

Fermer des tâches
-----------------

Quand une tâche est fermée, elle n'est plus visible sur le tableau.

Toutefois, vous pouvez toujours accéder à la liste des tâches closes en
utilisant la requête **status:closed** dans un formulaire de recherche,
ou bien choisissez simplement **Tâches fermées** dans le menu déroulant
des filtres.

Il existe deux façons différentes de fermer une tâche, depuis le menu
déroulant des tâches sur le tableau :

![Menu pour fermer une tâche](/images/v1/fr/menu-close-task.png)

ou bien depuis la barre latérale dans la vue détaillée des tâches

![Fermer une tâche depuis la barre latérale](/images/v1/fr/closing-tasks.png)

Remarque : quand vous fermez une tâche, toutes les sous-tâches qui ne sont pas achevées verront leur statut passer à "Terminé".

Liens entre les tâches
----------------------

Les tâches peuvent être liées ensemble avec des relations prédéfinies.

![Liens entre les tâches](/images/v1/fr/internal-task-links.png)

Il est également possible de connecter des tâches entre plusieurs
projets.

Les relations établies par défaut sont les suivantes :

- **fait référence à**
- **bloque** | **est bloqué par**
- **est bloqué par** | **bloque**
- **duplique** | **est dupliqué par**
- **est dupliqué par** | **duplique**
- **est un enfant de** | **est un parent de**
- **est un parent de** | **est un enfant de**
- **vise les étapes importantes** | **est une étape importante de**
- **est une étape importante de** | **vise les étapes importantes**
- **correctifs** | **est réglé par**
- **est réglé par** | **correctifs**

Ces étiquettes peuvent être modifiées dans les paramètres de l'application.

Transitions entre les tâches
----------------------------

Les transitions enregistrent tous les mouvements des tâches entre les
colonnes

![Transitions entre les tâches](/images/v1/fr/task-transitions.png)

Depuis la page détaillée de la tâche, vous pouvez accéder à ces
informations:

- Date de l'action
- Colonne d'origine
- Colonne de destination
- Exécutant (Pour l'utilisateur qui a déplacé la tâche)
- Temps passé sur la colonne d'origine

Tâches récurrentes
------------------

Pour convenir à ma méthodologie de Kanban, les tâches récurrentes ne
sont pas basées sur une date mais sur les évènements du tableau.

- Les tâches récurrentes sont dupliquées dans la première colonne du
    tableau quand les évènements sélectionnés se produisent
- La date d'échéance peut être automatiquement recalculée
- Chaque tâche enregistre l'identifiant de tâche de la tâche parente
    qui l'a créée et la tâche enfant qui a été créée.

### Configuration

Allez à la page de vue par tâches ou utilisez le menu déroulant du
tableau, puis choisissez **Modifier la récurrence**.

![Tâches récurrentes](/images/v1/fr/recurring-tasks.png)

il existe trois façons de déclencher la création d'une nouvelle tâche
récurrente :

- Déplacer une tâche depuis la première colonne
- Déplacer une tâche vers la dernière colonne
- Fermer la tâche

Les dates d'échéance, si elles concernent la tâche courante, peuvent
être recalculées en fonction d'un nombre donné de jours, mois ou années.
La date de base pour le calcul de la nouvelle date d'échéance peut être
soit la date d'échéance existante, soit la date de l'action.

Ajouter des captures d'écran
----------------------------

Vous pouvez copier-coller des images directement dans Kanboard pour
gagner du temps. Ces images sont mises en ligne en tant que pièces
jointes à une tâche.

Ceci est particulièrement utile pour prendre des captures d'écran, quand
il faut par exemple décrire un problème.

Vous pouvez ajouter directement des captures depuis le tableau en
cliquant sur le menu déroulant ou sur la page de visualisation des
tâches.

![Ajouter une capture d'écran](/images/v1/fr/dropdown-screenshot.png)

Pour ajouter une nouvelle image, prenez votre capture et collez-la avec CTRL+V ou Command+V:

![Ajouter une capture d'écran](/images/v1/fr/task-screenshot.png)

Avec macOS, vous pouvez utiliser les raccourcis suivants pour prendre
des captures d'écran :

- `Command-Control-Maj-3` : prend une capture de l'écran entier et l'enregistre dans le presse-papiers
- `Command-Control-Maj-4`, puis choix d'une zone : prend une capture  d'une zone définie et l'enregistre dans le presse-papiers
- `Command-Control-Maj-4`, puis touche espace, puis clic sur une fenêtre : prend une capture d'une fenêtre et l'enregistre dans le presse-papiers

Il existe plusieurs applications tierces qui peuvent être utilisées pour
prendre des captures d'écran avec des annotations et un choix de formes.

**Remarque : cette fonctionnalité n'est pas disponible sur tous les
navigateurs.** Elle n'existe pas pour Safari en raison de ce bug :
<https://bugs.webkit.org/show_bug.cgi?id=49141>

Statistiques des tâches
-----------------------

Chaque tâche possède une section analytique accessible à partir du menu
à gauche dans la page des tâches

### Lead et cycle time

![Lead et cycle time](/images/v1/fr/task-lead-cycle-time.png)

- Le lead time est la durée entre la création de la tâche et son achèvement (tâche fermée).
- Le cycle time est la durée entre la date de début et l'achèvement.
- Si la tâche n'est pas fermée, l'heure courante est utilisée à la place de la date d'achèvement.
- Si la date de départ n'est pas spécifiée, le cycle time n'est pas calculé.

Remarque : vous pouvez configurer une action pour définir automatiquement que la date de départ sera le moment où vous déplacez une tâche vers une colonne de votre choix

### Temps passé dans chaque colonne

![Temps passé dans chaque colonne](/images/v1/fr/time-into-each-column.png)

- Ce graphique montre le temps total passé dans chaque colonne pour la tâche
- Le temps passé est calculé jusqu'à ce que la tâche soit fermée
