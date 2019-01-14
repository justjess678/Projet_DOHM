

# Réalisation d’un noyau compréhension-gestion de dialogue

Kévin Cortacero
Pierre Mespoulet
Jessica Chambers
3ASRI

DÉCEMBRE 2018



## Présentation du projet

Dans le cadre de nos cours de Dialogue Oral Homme-Machine et suite à nos travaux pratiques de découverte (mise en place de grammaires et de dialogues et sous-dialogues simples) nous étions menés à compléter un projet d’agenda vocal qui permettrait à l’utilisateur de:

Se connecter à son compte avec un numéro d’utilisateur

Ajouter un rendez-vous à son agenda avec un date, une heure, un lieu, un sujet et une personne

Supprimer un rendez-vous

Modifier le sujet, le lieu ou la personne concernée par le rendez-vous

Déplacer un rendez-vous

Consulter les rendez-vous

Le tout en parlant  avec le système d’une manière naturelle

Les modifications faites sur l’agenda doivent être retournées sous forme d’une requête SQL correspondant

Il y a quelques contraintes à respecter néanmoins

Les heures que l’on peut ajouter doivent être comprises entre 7h30 et 21h30

Les demandes d’informations associées à chaque action possible se feront par le biais de sous-dialogues

La stratégie de confirmation sera implicite par défaut

Le système doit pouvoir gérer la réception de plusieurs informations en même temps

Au cours de ces dernières semaines nous avons développé un système visant à répondre à ces attentes, et dans ce rapport nous allons détailler l’organisation de l’application, les stratégies et les concepts utilisés ainsi que les modèles de dialogue de chaque sous-dialogue. 


## Stratégies  et Concepts utilisés

À partir d’un système de dialogue global (appelé “main”), des sous-dialogues sont appelés en fonction des réponses de l’utilisateur.  La partie reconnaissance de la parole est gérée par le système existant Optimtalk, le coeur du projet est le traitement de la parole. 
D’un point de vue conceptuel, un rendez vous est défini par:

Le numéro d'identification de l’utilisateur

Une date (réelle; on ne peut pas poser de rendez-vous le 35 août, par exemple)

Une heure (entre 7h30 et 21h30)

Un lieu (faisant partie de la grammaire définie, à savoir Toulouse, Marseille, Bordeaux ou Paris)

Une personne (faisant partie de la grammaire définie, à savoir [Monsieur/Madame] John Rambo, James Bond ou Bob Marley)

Un sujet (faisant partie de la grammaire définie, à savoir un rendez-vous médical, un contrôle de routine, un bilan ophtalmologique, ou dodo (utilisé dans les tests))

Dans les cas où ces contraintes ne sont pas respectées, l’utilisateur reçoit un message d’erreur approprié. Si le système ne comprend pas la demande de l’utilisateur il lui demande de répéter deux fois avant de lui demander les informations explicitement, élément par élément.

## Segments conceptuels

Le seul endroit où les segments conceptuels jouent un rôle indispensable est au niveau du déplacement d’un rendez -vous; en effet, il faut savoir différencier les anciennes dates et heures des nouvelles. Nous avons donc fait l’hypothèse que le mot “au” viendra entre les date/heure d’origine et les nouvelles.



## Conclusion

Dans le cadre de ce TP nous avons eu l’occasion de prendre en main le langage de balisage extensible vocal VXML ainsi que le langage de spécification de grammaire pour la reconnaissance vocale GRXML. Nous avons rencontré des problèmes techniques dans l’implémentation de ce système de prise de rendez-vous liés au technologies. Cependant nous avons pu appliquer la partie conceptuelle vue en cours. 

## Annexe
Le code du projet est disponible ici: 
https://github.com/justjess678/Projet_DOHM/tree/master/ProjetDOHM 
