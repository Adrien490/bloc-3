# Script Oral - Présentation Bloc 3 (35 minutes)

## Introduction (2 minutes)

Bonjour ! Je suis Adrien Poirier et je vais vous présenter mon projet de Bloc 3 : "Diététique et Interventions".

Le défi ? Créer un site web complet pour une diététicienne. D'un côté, un site vitrine pour présenter ses services. De l'autre, un espace d'administration privé pour gérer toutes les demandes de contact. Le site fonctionne déjà en ligne à l'adresse dietetique-et-interventions.manonchaillou.fr, et tout le code est accessible sur GitHub.

Aujourd'hui, je vais vous raconter comment j'ai mené ce projet de A à Z : la planification, le pilotage, les décisions importantes, et bien sûr une démo en direct !

---

## Sommaire et Méthodologie (3 minutes)

Comme vous le voyez, j'ai organisé ma présentation autour des compétences du référentiel. Chaque point sera illustré avec des exemples concrets !

Pour organiser ce projet, j'ai choisi la méthode Scrum. "Scrum tout seul ?", vous allez me dire. Eh bien oui ! Même en solo, cette méthode m'apporte un cadre structuré et me permet de m'améliorer en continu.

Concrètement, j'ai réparti les rôles : la diététicienne devient la "Product Owner" - elle définit les besoins. Moi, je joue à la fois le "Scrum Master" qui organise, et l'équipe de développement qui code. Je travaille par cycles de 2 semaines, ce qui me donne un bon rythme sans me mettre trop de pression.

Les rituels Scrum, je les ai adaptés à ma sauce : je planifie chaque cycle en 1 heure, je fais le point quotidien via mon tableau Trello plutôt qu'en réunion, je présente les avancées chaque semaine à la cliente, et je prends 20-30 minutes en fin de cycle pour réfléchir à ce qui peut être amélioré.

Pour l'organisation, j'utilise Trello pour gérer mes tâches, j'ai défini des critères clairs pour dire qu'une fonctionnalité est "finie" (tests OK, cliente validée), et chaque nouvelle version se déploie automatiquement sur internet.

---

## Planification et Architecture (5 minutes)

Pour m'organiser, j'ai mis en place un tableau Trello - c'est mon tableau de bord quotidien. Vous le voyez ici avec mes colonnes "À faire", "En cours", "En test" et "Terminé".

J'ai découpé le projet en 6 étapes de 2 semaines :

- Étape 1 : on définit ensemble le projet et le design
- Étape 2 : je crée le site vitrine avec un bon référencement Google
- Étape 3 : j'ajoute le formulaire de contact avec possibilité d'envoyer des fichiers
- Étape 4 : je mets en place la connexion sécurisée pour l'administration
- Étape 5 : je développe l'espace privé pour gérer les demandes
- Étape 6 : je peaufine la qualité et je mets tout en ligne

C'est logique : il faut d'abord le formulaire avant de pouvoir gérer les demandes, et il faut la connexion sécurisée avant l'espace admin. Tout se termine par la mise en production.

Voici la timeline complète sur 3 mois. Chaque étape a son jalon de validation - c'est là que la cliente valide ou demande des ajustements.

Côté technique, j'ai choisi des technologies modernes et fiables. Pour l'interface utilisateur, j'utilise Next.js et React - des outils très populaires pour créer des sites web interactifs. J'ai ajouté TypeScript pour éviter les erreurs de code, et Tailwind CSS pour un design propre et responsive.

Pour la partie serveur, je stocke les données dans une base PostgreSQL, j'utilise Vercel pour héberger le site (avec déploiement automatique), et plusieurs services spécialisés : Resend pour envoyer les emails automatiquement, UploadThing pour gérer l'envoi de fichiers, et Sentry pour surveiller les erreurs.

Côté qualité, j'ai mis en place des tests automatiques, des vérifications de performance avec Lighthouse, et des contrôles d'accessibilité pour que le site soit utilisable par tous.

J'ai organisé mon code de manière logique : un dossier pour tout ce qui concerne l'authentification, un autre pour les demandes de contact, etc. Ça rend le code plus facile à maintenir.

---

## Découpage fonctionnel et User Stories (3 minutes)

J'ai découpé le projet en 5 grandes parties :

- Partie 1 : Le site vitrine avec toutes les pages et un bon référencement
- Partie 2 : Le formulaire de contact qui permet d'envoyer jusqu'à 3 fichiers de 4MB maximum, avec envoi automatique d'email
- Partie 3 : Le système de connexion sécurisé pour accéder à l'administration
- Partie 4 : L'espace privé avec la liste des demandes, la recherche, les filtres, et la gestion des statuts
- Partie 5 : Tous les aspects qualité : tests, accessibilité, performance et conformité RGPD

