# Script Oral - Présentation Bloc 3 (35 minutes)

## Introduction (2 minutes)

Bonjour. Je suis Adrien Poirier et je vous présente aujourd'hui mon projet de Bloc 3 : "Diététique et Interventions".

L'objectif était de créer un site vitrine avec un back-office de gestion des demandes de contact pour une diététicienne nutritionniste. Le site est actuellement en production à l'adresse dietetique-et-interventions.manonchaillou.fr, et le code source est disponible sur GitHub.

Ma présentation va couvrir tous les aspects du référentiel, de la planification à la démonstration, en passant par le pilotage, l'arbitrage, le management d'équipe et le suivi client.

---

## Sommaire et Méthodologie (3 minutes)

Comme vous pouvez le voir sur cette slide, j'ai structuré ma présentation pour couvrir l'ensemble des compétences du référentiel C3.1 à C3.4.2.

Pour ce projet, j'ai choisi d'adapter la méthodologie Scrum à un contexte de développeur unique. Pourquoi Scrum ? Parce que même en solo, cette approche apporte de la structure, de la transparence et permet une amélioration continue.

J'ai adapté les rôles : la commanditaire joue le rôle de Product Owner, j'assume celui de Scrum Master comme facilitateur, et bien sûr je suis l'équipe de développement. Les sprints durent 2 semaines, ce qui permet un rythme soutenu tout en gardant de la flexibilité.

Les événements Scrum ont été adaptés : le Sprint Planning dure 1 heure en début de sprint, le Daily est asynchrone via le board Trello pour éviter la surcharge, les Sprint Reviews sont hebdomadaires en présentiel pour maintenir l'alignement client, et les rétrospectives de fin de sprint durent 20-30 minutes pour l'amélioration continue.

Les artifacts incluent le Product Backlog géré dans Trello, le Sprint Backlog visible sur le board, une Definition of Done claire avec lint, type-check, tests, preview OK et validation client, et l'increment déployé automatiquement sur Vercel.

---

## Planification et Architecture (5 minutes)

Pour la planification, j'ai utilisé Trello comme outil principal avec une structure board/sprints et des milestones clairs. Voici le board que j'utilise quotidiennement.

J'ai défini 6 sprints de 2 semaines chacun :

- S1 pour le cadrage fonctionnel et design
- S2 pour la vitrine et le SEO
- S3 pour le formulaire de contact avec upload
- S4 pour l'authentification et les rôles
- S5 pour le dashboard administrateur
- S6 pour la qualité, le RGPD et la mise en production

Cette planification respecte les dépendances : le formulaire doit être prêt avant le dashboard, l'authentification aussi, et tout converge vers la production en S6.

Côté architecture technique, j'ai opté pour une stack moderne et robuste : Next.js 15 avec React 19 pour le frontend, TypeScript strict pour la sécurité du code, Tailwind CSS pour le styling, et Radix UI avec shadcn/ui pour les composants.

Le backend utilise les Server Actions de Next.js combinées aux API Routes, avec Prisma ORM pour la base de données PostgreSQL. L'infrastructure repose sur Vercel pour l'hébergement et le CI/CD, Better Auth pour l'authentification, et plusieurs services comme Resend pour les emails et UploadThing pour les fichiers.

Pour la qualité, j'ai mis en place Jest avec React Testing Library, Lighthouse pour la performance, Pa11y pour l'accessibilité, et Sentry pour le monitoring.

L'architecture logique suit un DDD léger avec une séparation par domaines : auth, contact-request, user, plus un dossier shared pour le code commun.

---

## Découpage fonctionnel et User Stories (3 minutes)

Le projet a été découpé en 5 lots fonctionnels :

- Lot 1 Vitrine avec pages, SEO et contenus
- Lot 2 Contact avec validation Zod, uploads limités à 3 fichiers de 4MB max, et envoi d'emails via Resend
- Lot 3 Auth avec Better Auth et gestion des rôles
- Lot 4 Dashboard avec listing, recherche, filtres, tri, détail, changement de statut et archivage
- Lot 5 Qualité et RGPD avec tests, accessibilité, performance et registre de conformité

Prenons l'exemple de la user story US-VIS-02 : "En tant que visiteur, je veux envoyer une demande de contact avec pièces jointes afin de préparer mon suivi."

Les critères d'acceptation sont précis : validation Zod des données, maximum 3 fichiers, chaque fichier limité à 4MB, types acceptés jpg/png/pdf, message de succès affiché, email Resend reçu par la diététicienne, et entrée visible dans le dashboard avec le statut "Nouveau".

