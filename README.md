# MODÉLISATION DE BASES DE DONNÉES

## 2.1. FreeDoc - Réserve ton docteur

Allez, on va implémenter pour de vrai un concurrent de Doctolib! À toi d'être chirurgical 👩‍⚕️

Pour ce premier exercice, nous allons t'aider et te donner les models à créer :

1) un model Doctor, qui a comme attributs :
- un first_name, qui est un string
- un last_name, qui est un string
- un specialty, qui est un string
- un zip_code, qui est un string

2) un model Patient, qui a comme attributs:
- un first_name, qui est un string
- un last_name, qui est un string

3) un model Appointment, qui a comme attributs :
- un date, qui est un datetime

Une fois les attributs fixés, on s'attaque aux relations :
- Un appointment ne peut avoir qu'un seul doctor, mais un doctor peut avoir plusieurs appointment.
- Un appointment ne peut avoir qu'un seul patient, mais un patient peut avoir plusieurs appointment.
- Un doctor peut avoir plusieurs patient, au travers des appointments, et vice versa.

Ta startup de docteurs marche à merveille, tellement que tu aimerais ajouter plusieurs tables :
- city : Chaque docteur, patient, et rendez-vous est lié à une city. Une city peut avoir plusieurs docteurs, patients, et rendez-vous.
- tu voudrais virer la ligne specialty de ta table doctor et la remplacer par un model à part entière : tu vas donc créer un model specialty. Un docteur aurait plusieurs specialty, et une specialty pourrait concerner plusieurs doctor.

Et voilà pour FreeDoc! Doctolib est en PLS.

## 2.2. Le Airbnb des promenades de chiens

En cours de "Bizness Growth Money Maker", on t'avait demandé de créer une entreprise à fort potentiel. À l'époque tu t'étais dit que ce serait une chouette idée de faire une plateforme où des personnes pourraient promener les chiens des autres, en échange de cash-money. C'est dingue comme idée: ça va mettre tous les VC aux abois. Allez, on le fait !

À priori, les models sont simples: il y a un model dogsitter et un model dog (on te laisse choisir au moins un attribut chacun). Un dogsitter peut promener plusieurs dog lors d'une stroll (promenade, en anglais) ; et un dog peut avoir plusieurs dogsitter via les stroll.
Maintenant tu veux préciser la ville des promeneurs et des chiens pour faire un super algorithme de matching. Tu devras donc créer un model City avec comme attribut city_name. Chaque ville contient plusieurs promeneurs et plusieurs chiens mais un chien et un promeneur ne peuvent appartenir qu'a une ville.

## 2.3. The Gossip Project

Le parcours utilisateur est le suivant: sur ce super réseau social, un utilisateur va s'inscrire, renseigner son prénom et nom, son mail et son age, puis il précisera sa ville avec une recherche par code postal.

Il aura ensuite toutes les fonctionnalités qui feront de cette appli une future licorne de la Bitchin'Tech:
- Les utilisateurs peuvent créer des potins : "askip john est célib hihi"
- Les utilisateurs, en créant des potins, peuvent mettre un ou plusieurs tags sur les potins: #romance
- Les utilisateurs peuvent commenter des potins : "ahiii j'savé pa lol ptdr 💁‍♂️"
- Et puisque ton appli doit respecter les standards de l'industrie, on va faire en sorte qu'il soit possible aussi de commenter des commentaires.
- Les utilisateurs peuvent liker des potins.
- Les utilisateurs peuvent contacter leur commères favoris en MP pour obtenir des exclus mondiales. L'utilisateur pourra donc rechercher les potins par ville, par utilisateurs, par date (plus récent ou plus ancien), par nombre de likes, par tags, pour trouver les potins les plus croustillants.

1) LES USERS
Crée une classe User, qui aura comme attributs :
- Un first_name, qui est un string
- Un last_name, qui est un string
- Un description, qui est un text
- Un email, qui est un string
- Un age, qui est un integer

2) LES VILLES
Crée une classe City, qui aura comme attributs :
- Un name, qui est un string
- Un zip_code, qui est un string
Un utilisateur appartient à une seule ville mais une ville peut contenir plusieurs utilisateurs.

3) LES GOSSIPS
Crée une classe Gossip, qui aura comme attributs :
- Un title, qui est un string
- Un content, qui est un text
Un utilisateur peut écrire plusieurs gossips mais un gossip ne peut être écrit que par un seul utilisateur.

4) LES TAGS
Crée une classe Tag, qui aura comme attributs :
- Un title, qui est un string
Un gossip peut avoir plusieurs tags et un tag peut être présent sur plusieurs gossip (genre #bromance).

5) LES MESSAGES PRIVÉS
Crée une classe PrivateMessage, qui aura comme attributs :
- Un content, qui est un text Un PM aura un expéditeur et un (ou plusieurs) destinataires.

## 2.4. Un système d'info décisionnel pour votre université 🎓🎓

Maintenant que vous savez cruncher les classements mondiaux des universités, vous avez pu transmettre un reporting sur l'évolution des performances de votre Université. Depuis, les équipes veulent améliorer cette performance. Et pour cela, le recteur de l'Université de Strasbourg vous a demandé de mettre en place un système qui lui permettra de prendre des décisions éclairées.

En fait, il cherche à étudier les facteurs influant sur la réussite des candidats aux examens. Pour cela, on vous a chargé de construire un datawarehouse.

Il souhaite pouvoir répondre aux questions suivantes :
- Quel est le nombre de réussites aux examens par cours, pour l’année 2020 ?
- Quel est le nombre de réussites aux examens d’un cours obligatoire, pour l’année 2020 ?
- Quel est le nombre de réussites aux examens par genre (féminin, masculin), entre 2019 et 2020 ?
- Combien d’apprenants ayant un âge supérieur à 23 ans ont réussi leurs examens de « BI » ?
- Quel est le nombre de réussites aux examens pendant le semestre d’hiver 2020 ?

Pour cela, vous disposez des données suivantes : pour chaque examen passé, on connaît l’âge et le genre de l’apprenant, le nom du cours (les cours peuvent être regroupés en cours obligatoire et cours à option), la date de l’examen, la note obtenue et si l’examen est réussi ou non.

Pour l'instant, il vous demande de réfléchir à la conception du système. Vos missions sont les suivantes :
- Donner la table principale de l’entrepôt ainsi que les tables dimensions relatives.
- Tracer le schéma en étoile dimensionnel.