Pour bien définir les besoins, j'utilise des "user stories" - des petites histoires qui décrivent ce que veut faire l'utilisateur. Par exemple : "En tant que visiteur, je veux envoyer une demande de contact avec des pièces jointes pour préparer mon suivi."

Pour chaque histoire, je définis des critères précis : 3 fichiers maximum, 4MB par fichier, formats jpg/png/pdf acceptés, message de confirmation affiché, email automatique envoyé à la diététicienne, et demande visible dans l'espace admin avec le statut "Nouveau".

Cette méthode m'aide à ne rien oublier et facilite les tests avec la cliente.

---

## Pilotage et Indicateurs (4 minutes)

Pour suivre l'avancement, mon tableau Trello a 4 colonnes : "À faire", "En cours", "En révision" et "Terminé". Chaque tâche suit un parcours complet : elle devient une branche de code, puis une demande de fusion, puis un test en ligne, et enfin une mise en production.

Cette traçabilité me permet de suivre chaque fonctionnalité de l'idée jusqu'à sa mise en ligne.

Je surveille plusieurs indicateurs pour m'assurer que tout va bien :

Pour la qualité du code : tous mes 1557 tests automatiques passent au vert, et j'ai 56% de couverture de code (j'aimerais atteindre 70%).

Pour les performances du site : Lighthouse me donne 92/100 en vitesse, et 100/100 en accessibilité, référencement et bonnes pratiques. Sentry me confirme 0 erreur en production.

Pour les délais et le budget : je mesure le temps entre une idée et sa mise en ligne, et surtout, le projet me coûte 0€ car j'utilise les versions gratuites de tous les services !

J'ai surveillé de près ma consommation des services gratuits : Vercel pour l'hébergement (45, 72 et 38 GB sur les 3 mois, limite à 100GB), Resend pour les emails (127, 234 et 89 emails envoyés, limite à 3000), UploadThing pour les fichiers (0,8 à 1,2 GB utilisés sur 2GB autorisés), et Sentry pour le monitoring (23 à 67 erreurs détectées sur 5000 autorisées).

Je travaille environ 20h par semaine sur le projet, et je me limite à 1 ou 2 tâches en parallèle pour rester concentré.

---

## Gestion des Risques et Arbitrage (4 minutes)

J'ai anticipé plusieurs types de problèmes possibles : sécurité, bugs qui cassent des fonctionnalités existantes, dépassement des quotas gratuits, et respect du RGPD. Pour les détecter, je m'appuie sur mes tests automatiques, Sentry qui surveille les erreurs, mes vérifications manuelles, et les retours de la cliente.

Quand un problème survient, j'ai mes solutions : correction rapide sur une branche spéciale, activation/désactivation de fonctionnalités, ou mise à jour des dépendances.

Dans mon tableau des risques, j'ai par exemple le risque de dépasser les quotas Vercel (impact moyen mais peu probable), avec surveillance et plan B. Ou le risque de casser la connexion (impact élevé, probabilité moyenne) que je limite avec des tests automatiques.

Exemple concret : le bug de l'email dans le footer. Sur les petits écrans de téléphone, l'adresse email était trop longue et créait un scroll horizontal gênant. J'ai corrigé ça avec du CSS qui coupe proprement le texte. Problème identifié, résolu et documenté !

Pour prendre des décisions importantes, j'ai mes critères : respecter les délais, couvrir le besoin, évaluer le risque technique, l'impact sur l'expérience utilisateur et le coût. Je reste toujours transparent avec la cliente et je documente mes choix.

---

## Management et Communication (3 minutes)

En solo, je porte toutes les casquettes : designer, développeur front et back, testeur, responsable du déploiement, et chargé de relation client. Ça demande une organisation au top !

Je priorise avec ma liste de tâches ordonnée, je planifie chaque semaine, j'exécute en me limitant à 2 tâches max en parallèle pour rester focus, et je m'améliore grâce aux rétrospectives.

Même en travaillant seul, j'ai pensé à l'accessibilité à deux niveaux : dans le site lui-même avec les standards d'accessibilité (navigation au clavier, contrastes, etc.), et dans mon organisation de travail avec de la documentation claire, des enregistrements des présentations à la cliente, des sous-titres automatiques sur Google Meet, et la possibilité d'adapter les réunions si nécessaire.

Mon style de management avec la cliente est collaboratif : on construit ensemble les contenus du site pendant nos points hebdomadaires, et je valide l'expérience utilisateur avec elle.