Cette approche par user stories avec critères d'acceptation clairs facilite les tests et la validation client.

---

## Pilotage et Indicateurs (4 minutes)

Pour le pilotage, j'utilise Trello comme outil de suivi principal avec 4 colonnes : To do, In progress, Code review, Done. Chaque carte Trello est liée à une branche GitHub, puis à une Pull Request, puis à un déploiement Preview Vercel, et enfin à la production.

Cette traçabilité complète permet de suivre chaque fonctionnalité de l'idée à la mise en production.

Mes indicateurs de pilotage couvrent plusieurs dimensions :

Pour l'avancement et la qualité : tous les tests passent (1557/1557), avec un coverage de 56,64% que je vise à porter à 70%.

Pour la performance et la stabilité : Lighthouse affiche un score de 92 en performance, 100 en accessibilité, 100 en SEO, 100 en best practices, et Sentry rapporte 0 erreur.

Pour les délais et le budget : je mesure le cycle time de l'issue à la production, et les coûts restent à 0€ grâce aux paliers gratuits de tous les services.

Concernant les coûts, j'ai fait un suivi précis des consommations : Vercel avec 45/72/38 GB sur les 3 mois pour 100GB autorisés, Resend avec 127/234/89 emails pour 3000 autorisés, UploadThing avec 0,8/1,2/0,6 GB pour 2GB autorisés, et Sentry avec 23/67/12 erreurs pour 5000 autorisées.

J'ai une capacité de 20h/semaine avec un WIP limité à 1-2 tâches maximum pour maintenir le focus.

---

## Gestion des Risques et Arbitrage (4 minutes)

J'ai identifié plusieurs types de risques : sécurité, régressions, dépassement de quotas, et conformité RGPD. La détection se fait via les tests automatisés, Sentry pour le monitoring, la QA manuelle, et les retours client. Les actions incluent les hotfix sur branches `fix/*`, les feature toggles, et les mises à jour de dépendances.

Mon registre des risques documente par exemple le risque de quota Vercel (impact moyen, probabilité faible) avec monitoring et plan B, et le risque de régression auth (impact élevé, probabilité moyenne) mitigé par les tests e2e.

Je peux vous donner un exemple concret de risque résolu : l'Issue BUG-001 sur l'affichage email du footer. Le problème était que l'email dans le footer provoquait un débordement horizontal sur mobile pour les écrans inférieurs à 375px, créant un scroll horizontal indésirable. J'ai résolu cela avec du CSS responsive utilisant `word-break: break-all` et les classes Tailwind appropriées. Cette issue a été fermée avec le commit e9deaf5.

Pour l'arbitrage, ma méthodologie repose sur des critères clairs : délai, couverture du besoin, risque technique, dette technique, impact UX et coût. Cette approche structurée me permet de prendre des décisions éclairées en cas de contraintes ou d'imprévus, toujours en maintenant la transparence avec la commanditaire et en documentant les rationales pour la traçabilité.

---

## Management et Communication (3 minutes)

En tant que développeur unique, j'assume toutes les responsabilités : conception UX, développement front/back/DB, tests et qualité, DevOps CI/CD, et relation client. Cette situation nécessite une auto-organisation rigoureuse.

Ma priorisation se base sur le Product Backlog ordonné, la planification via Sprint Planning hebdomadaire, l'exécution avec un WIP limité à 2 pour maintenir le focus, et l'adaptation via les Sprint Retrospectives.

Bien qu'en contexte solo, j'ai intégré la prise en compte du handicap dans le développement : le site respecte les standards WCAG 2.1 AA avec navigation clavier complète, contrastes conformes, et focus visibles. Cette démarche d'accessibilité démontre ma sensibilité aux besoins des personnes en situation de handicap.

Mon style managérial est participatif : je co-construis les contenus vitrine en Review et valide l'UX et les fonctionnalités avec la commanditaire.

Pour l'analyse critique, prenons le cas "prioriser RGPD vs Dashboard". Ce qui a bien fonctionné : l'explication des risques juridiques, la visualisation des impacts métier, et la co-décision avec la commanditaire. À améliorer : l'anticipation des dépendances et une planification plus fine des contraintes légales.

Mes apprentissages incluent l'efficacité de la communication visuelle, l'importance de l'implication client dans les arbitrages, et la nécessité de documenter les décisions.

