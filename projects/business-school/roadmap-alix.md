---
type: scope-doc
project: business-school
client: alix
sent_by: quentin
sent_at: 2026-05-11
slack_source: https://42lab.slack.com/files/U09PR0HB4E8/F0B315W164A/roadmap-alix.md
aliases: [roadmap-alix, Roadmap Alix, Scope détaillé Alix]
---

> **Source**: [[quentin|Quentin]] sent in DM 2026-05-11 16:29 — [Slack file](https://42lab.slack.com/files/U09PR0HB4E8/F0B315W164A/roadmap-alix.md). Canonical scope doc for [[business-school|Alix V2]] Build 60 jours.

# Scope détaillé Alix

> **Note importante :** Cette V2 s'intègre dans la plateforme existante. Elle réutilise la base de données, l'authentification, l'infrastructure et les modules déjà en place (chartes, agents IA, profils utilisatrices). Le travail inclut la transformation de la plateforme en SaaS public tout en préservant l'expérience des clientes Business School actuelles.

#### Module 1 : Rebranding & Transformation SaaS

Transformer la plateforme actuelle en un produit indépendant, accessible à tous.

- Nouveau branding neutre (retrait logo et nom "Business School", charte graphique universelle)
- Nouveau nom de domaine dédié
- Redirection transparente depuis l'ancien domaine
- Page d'accueil publique avec présentation de la plateforme
- Inscription ouverte à tous (plus besoin d'être cliente Business School)

**Critère d'acceptation** : Une nouvelle utilisatrice peut découvrir la plateforme, comprendre la proposition de valeur, et créer un compte en moins de 2 minutes — sans aucune référence à Business School.

---

#### Module 2 : Système d'abonnements & Paiements (Stripe)

Monétiser la plateforme avec des abonnements récurrents.

- Intégration Stripe complète (checkout, gestion abonnements, webhooks)
- Plans d'abonnement configurables depuis l'admin (nom, prix, périodicité, fonctionnalités incluses)
- Page de pricing publique dynamique (1 à 3 plans)
- Gestion du cycle de vie : inscription, upgrade, downgrade, annulation, relance
- Factures automatiques
- Période d'essai configurable (ex : 7 jours gratuits)
- Dashboard admin : MRR, churn, abonnements actifs, LTV

**Critère d'acceptation** : Une utilisatrice peut souscrire un abonnement, accéder aux fonctionnalités correspondantes, upgrader/downgrader, et annuler — le tout en self-service.

---

#### Module 3 : Mon Entourage — Viralité

Le moteur de croissance de la plateforme : chaque utilisatrice invite son réseau.

- Chaque utilisatrice peut créer des profils pour ses proches, amis, clientes
- Catégories de profils : Famille, Amis, Business/Clientes, Custom
- Invitation par lien unique ou email — la personne invitée peut créer son propre compte
- Matching entre profils : compatibilité, atomes crochus, dynamiques relationnelles
- Dashboard "Mon Entourage" : visualisation du réseau, statut des invitations
- Données privées protégées (jardin secret) — seules les données de croisement sont partagées

**Critère d'acceptation** : Une utilisatrice peut inviter 3 proches, créer leur profil et voir le matching entre eux.

![Mon Entourage — visualisation du réseau et matching](/mon-entourage.png)

---

#### Module 4 : Réorganisation des Agents IA

Simplifier et spécialiser les agents pour une meilleure expérience utilisateur.

- Remplacement de la navigation multi-onglets par des agents clairement identifiés et spécialisés
- Agents prévus :
  - **Agent Astrologie** : lecture et interprétation de charte astrale
  - **Agent Numérologie** : analyse numérologique complète
  - **Agent Gene Keys** : interprétation des Gene Keys
  - **Agent Human Design** : lecture du profil Human Design
  - **Agent Astrocartographie** : analyse des lignes planétaires par lieu
  - **Agent Business Coach** : guidance stratégique basée sur les chartes
  - **Agent "Alix AI"** (optionnel) : IA entraînée sur ta façon de penser, parler, coacher
- Personnification de chaque agent (avatar, prénom, personnalité)
- Un seul flux conversationnel par agent (plus de changement d'onglet)

**Critère d'acceptation** : Une utilisatrice peut choisir un agent spécialisé, démarrer une conversation, et obtenir une analyse approfondie sans jamais changer d'onglet ni se demander "quel agent utiliser".

---

#### Module 5 : LMS — Modules de Formation Intégrés

Centraliser les contenus éducationnels directement dans la plateforme.

- Module d'administration LMS : créer des cours, sections, modules en quelques clics
- Support vidéo, texte, e-books, podcasts, liens externes (ex: YouTube)
- Système de droits d'accès granulaire :
  - Contenus réservés aux clientes Business School
  - Contenus accessibles aux abonnées SaaS (vidéos explicatives, tutoriels)
  - Contenus verrouillés avec CTA configurable ("Prenez un call pour débloquer cet accès")
  - Contenus invisibles (pas affichés du tout selon le profil)
- Progression par module (suivi complétion)
- Attribution par programme : tu décides quel contenu va sur quel plan

**Critère d'acceptation** : Tu peux créer un cours avec 5 modules vidéo, l'attribuer uniquement aux clientes Business School, et vérifier qu'une abonnée SaaS standard ne le voit pas du tout.

---

#### Module 6 : Gestion des Droits & Niveaux d'Accès

Le système qui fait cohabiter Business School et SaaS public sur une même plateforme.

- Profils utilisateur avec niveaux : Abonnée SaaS / Cliente Business School / Coachs / Admin
- Règles d'accès configurables depuis l'admin (si programme X → accès à Y)
- Une seule base de données partagée : une cliente qui passe de SaaS à Business School garde toutes ses données
- Transition fluide : pas de nouveau compte à créer
- Options de visibilité par fonctionnalité : visible + accessible / visible + verrouillé (CTA) / invisible

**Critère d'acceptation** : Une utilisatrice SaaS qui rejoint la Business School voit ses nouveaux contenus apparaître automatiquement sans créer de nouveau compte.

---

#### Module 7 : API Externe

Ouvrir la plateforme à des partenaires techniques.

- API RESTful documentée pour accès aux données de chartes
- Accès aux agents IA via API
- Authentification par clé API + rate limiting
- Dashboard partenaire : suivi de consommation, clés API, documentation
- Système de facturation API

**Critère d'acceptation** : Un développeur externe peut générer une charte complète et interroger un agent IA via l'API avec sa clé, en suivant la documentation.

#### Comment l'API fonctionne

L'API est conçue pour être **headless** — un partenaire technique peut intégrer toute la puissance de ta plateforme dans son propre produit, sans que ses utilisateurs ne voient jamais ta marque.

**Deux services principaux :**

**1. Chartes (création et consultation)**

```
POST /users → Créer un utilisateur (prénom, nom, date/heure/lieu de naissance)
  → Génère automatiquement toutes les chartes (astro, numéro, Gene Keys, HD...)
  → Retourne un user_id + statut de génération

GET /users/:id/charts → Récupérer les chartes d'un utilisateur
  → Les chartes sont générées une seule fois et stockées
  → Le partenaire les consulte autant de fois qu'il veut
```

**2. Agents IA (conversations contextuelles)**

```
POST /chat → Démarrer ou continuer une conversation
  → agent_type (obligatoire) : astro, numérologie, gene_keys, human_design...
  → user_id (obligatoire) : l'agent reçoit automatiquement les chartes en contexte
  → conversation_id (optionnel) : si absent = nouvelle conversation, si présent = suite
  → Retourne la réponse de l'agent + conversation_id pour continuer
```

**L'avantage majeur :** Le partenaire n'a pas à gérer la complexité des calculs astrologiques, des bases de connaissances, ni du contexte IA. Il envoie une date de naissance, il reçoit des chartes. Il envoie un message, il reçoit une réponse d'expert. Tout le savoir — ton RAG, tes prompts, tes connaissances — est encapsulé dans l'API.

#### Ce qu'on fournit clé en main

- **Documentation API complète et détaillée** : chaque endpoint documenté avec exemples de requêtes et réponses, guide de démarrage rapide, cas d'usage types
- **Console partenaire** : génération automatique des clés API, suivi de consommation en temps réel, gestion des credentials — le partenaire est 100% autonome
- **Zéro dépendance à toi** : tu n'as rien à gérer. Chaque partenaire est strictement indépendant — ses credentials, ses utilisateurs, sa facturation. Tu n'es jamais en support technique ni en intermédiaire. Tout est automatisé par la plateforme.

Et surtout : **tu prends en charge 100% des coûts d'infrastructure.** Les appels API vers les modèles IA (Claude, etc.), le stockage des chartes, l'historique des conversations, la puissance de calcul — tout est inclus dans le prix. Le partenaire n'a rien à gérer, rien à payer en plus. Messages illimités par utilisateur. C'est un argument de vente massif pour lui : il intègre une brique d'intelligence complète sans aucun coût technique variable.

#### Proposition de pricing API

Le pricing est **à l'utilisateur actif mensuel (MAU)**, pas à la requête. C'est premium, parce que la valeur délivrée est énorme — chaque MAU représente un utilisateur pour lequel le partenaire obtient des chartes complètes ET un accès conversationnel aux agents IA, avec tout le contexte.


| Tranche MAU         | Prix par MAU     | Exemple                                                                    |
| ------------------- | ---------------- | -------------------------------------------------------------------------- |
| **Minimum mensuel** | **250 EUR/mois** | Accès API + documentation + console + support. Inclut les 25 premiers MAU. |
| 26 — 200 MAU        | 5,00 EUR/MAU     | 200 MAU = 200 + (175 x 5) = **1 075 EUR/mois**                             |
| 201 — 1 000 MAU     | 4,00 EUR/MAU     | 1 000 MAU = 200 + 875 + 3 200 = **4 275 EUR/mois**                         |
| 1 001+ MAU          | 3,00 EUR/MAU     | 3 000 MAU = 200 + 875 + 3 200 + 6 000 = **10 275 EUR/mois**                |


**Un MAU = tu peux choisir ta propre définition, soit est considéré actif tant qu'il n'est pas passé inactif par API (dès qu'il est désabonné de la plateforme de ton partenaire) ou simplement est considéré actif un utilisateur unique pour lequel au moins une requête (charte ou chat) a été faite dans le mois.**

**Pourquoi ce pricing est justifié :**

- **Tous les coûts API IA sont inclus** : le partenaire ne paie jamais de token, jamais de surcharge. Messages illimités par utilisateur. C'est toi qui absorbes les coûts d'infrastructure — et c'est un argument de vente énorme pour le partenaire.
- **Minimum à 200 EUR/mois** : filtre les curieux, engage les partenaires sérieux
- **Dégressif** : le partenaire est récompensé quand il scale
- **Premium assumé** : 5 EUR/MAU, c'est le prix d'une intelligence complète (chartes + agents + contexte + historique). Le partenaire n'a rien à construire, rien à maintenir — il branche et ça marche.
- **Aligné avec la valeur** : chaque MAU est un client du partenaire qui tire de la valeur. S'il vend son produit 20 EUR/mois à son utilisateur, 5 EUR pour toi est une évidence.

---

#### Module 8 : Nouvelles Chartes — Astrocartographie & Transits

Enrichir l'offre avec de nouvelles analyses.

- Charte astrocartographique : lignes planétaires selon le lieu de naissance et les lieux de vie
- Transits planétaires : analyse des influences actuelles et à venir
- Intégration dans les agents IA correspondants
- Visualisation graphique des transits (timeline)

**Critère d'acceptation** : Une utilisatrice peut générer sa charte astrocartographique et voir les transits actuels directement dans son profil.


---

## Build 60 jours


| Semaine | Phase                              | Livrables                                                                                                                     | Pourquoi maintenant                                                        |
| ------- | ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| S1      | **Kick-off & Fondations**          | Specs finales, refonte schéma DB (rôles, plans, entourage), design system V2, setup Stripe, nouveau domaine                   | Fondation technique pour tout le reste                                     |
| S2      | **Rebranding & Droits d'accès**    | Nouveau branding déployé, inscription publique, système de rôles (SaaS / BS / Mastermind / Admin), redirection ancien domaine | **Le SaaS existe dès S2** — les utilisatrices peuvent s'inscrire           |
| S3      | **Abonnements Stripe**             | Checkout, page pricing 3 plans, gestion cycle de vie (upgrade/downgrade/cancel), dashboard admin MRR                          | **Le revenu démarre dès S3** — tu génères du MRR                           |
| S4      | **Mon Entourage + Affiliation**    | Profils proches/clientes, invitations, matching compatibilité, programme d'affiliation, dashboard commissions                 | **La machine d'acquisition tourne** — chaque utilisatrice amène son réseau |
| S5-6    | **Agents IA + API (en parallèle)** | 6-7 agents spécialisés et personnifiés + API headless documentée (chartes + chat), clés API, dashboard partenaire             | **Deux canaux de revenus en parallèle** — B2C (agents) + B2B (API)         |
| S7      | **LMS + Nouvelles chartes**        | Admin LMS, contenus multi-format, droits d'accès granulaires, astrocartographie, transits                                     | **Upsells activés** — contenus premium verrouillés = levier d'upgrade      |
| S8      | **Intégration & Polish**           | Intégration complète, UX polish, responsive, edge cases, tests end-to-end                                                     | Qualité = rétention                                                        |
| S9      | **Pré-prod & Lancement**           | Deploy prod, monitoring, formation, go-live                                                                                   | Live.                                                                      |