Prenons un exemple concret d'arbitrage : fallait-il prioriser la conformité RGPD ou le dashboard ? Ce qui a bien marché : j'ai expliqué clairement les risques juridiques, montré l'impact sur l'activité, et on a décidé ensemble avec la cliente. À améliorer : j'aurais dû mieux anticiper les dépendances et planifier plus finement les contraintes légales.

Mes apprentissages : les schémas et visuels sont super efficaces pour expliquer, impliquer le client dans les décisions importantes c'est essentiel, et il faut absolument documenter les choix.

Pour communiquer, j'ai plusieurs moyens : des points hebdomadaires en visio avec Google Meet (ordre du jour, démo en direct, décisions prises, prochaines étapes), des emails pour les comptes-rendus officiels, Trello pour les commentaires sur les tâches, et GitHub pour les discussions techniques. Côté documentation : le README explique l'architecture, les tickets détaillent les spécifications, et les demandes de fusion donnent le contexte.

---

## Évaluation des Compétences (3 minutes)

J'ai établi une grille d'évaluation de mes compétences avec niveaux actuels et cibles.

Pour Next.js/React, je suis niveau 3 avec pour cible 4. Mes preuves : vitrine et dashboard en production, routing app dir maîtrisé, Server Actions implémentées.

TypeScript strict : niveau 3 vers 4. `tsc --noEmit` clean, types Domain définis, schémas Zod alignés.

Prisma/SQL : niveau 2 vers 3. Migrations `prisma migrate` maîtrisées, indexations, seed contrôlé.

Tests Jest/RTL : niveau 2 vers 3. 1557/1557 tests passants, 56,64% de coverage avec objectif 70%.

Accessibilité WCAG : niveau 3 vers 4. Pa11y à 0 erreur, Lighthouse accessibilité à 100, navigation clavier et focus maîtrisés.

CI/CD Vercel : niveau 3 vers 4. Preview par PR, `VERCEL_GIT_COMMIT_SHA` exposé.

RGPD et sécurité : niveau 2 vers 3. Registre établi, DPA avec tous les fournisseurs, headers sécurisés.

Gestion de projet Scrum : niveau 3 vers 4. Sprints S1 à S6 exécutés, Reviews régulières, burndown et vélocité suivis.

Les écarts clés identifiés concernent les tests d'intégration/e2e manquants avec coverage sous 70%, Prisma pour les requêtes avancées et transactions, et le pilotage avec des KPIs fonctionnels.

Mes priorités de développement : Tests e2e avec Playwright pour les parcours Visiteur et Admin, observabilité renforcée avec Sentry alerting et traces, RGPD avec registre complet et minimisation des données.

Mon plan de développement inclut des formations Playwright, Prisma avancé, A11y WCAG 2.2, RGPD, et de la pratique avec pair-review externe et objectifs trimestriels.

Objectifs mesurables : coverage ≥ 70% d'ici le 30/06, 2 parcours e2e stables en S6, erreurs Sentry < 1% sur 30 jours glissants.

---

## Suivi Client et Indicateurs (3 minutes)

Pour les comptes rendus, j'utilise un format email structuré : faits → décisions → risques → prochaines étapes, envoyé après chaque Review et jalons, stocké dans les emails et le README.

Exemple de CR anonymisé de la Review S3 : "Formulaire opérationnel, upload 3×4MB OK" pour les faits, "Validation S4 auth, priorisation rôles" pour les décisions, "Quota UploadThing 1,2GB/2GB" pour les risques, "S4 auth Better Auth, rôles, protection routes" pour les prochaines étapes.

Mes jalons et Reviews suivent les dates réelles : fin mars vitrine/SEO validés, mi-avril formulaire et email OK, fin avril auth et rôles, mi-mai dashboard complet, fin mai qualité Lighthouse/Pa11y OK, fin mai mise en production et démo finale.

Le processus de validation suit un flow : Développement → Preview Vercel → Démo Review → Validation → Production ou Ajustements si nécessaire.

Mes critères GO/NO-GO incluent tests passants, Lighthouse au-dessus des seuils, et validation commanditaire.

Pour la satisfaction, je mesure le NPS post-démo, questionnaire 1-5 après Review, taux d'achèvement formulaire, délai création-traitement, et taux de rebond des pages vitrine.

Qualité technique : erreurs Sentry sous 1%, Lighthouse avec performance ≥ 90, accessibilité 100, SEO 100, best practices 100.

La boucle d'amélioration suit : Retour client → Issue GitHub → Sprint Backlog → PR → Preview → Production.

Exemple corrigé : Issue #1 BUG-001 footer/email mobile en S2, avec problème de débordement horizontal sur mobile < 375px, solution `word-break: break-all` + classes Tailwind responsive, commit e9deaf5.

