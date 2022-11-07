---
title: Projets
---

Types de projets
----------------

Il y a deux types de projets :

Type                | Description
--------------------| ---------------------------------------------------------
Projet d'équipe     | La gestion des utilisateurs est activée
Projet personel     | Projet qui appartient à une seule personne, il n'y a pas de gestion d'utilisateurs

- Seulement les administrateurs et les gestionnaires peuvent créer des projets d'équipe.
- Les projets privés peuvent être créé par tout le monde.

Créer des projets multi-utilisateurs
------------------------------------

- Seuls les administrateurs et les gestionnaires de projets peuvent créer ce type de projets
- La gestion des utilisateurs est disponible

Depuis le tableau de bord, cliquez sur le lien **Nouveau projet** :

![Création d'un projet](/images/v1/fr/new-project.png)

C'est vraiment très simple, il vous suffit de trouver un nom pour votre projet !

Créer un projet personel
------------------------

- Tout le monde peut créer un projet privé (sauf si désactivé par l'administrateur)
- Il n'y a **pas** de gestion des utilisateurs
- Seuls le propriétaire et les administrateurs peuvent accéder au projet

Depuis le tableau principal, cliquez sur le lien **Nouveau projet privé**.

Créer un projet depuis un autre projet
--------------------------------------

Lorsque vous créez un nouveau projet, vous pouvez choisir de dupliquer
les propriétés d'un projet existant :

- Permissions
- Catégories
- Actions
- Swimlanes
- Tâches

Modifier des projets
--------------------

Les projets peuvent être renommés et désactivés à tout moment.

Pour renommer un projet, il suffit de cliquer sur le lien « Modifier un
projet » sur la gauche.

![Modification de projets](/images/v1/fr/project-edition.png)

- Les dates de début et de fin sont utilisées pour créer le diagramme de Gantt du projet
- La description est visible en infobulle sur le tableau et sur la page qui liste les projets
- Les administrateurs et administrateurs de projets peuvent convertir un projet privé en projet multi-utilisateur en décochant la case « Projet privé ».
- Vous pouvez également convertir un projet multi-utilisateur en projet privé.

Remarque : quand vous rendez un projet privé, tous les utilisateurs existants auront accès au projet. Ajustez la liste des utilisateurs selon vos besoins.

Supprimer un projet
-------------------

Pour supprimer un projet, vous devez être gestionnaire du projet ou administrateur.

Aller dans les **Préférences du projet**, depuis le menu à gauche, en bas, choisissez **Supprimer**.

![Suppression d'un projet](/images/v1/fr/project-remove.png)

Supprimer un projet, supprime également toutes les tâches qui appartiennent à ce projet.

Permissions des projets
-----------------------

Chaque projet est isolé des autres. Les accès au projet doivent être autorisés par le chef de projet.

Chaque utilisateur et chaque groupe peut avoir un rôle différent. Il y a 3 types de rôles pour les projets :

- Chef de projet
- Membre du projet
- Visualiseur

L'assignation des rôles est disponible depuis **Paramètres du projet > Permissions**:

![Permissions des projets](/images/v1/fr/project-permissions.png)

Les projets privés ne peuvent pas définir de permissions.

Rôles personnalisés pour les projets
------------------------------------

Vous pouvez créer des rôles personnalisés pour les projets afin
d'appliquer des restrictions spécifiques sur les personnes qui
appartiennent à ce rôle. Ces rôles personnalisés sont définis pour
chaque projet.

Un rôle personnalisé hérite du rôle « Membre du projet ». Par exemple,
vous pouvez créer un rôle personnalisé pour forcer quelqu'un à suivre un
process. Vous pourriez avoir un groupe de gens qui sont autorisés
seulement à déplacer des tâches entre les colonnes « Travail en cours »
et « Terminé ».

### Liste des restrictions

- Restrictions au niveau du projet :
    - La création de tâches n'est pas permise
    - Ouvrir ou fermer une tâche n'est pas permise
    - Déplacer une tâche n'est pas autorisé
- Restrictions au niveau des colonnes :
    - La création de tâches est autorisée ou bloquée pour une colonne
        spécifique
    - L'ouverture ou la fermeture de tâche est autorisée ou bloquée
        pour une colonne spécifique
- Déplacer une tâche seulement entre les colonnes spécifiées

### Configuration

#### 1) Créer un rôle personnalisé

Depuis les réglages du projet, cliquez dans le menu à gauche sur **Rôles
personnalisés** et en haut de la page sur **Ajouter un nouveau rôle
personnalisé**.

![Créer un rôle personnalisé](/images/v1/fr/new_custom_role.png)

Donnez un nom au rôle et soumettez le formulaire.

#### 2) Ajouter une restriction au rôle

Il y a plusieurs sortes de restrictions :

- Restrictions au niveau du projet
- Restriction sur le déplacement des tâches entre les colonnes
- Restrictions sur les colonnes

Vous pouvez cliquer sur le menu déroulant pour ajouter une nouvelle
restriction :

![Ajouter une restriction au rôle](/images/v1/fr/add_new_restriction.png)

#### 3) Liste des restrictions

![Exemple de restrictions](/images/v1/fr/example-restrictions.png)

Par exemple, ce rôle est capable de créer des tâches seulement dans la
colonne « Backlog » et de déplacer des tâches entre les colonnes « Ready
» et « Work in progress ».

#### 4) Assigner le rôle à quelqu'un

Allez dans la section **Permissions** dans le menu sur la gauche et
assignez le rôle personnalisé à l'utilisateur.

![Assigner un rôle](/images/v1/fr/custom_roles.png)

### Exemples

#### Autoriser les gens à créer des tâches uniquement dans certaines colonnes

![Restriction pour créer des tâches](/images/v1/fr/example-restriction-task-creation.png)

- Les utilisateurs qui appartiennent à ce rôle seront capables de
    créer des tâches seulement dans la colonne « Backlog ».
- La combinaison des deux règles est importante, sinon cela ne
    fonctionnera pas.

#### Autoriser les gens à changer le statut des tâches uniquement dans certaines colonnes

![Restriction pour changer le statut](/images/v1/fr/example-restriction-task-status.png)

- Les utilisateurs qui appartiennent à ce rôle seront capables de
    change le statut des tâches seulement dans la colonne « Backlog ».
- Les tâches qui possèdent le statut ouvert sont visibles sur le
    tableau alors que celles qui ont le statut fermé ne sont pas
    visibles.

#### Ne pas autoriser les gens à changer le statut des tâches dans une colonne spécifique

![Restriction pour changer le status dans une colonne spécifique](/images/v1/fr/example-restriction-task-status-blocked.png)

Les utilisateurs qui appartiennent à ce rôle ne seront pas capables de
changer le statut des tâches dans la colonne « Done ». Par contre, cela
reste possible dans les autres colonnes.

#### Autoriser les gens à déplacer des tâches seulement entre certaines colonnes

![Restriction pour déplacer des tâches](/images/v1/fr/example-restriction-task-drag-and-drop.png)

Les utilisateurs qui appartiennent à ce rôle seront capables de déplacer
les tâches seulement entre les colonnes « Ready » et « Work in progress
».

Partager des tableaux et des tâches
-----------------------------------

Par défaut, les tableaux sont privés, mais il est possible de rendre un
tableau public.

Un tableau public ne **peut pas être modifié, il est en lecture seule**.
Son accès est protégé par un jeton aléatoire, seules les personnes qui
ont la bonne URL peuvent voir le tableau.

Les tableaux publics sont automatiquement réactualisés toutes les
minutes. Les détails des tâches sont disponibles en lecture seule.

Exemples d'utilisation :

- Partager son tableau avec quelqu'un qui ne fait pas partie de votre organisation / entreprise / groupe
- Afficher le tableau sur un grand écran dans votre bureau

### Activer l'accès public

Choisissez votre projet, puis cliquez sur « Accès public » et enfin sur
le bouton « Activer l'accès public ».

![Activer l'accès public](/images/v1/fr/project-enable-sharing.png)

Lorsque l'accès public est activé, plusieurs liens sont créés :

- Affichage du tableau public
- Lien de souscription au fil RSS
- Lien d'abonnement à iCalendar

![Désactiver l'accès public](/images/v1/fr/project-disable-sharing.png)

Vous pouvez désactiver l'accès public à tout moment.

À chaque fois que vous activez ou désactivez l'accès public, un nouveau jeton aléatoire est créé. **Les liens précédents ne fonctionneront pas**.