Pour la communication, j'utilise plusieurs canaux : Sprint Reviews hebdomadaires en présentiel via Google Meet avec ordre du jour structuré, démo Preview/Prod, décisions documentées et prochaines étapes claires. En asynchrone : emails pour les CR formels et jalons, Trello pour les commentaires et checklists, GitHub pour les discussions techniques. La documentation passe par le README pour l'architecture et scripts, les Issues pour les spécifications détaillées, et les PR pour le contexte et review.

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

Maintenant, passons à la démonstration pratique. Je vais vous présenter deux scénarios : visiteur et administrateur.

**Scénario Visiteur** (4 minutes)

Je me rends sur le site en production : dietetique-et-interventions.manonchaillou.fr

[Navigation sur le site]

Vous voyez l'accueil avec une présentation claire des services. Le site est entièrement responsive, comme vous pouvez le constater en redimensionnant la fenêtre.

Je navigue vers "Prestations" pour voir le détail des services proposés. Le SEO est optimisé avec des meta descriptions et une structure sémantique.

Maintenant, dirigeons-nous vers "Contact". Voici le formulaire avec validation en temps réel. Je vais remplir les champs requis : nom, prénom, email, téléphone, et message.

Pour les pièces jointes, je peux ajouter jusqu'à 3 fichiers de maximum 4MB chacun. Les types acceptés sont jpg, png et pdf. Regardez, si j'essaie d'ajouter un 4ème fichier, le système me l'interdit. Si j'ajoute un fichier trop volumineux ou d'un mauvais type, j'ai une validation côté client.

[Démonstration upload de fichiers]

Une fois le formulaire soumis, vous voyez le message de succès et la diététicienne reçoit automatiquement un email via Resend avec toutes les informations et les pièces jointes.

**Scénario Administrateur** (4 minutes)

Maintenant, connectons-nous à l'interface d'administration avec le compte test : jury@ynov.com, mot de passe : d85pm832

[Connexion au dashboard]

Voici le dashboard administrateur. L'authentification est gérée par Better Auth avec des rôles. Seuls les utilisateurs autorisés peuvent accéder à cette interface.

Dans "Contact Requests", je vois la liste de toutes les demandes avec plusieurs informations : nom, email, date de création, statut, et actions possibles.

Je peux filtrer par statut : Nouveau, En cours, Traité, Archivé. La recherche fonctionne sur le nom et l'email. Le tri est possible sur toutes les colonnes.

[Démonstration des filtres et recherche]

Cliquons sur une demande pour voir le détail. J'ai accès à toutes les informations soumises : coordonnées complètes, message, et les pièces jointes téléchargeables.

Je peux changer le statut directement depuis cette interface. Par exemple, passer de "Nouveau" à "En cours", puis à "Traité". Chaque changement est tracé avec horodatage.

[Démonstration changement de statut]

L'archivage permet de masquer les anciennes demandes sans les supprimer, respectant ainsi les obligations de conservation RGPD.

La navigation est entièrement accessible au clavier, comme vous pouvez le voir, et tous les éléments interactifs ont des focus visibles conformes aux standards WCAG 2.1 AA.

---

## Critères de Validation et Conclusion (2 minutes)

Cette démonstration valide tous les critères fonctionnels : couverture des fonctionnalités attendues, robustesse avec validation et gestion d'erreurs, traçabilité avec statuts et archives.

Les critères techniques sont respectés : accessibilité avec navigation clavier et focus, performance avec réactivité UI, sécurité avec authentification et validation.

Les critères qualité incluent une UX fluide, un design responsive mobile/desktop, un SEO optimisé, et un code maintenable et testé.

Cette "version utilisable" a été validée par la commanditaire et répond aux objectifs fixés.

**Conclusion**

Ce projet de 3 mois m'a permis de démontrer ma capacité à coordonner et piloter un projet de développement complet, de la planification à la livraison.

J'ai adapté avec succès la méthodologie Scrum à un contexte solo, maintenu une qualité élevée avec 0 erreur en production, respecté les délais avec 6 sprints livrés, et maîtrisé les coûts en restant dans les paliers gratuits.

Les compétences du référentiel sont toutes couvertes avec des preuves concrètes : planification rigoureuse, pilotage par indicateurs, arbitrage documenté, management adaptatif, développement des compétences, et suivi client régulier.

Le site est en production, utilisé quotidiennement, et prêt pour les évolutions futures planifiées.

Je vous remercie pour votre attention et reste à votre disposition pour vos questions.

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
