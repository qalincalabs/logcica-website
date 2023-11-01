---
title: Story
date: 2023-11-01T00:00:00.000Z
---

# La construction

Le développement de la plateforme logCiCa (logistique collaborative pour les circuits courts) a débuté mi-septembre 2021 avec l’engagement d’Olivier, développeur software.

Le **besoin d’une plateforme** (ensemble d’outils autour d’une même base) s’est rapidement fait sentir. Divers outils et intégrations sont nés pour satisfaire les besoins des acteurs des circuits courts et ont mué pour surmonter les défis rencontrés au fil du projet.

La plateforme est bâtie sur la volonté de :

- **Collaboration logistique** : le plus haut niveau de maturité en logistique
- **Interopérabilité** : la capacité à se connecter à d’autres plateformes, via des librairies partagées, API, HTML incorporé, …
- **Utilité** : aider les acteurs au quotidien, du court au long terme
- **Pertinence** : 
  - Être adapté aux circuits courts
  - Être en phase avec les outils digitaux utilisés par les acteurs des circuits courts
- **Globalité**
  - Des services aussi bien stratégiques que opérationnels
  - Prendre en compte tous les aspects de la logistique : approvisionnement, planification, transport, gestion des retours, …
  - À tous les niveaux de gestion (entreprise, partenariat, territoire, filière)
- **Coût d’exploitation minimum** (beaucoup d’acteurs ont peu de ressources financières)

