---
title: Notifications
toc: true
menu:
    main:
        parent: Guide utilisateur
---

Kanboard est capable d'envoyer des notifications via différents canaux :

- Email
- Web (Liste de message non lus)

Vous pouvez ajouter d'autres canaux en ajoutant des extensions comme par
exemple Hipchat, Slack ou encore Jabber.

Configuration
-------------

Chaque utilisateur doit autoriser les notifications dans son profil :
**Profil Utilisateur > Notifications**. Cette option est désactivée par
défaut.

Vous devez, bien sûr, avoir renseigné une adresse email valide dans
votre profil et l'application doit être configurée pour envoyer des
emails.

![Notifications](/images/v1/fr/notifications.png)

Vous pouvez choisir votre méthode favorite de notification :

- Email
- Web

Pour chaque projet dont vous êtes membre, vous pouvez choisir de recevoir des notifications pour :

- Toutes les tâches
- Seulement les tâches qui vous sont assignées
- Seulement les tâches que vous avez créées
- Seulement les tâches que vous avez créées et celles qui vous sont assignées

Vous pouvez aussi sélectionner certain projets, par défaut tous les
projets dont vous êtes membre sont sélectionnés.

Notifications web
-----------------

Les notifications web sont accessibles depuis le tableau de bord ou
depuis l'icône en haut de la page :

![Icône de notifications web](/images/v1/fr/web-notifications-icon.png)

Les notifications sont affichées sous forme de liste. Vous pouvez
marquer comme lu chacune d'entre-elle ou toutes en même temps.

![Notifications web](/images/v1/fr/web-notifications.png)

Avec cette méthode vous pouvez quand même rester avertis de ce que se
passe sans pour autant être inondé d'emails.

Mentionner les utilisateurs
---------------------------

Kanboard offre la possibilité d'envoyer des notifications lorsque
quelqu'un est mentionné.

Si vous avez besoin d'obtenir l'attention de quelqu'un dans un
commentaire ou une tâche, utilisez le symbole @ suivi de l'identifiant
de l'utilisateur. Kanboard va automatiquement suggérer une liste
d'utilisateurs :

![Mention utilisateur](/images/v1/fr/user-mentions.png)

- Pour le moment, cette fonctionnalité est activée uniquement pour la description des tâches et les commentaires
- Cela fonctionne seulement lors de la création des tâches ou commentaires
- Pour être mentionné, les utilisateurs doivent être membres du projet