La roadmap produit prévoit pour S6 : tests e2e, RGPD, performance. Q3 2025 : module devis. Q4 2025 : notifications, export, API.

---

## Démonstration (8 minutes)

Allez, place à la démo ! Je vais vous montrer le site en action avec deux parcours : visiteur et administrateur.

**Côté visiteur** (4 minutes)

Je vais sur le site en ligne : dietetique-et-interventions.manonchaillou.fr

[Navigation sur le site]

Voilà l'accueil avec une présentation claire des services. Le site s'adapte automatiquement à toutes les tailles d'écran - regardez quand je redimensionne la fenêtre.

Je clique sur "Prestations" pour voir le détail des services. Tout est optimisé pour Google avec de bonnes descriptions et une structure claire.

Maintenant, direction "Contact". Voici le formulaire avec vérification en direct. Je remplis les champs obligatoires : nom, prénom, email, téléphone et message.

Pour les pièces jointes, on peut envoyer jusqu'à 3 fichiers de 4MB maximum. Formats acceptés : jpg, png et pdf. Regardez, si j'essaie d'ajouter un 4ème fichier, le système m'arrête. Si je mets un fichier trop gros ou d'un mauvais format, j'ai une alerte immédiate.

[Démonstration upload de fichiers]

Une fois envoyé, j'ai un message de confirmation et la diététicienne reçoit automatiquement un email avec tout le contenu et les fichiers joints.

**Côté administrateur** (4 minutes)

Maintenant, connectons-nous à l'espace privé avec le compte de test : jury@ynov.com, mot de passe : d85pm832

[Connexion au dashboard]

Et voilà l'espace d'administration ! La connexion est sécurisée avec des rôles - seules les personnes autorisées peuvent y accéder.

Dans "Demandes de contact", je vois la liste complète avec toutes les infos : nom, email, date, statut, et les actions possibles.

Je peux filtrer par statut : Nouveau, En cours, Traité, Archivé. La recherche marche sur le nom et l'email. Je peux trier toutes les colonnes.

[Démonstration des filtres et recherche]

Je clique sur une demande pour voir le détail. J'ai tout : coordonnées complètes, message, et les fichiers joints téléchargeables.

Je peux changer le statut direct depuis cette page. Par exemple, passer de "Nouveau" à "En cours", puis à "Traité". Chaque changement est daté et tracé.

[Démonstration changement de statut]

L'archivage permet de ranger les anciennes demandes sans les supprimer - ça respecte les obligations légales de conservation.

Tout est navigable au clavier pour l'accessibilité, et chaque élément interactif a un focus bien visible.

---

## Critères de Validation et Conclusion (2 minutes)

Cette démo valide tout ce qui était demandé : toutes les fonctionnalités marchent, c'est robuste avec les vérifications et la gestion d'erreurs, tout est tracé avec les statuts et l'archivage.

Côté technique, c'est bon aussi : accessible au clavier avec des focus visibles, performant et réactif, sécurisé avec l'authentification et les validations.

Et niveau qualité : expérience utilisateur fluide, design qui s'adapte partout (mobile/desktop), bien référencé sur Google, et code propre et testé.

Cette version finale a été validée par la cliente et répond parfaitement à ses besoins.

**Pour conclure**

Ces 3 mois de projet m'ont permis de vous montrer que je sais mener un projet de développement de bout en bout.

J'ai réussi à adapter Scrum en solo, maintenir une qualité au top avec zéro erreur en production, respecter tous les délais avec mes 6 étapes, et maîtriser les coûts en restant dans le gratuit.

Toutes les compétences du référentiel sont couvertes avec des exemples concrets : planification structurée, pilotage avec des indicateurs, décisions documentées, management collaboratif, montée en compétences, et suivi client régulier.

Le site tourne en production, la cliente l'utilise tous les jours, et il est prêt pour les évolutions prévues.

Merci pour votre attention ! Je suis là pour vos questions.

---

**Timing total : 35 minutes**

- Introduction : 2min
- Méthodologie : 3min
- Planification/Architecture : 5min
- User Stories : 3min
- Pilotage : 4min
- Risques/Arbitrage : 4min
- Management : 3min
- Compétences : 3min
- Suivi Client : 3min
- Démonstration : 8min
- Conclusion : 2min

**Notes pour la présentation :**

- Garder un débit naturel et professionnel
- Faire des pauses pour laisser le jury digérer l'information
- Préparer les fichiers de test pour la démo
- Vérifier la connexion internet avant la présentation
- Avoir un plan B si la démo ne fonctionne pas (captures d'écran)
- Maintenir le contact visuel avec le jury
- Être prêt à adapter le timing selon les réactions du jury