Les chapitres suivants reprennent l’évolution chronologique de la plateforme logCiCa au niveau technique. [**Un tableau récapitulatif des dernières actions est disponible ici**](https://docs.google.com/spreadsheets/d/1Hinnt_VSZFGCe-0SFNRxKkSsytXf2aDYnp6gYdiVJ0I/edit#gid=934555503)**.**

## La recherche de solutions existantes (Sept. - Oct. 2021)

Les différents ERPs, CRMs, e-commerces [sont passés en revue](https://docs.google.com/spreadsheets/d/1FAwcNQv7SlnQkI5jE40PZGtRSQ5t6xgO/edit#gid=2138143957). Les solutions digitales spécialisées sont épluchées (spécifique à l’envoi de colis, TMS, WMS, …). L’accent est mis sur les outils open source pour s’assurer de la pérennité et viabilité économique du projet : possibilité de transformer l’outil suivant les besoins du projet sans casser la tirelire. 

**Aucune solution holistique ne semble se profiler. La difficulté d’intégration et de modification, la faible maturité ou la non-pertinence** vis-à-vis des circuits courts éliminent de nombreuses initiatives et **ne laissent que les APIs spécialisées** (routing, géolocalisation, mapping) comme briques de construction.

**L’idée d’une plateforme logistique collaborative** dédiée aux circuits courts se dessine. On recherche les technologies et concepts software de base qui serviront de fondations. On explore tout ce qui permet un **haut niveau d’interopérabilité, un coût d’exploitation proche de zéro et une certaine rapidité de mise en œuvre** : 

- Les types d’API : GraphQL ou REST
- Les types de plateforme (MongoDB Atlas, …)
- Les types d’outils de base de données (MongoDB, ElasticSearch, …
- Les types de format de données (GeoJSON)
- Les outils d’hébergement et d’exposition sur le cloud (GitHub, …).

Pour maximiser la compatibilité avec d’autres systèmes, on étudie et on s’inspire des standards de modélisation de produits et de gestion de la chaîne d’approvisionnement (GS1, shema.org, UN/CEFACT, Data Food Consortium, …). Une attention particulière est portée sur les modèles derrière : 

- les plateformes partenaires DigiCirCo : Open Batra, OFN
- les plateformes plus générales que l’on pourrait utiliser comme source de données (BCE, Open Food Facts …) 
- les outils accessibles et open source (MongoDB charts,…)

## La logistique collaborative avec Koala (Nov. - Dec. 2021)

Après une phase de recherche et d’analyse, le travail de création et de conception peut démarrer avec l’ajout du premier outil à la plateforme : [Koala](https://github.com/qalincalabs/koala). En s’imprégnant du projet pilote existant “CHOUD’Bruxelles”, **le nouveau projet pilote Koala permettant de simuler et analyser la logistique collaborative des circuits-courts**. En comparaison avec “CHOUD’Bruxelles”, le modèle de Koala est plus **flexible** et **interopérable** ce qui lui permet d’être plus rapide à développer et faire évoluer. Koala se compose d’un modèle de données pouvant être implémentées sur **Google Sheet**. « L’activation » du modèle permet la géolocalisation automatique ainsi que l’importation des informations produits issues de la base de données Open Batra. Les données de différents producteurs sont insérées sur Koala. Des visualisations sont également générées à partir de ces dernières.

![](https://lh7-us.googleusercontent.com/fTuaPq7-sl1FFzyD_v5QX4jnJYUMdLOKrcx1btn5fC99D1ATIbxRU6TmwjEQxWG1AK9933J-PFupdoHZ3PJsj4wEfgDcgop2J5en2d5QHUn1QzUi_Yci9y91GfyHYHc8XcfdP3ALKLMfE4TriShYqIk)

## La logistique intégrée et stratégique avec Cockpit et logCiCa 1.0 (Jan. - Mai 2022)

Les notions d’offre, de sessions de vente, clients, fournisseurs sont ajoutées à la structure de données logCiCa. Une librairie de consolidation de données, [Consolidator](https://www.npmjs.com/package/@qalincalabs/consolidator), voit le jour, logCiCa se mue en **data warehouse**. La plateforme a la capacité d’accueillir les données d’outils externes quelle que soit leur structure de données, les **mapper** sur la structure logCiCa, les **identifier**, les **mettre à jour**, les **mettre en relation**. L’entièreté de la structure de données est **accessible et modifiable via API**.

Grâce à l’outil [Cockpit](https://github.com/qalincalabs/cockpit)**,** **des tableaux de bord peuvent être créés et modifiés par des non développeurs**.

![](https://lh7-us.googleusercontent.com/uSg4uxptaNwEQnArpqRkI8lC94Rf-2QfQX3p2_qkz0TsoMypYuDl41d2nC3PsqjcUuAWdFcaqvKj8WWWdbGbSFXHTGBnfBhCcwI0Ebed2A5UZLTw4hb9NpSlvCD4tZ8eIfi4BLVmclRddl5tkrar5iM)

## La logistique opérationnelle de bout en bout (Juin 2022 - Mars 2023)

Grâce à l’outil [Coconut](https://github.com/qalincalabs/coconut-slack-app) (et son interface graphique sur Slack, qui est une plateforme de communication collaborative ), une **commande créée sur OFN be devient un envoi sur logCiCa et s’affiche dans le canal Slack du producteur** (avec un poids total sur base du poids des produits référencés sur Open Batra par exemple). Le producteur peut alors créer une tournée et ajouter les envois qu’il souhaite à cette tournée. L’itinéraire de la tournée est calculé via une API externe. **Slack**, une application de messagerie pour entreprise, conserve **l’attrait d’une messagerie classique** pour l’**organisation informelle** d’une activité et des collaborations mais ajoute une dimension **d’interopérabilité système et graphique immense.** On peut véritablement construire une application sur Slack. 

L’outil Koala qui est utilisé comme un “bac à sable”  (pour simuler une collaboration logistique) peut être généré à partir des données structurées présentes dans le backend de la plateforme.

Enfin, [Limosa](https://www.npmjs.com/package/@qalincalabs/limosa), une librairie de géolocalisation basée sur des API publiques est créée, ce qui permet d’ajouter une dimension géographique à logCiCa. La notion d’emplacement est ajoutée et permet de **situer les données à plusieurs échelles géographiques.**

Voici à quoi ressemble la plateforme à cette étape

![](https://lh7-us.googleusercontent.com/8eo1caObKqm67pbS9Mh4RcNFBsyNBG1EgtKN7Twf2JHbehP6c7xAV8H6T7vWKLQzpIcptJpQUXALoTBESm_HQb2biQ7AGwq0ImNOlyvqGJ1la1fErLBk-aB2D4Ztr9Y7vqoQgWMYyy8qHKzI0kDgbA4)

## L’appel à projet  “bourse aux transports”, pour un outil “pro” (Avr. - Mai 2023)

**Le besoin d’une interface graphique avec des fonctionnalités avancées se fait cruellement sentir.** Les **applications Slack sont plutôt limitées** à ce niveau et se réduisent souvent à un ensemble de fonctionnalités pour une notification bien précise (la commande une telle vient d’être validée, que voulez-vous faire ?). L’appel à projet “bourse aux transports” de la Socopro semble la bonne occasion pour faire évoluer la plateforme au niveau backend et **s'associer avec une entreprise de développement d’application web** pour son expertise et ses ressources front end.  **Le modèle de logCiCa s’adapte pour supporter une bourse aux transports** (de nombreuses notions sont ajoutées), une collaboration avec Sum Consulting se construit (énormément d’échanges d’expérience au niveau technique) mais [l’appel](https://drive.google.com/file/d/11zy2e_EgUxmhhu4WaZkM2R_QKo2x_19E/view?usp=sharing) n’est pas remporté. On continue avec les ressources disponibles.

## logCiCa 2.0, un modèle pour les circuits courts (Juin - Jui. 2023)

Après l’encodage des activités, des canaux de vente, des entités de gouvernance, des collaborations des différents acteurs rencontrés, on se rend compte que **le modèle manque de concepts et de relations entre ces concepts.** Il est donc soumis à d’importantes modifications, [**logCiCa 2.0**]({{< ref "/model/" >}}) **est né**. Tous les outils développés jusqu’ici vont devoir être portés vers cette nouvelle version.

![](https://lh7-us.googleusercontent.com/SmW6pyO8zZ5VIiEcl1psMDKxgawYKR-EfHU7PsZ7mhhSgTYkJhnbAmbeBBU-8S8Vv_zxkbrsQ_z4aDo3ZcE1Q0UVAXE2Xt2sxLo2Z0sCuy9papArZ9TBwk0uDYaurad1TjgS1EAKFrYtPN93P5W9aEs)

## Un outil de gestion complet et collaboratif : logCiCa au quotidien (Août - Sept. 2023)

Découvert lors d’échange technique, Appsmith est élu comme framework de développement low-code pour le nouvel ERP : [logCiCa au quotidien](https://app.appsmith.com/app/logcica-au-quotidien/abonnements-64ef08fa59a48d0a66258f85). **Pour pouvoir apporter un maximum de fonctionnalités en un temps record, une interface graphique développée via un outil low code est une solution appropriée.** 

![](https://lh7-us.googleusercontent.com/CJi2YsWwX_Ie9sZWQxzPG4P_8gXSyXXTkCYN1R5Gi4XDOdDdGXm2eT89PvauoNr94ug-B83K-8zkBN9Gpb2-tefO5FxSCnvr0LAZXn8Kr2hZtSk92goTMq0gt3-FujS_smFK2GUSipmSvAygtPO8WhU)

## Découvrir toutes les opportunités circuits courts via logCiCa explore (Sept. - Oct. 2023) 

[logCiCa explore](https://qalincalabs.github.io/logcica-discover/) est dans une premier temps également implémenté via Appsmith. Les limitations au niveau mobile (rapidité, graphique) font que **l’application est réécrite via un framework de génération de site statique (pour des raisons de rapidité, sécurité, flexibilité et économique).** Toutes les opportunités circuits courts (produits, marchés, événements, tournées régulières) ont leur place dans ce nouvel outil. Des **intégrations graphiques** (iframe ou HTML incorporé) **sont mises sur pied** pour exposer ces informations publiques dans les sites web de tout acteur (épicerie, territoire, groupement, …) qui promeut les circuits courts.

![](https://lh7-us.googleusercontent.com/oFmiRJuvpW39s-lyhLyKpdXNaNbhs9DM0cpaVMTEUPE05AnR6mKErLOIb_vByXJqYhOUY6MTAuSx_TNGP4fXMzAHVclqkyS8lgGgqZDyEf5a5oJYZGzD294hNWs2c7dyMkbArM73wL4hn60r7Yr1yCE)

## Utilisation de la plateforme et finalisation des fonctionnalités (Nov. 2023 - Juin 2024 ) 

Les prochaines étapes du projet seront principalement consacrées à l'implémentation et aux tests des outils développés auprès des utilisateurs. Après une phase au cours de laquelle les outils seront finalisés, nous allons les tester avec les utilisateurs pour valider l’impact que ceux-ci vont avoir sur la performance de leurs activités.


### Fonctionnalités à finaliser

- Outils et intégrations : migrer de logCiCa 1.0 à logCiCa 2.0
  - Koala (si une création de partenariat le demande)
  - Intégration commandes OFN (**nov. 2023**)
  - Intégration produits Open Batra (**nov. 2023**)
  - Shopify et WooCommerce (si utilisé par un acteur)
- logCiCa au quotidien : 
  - Préparation de commande et envoi (**déc. 2023 à fév. 2024**)
- logCiCa explore
  - Carte et filtre (**mars 2024**)
- Coconut -> Chat (s’il reste du temps) : transformer l’application de transport via messagerie en un outil plus large de messagerie pour l’ensemble de la plateforme

### Utilisation de la plateforme

On met l’accent sur la diversité des acteurs et on leur propose une intégration qui leur apporte une réelle plus-value.

- Producteurs DigiCirCo (**déc. 2023 - juin 2024**)
  - intégration Open Batra, OFN
  - utilisation Explore et Au quotidien
- Hub sur OFN (La Consigne, **jan. 2023 - avr. 2024**)
  - intégration Open Batra, OFN
  - utilisation Cockpit et Explore (producteurs, comptoirs, groupement)
- Territoire (’L'ADL BBHP, **oct. 2023 - mars. 2024**)
  - Intégration (machine et graphique)
  - Utilisation Explore (producteurs, marchés, emplacements, évènements)
