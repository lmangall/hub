---
type: scope-doc
project: business-school
client: alix
sent_by: alix-or-quentin
received_at: 2026-05-12
source_file: Kickoff Brief Build 2.pdf
aliases: [kickoff-brief-alix, Kickoff Brief Build 2, Build 2 brief]
---

> **Source**: PDF received 2026-05-12 11:25 (in Léonard's Downloads, transcribed). Companion doc to [[roadmap-alix]] — this one has the **contract context, pricing tiers, exclusions, and long-term vision** that the roadmap-alix.md doesn't cover.

# Brief de Kickoff — Build #2 · 60 Jours

**Refs**:
- MOCKUP V2: <https://astroaimockup-mophqjds.manus.space/>
- Chartes astrologie: <https://astro-charts.com/>
- Autre exemple pro: <https://www.astrogold.io/>

## Trois priorités

1. **Les chartes en un seul endroit** — visualisation qui remplace les logiciels externes, surtout pour le thème astral
2. **Des agents IA véritablement performants** — lectures profondes, pas de réponses génériques
3. **Mon Entourage** — gestion des profils des personnes autour de soi avec toutes leurs chartes

**Cible commerciale**: abonnement à **30 €/mois**, objectif **1 000 abonnés actifs** = **30 000 €/mois MRR**.

## Contexte & intention

Document de synthèse du périmètre contractuel signé (**contrat 42Lab × AR International, signé le 20 avril 2026, kickoff décalé au 4 mai 2026**).

**Objectif commercial du Build #2**: 1 000 abonnées payantes à ~30 €/mois le plus vite possible après lancement.

### Dates clés du contrat

| Étape | Date | Montant |
|-------|------|---------|
| Démarrage / Kickoff | 4 mai 2026 | 8 700 € HT (30%) |
| Mi-parcours | 3 juin 2026 | 11 600 € HT (40%) |
| Livraison finale | 3 juillet 2026 | 8 700 € HT (30%) |
| Fin maintenance | 3 août 2026 | Inclus |

**Total contrat**: ~29 000 € HT.

---

## Partie 1 — Scope contractuel (signé et engagé)

**8 modules contractuellement inclus**, base non négociable.

### Module 1 — Rebranding & Transformation SaaS
Nouveau branding neutre, nouveau domaine, redirection, page d'accueil publique, inscription ouverte à tous. **Critère**: nouvelle utilisatrice crée un compte en < 2 min, sans aucune référence "Business School".

### Module 2 — Système d'abonnements & Paiements Stripe
Checkout, gestion cycle de vie, facturation auto, période d'essai, dashboard admin (MRR, churn, abonnements actifs, LTV).

**Structure tarifaire validée**:

| Plan | Prix | Essai | Contenu |
|------|------|-------|---------|
| **Essentiel** | **19 €/mois** | **7 jours gratuits** (CB requise, prélèvement auto après 7 jours) | Toutes chartes (astro/HD/numéro/Gene Keys), tous agents IA, Mon Entourage (5 profils max) |
| **Pro** | ~29 €/mois | non | Tout Essentiel + Mon Entourage illimité, transits planétaires, astrocartographie, Planning Cosmique |
| **Business** | ~49 €/mois | non | Tout Pro + accès LMS formations exclusives, rapports PDF brandés, espace praticien |

*Note Essentiel*: 7 jours d'accès intégral, prélèvement 20 €/mois si non annulé avant J7. Annulation self-service à tout moment.

### Module 3 — Mon Entourage (Viralité & Affiliation)
Profils proches/amis/clientes, invitations, matching de compatibilité, dashboard réseau, affiliation avec commissions. **Critère**: inviter 3 proches, voir le matching, être créditée si une souscrit.

### Module 4 — Réorganisation des Agents IA
**6 agents spécialisés et personnifiés**: Astrologie, Numérologie, Gene Keys, Human Design, Astrocartographie, Business Coach. Un seul flux conversationnel par agent. **Critère**: choisir un agent, obtenir analyse approfondie sans changer d'onglet.

### Module 5 — LMS
Admin LMS (cours/sections/modules), multi-format (vidéo/texte/e-books/podcasts/YouTube/Vimeo/Wistia), droits granulaires (BS / SaaS / verrouillé / invisible), suivi progression, attribution par plan.

### Module 6 — Gestion des Droits & Niveaux d'Accès
4 niveaux: Abonnée SaaS / Cliente Business School / Coachs / Admin. Règles configurables, base partagée, transition fluide.

### Module 7 — API Externe Headless
API RESTful (chartes + agents conversationnels), gestion utilisateurs/stockage/historique, auth par clé + rate limiting, dashboard partenaire, facturation MAU.

### Module 8 — Nouvelles Chartes (Astrocartographie & Transits)
Charte astrocartographique (lignes planétaires par lieu), transits planétaires, intégration agents, visualisation timeline.

---

## Partie 2 — Priorités absolues (semaines 1-3)

À traiter en priorité absolue avant les fonctionnalités secondaires.

### Priorité 1 — Roue natale de qualité professionnelle (niveau Astro.com)

**Problème actuel**: V1 affiche une roue moins lisible que les sites pro. Les utilisatrices continuent d'utiliser Astro.com ou Astro-Seek séparément. Promesse "tous les chartes en un seul endroit" non tenue.

**Attendu Build #2**:
- Roue natale SVG générée dynamiquement
- Calcul astronomique précis: **Swiss Ephemeris** recommandé (open-source, utilisé par Astro.com)
- Système de maisons **Placidus** par défaut, option Koch / Whole Sign / etc.
- Affichage complet: 10 planètes + Nœud Nord/Sud + Chiron + Lilith, glyphes planétaires et zodiacaux, degrés et minutes, numérotation 12 maisons, cuspides (lignes pointillées intermédiaires, pleines pour ASC/DSC/MC/IC), lignes d'aspects colorées par type (conjonction, opposition, trigone, carré, sextile, quinconce)
- Légende des aspects intégrée sous la roue
- Export PNG et PDF
- Tableau positions planétaires à côté de la roue (signe, degré, maison, rétrograde)

**Note technique**: Swiss Ephemeris dispo Python (`pyswisseph`) + JS (`swisseph` npm). Alternative API externe: AstrologyAPI.com (charte natale, transits, synastrie). **Décision technique en S1**.

### Priorité 2 — Agents IA avec injection complète du contexte des chartes

**Problème actuel**: agents répondent de manière générique. Ils ne "connaissent" pas l'utilisatrice.

**Attendu**:
- À chaque conversation: contexte enrichi automatiquement avec positions planétaires, maisons, aspects, type HD, profil, autorité, centres définis/ouverts, canaux, portes actives, chemin de vie numérologique, Gene Keys d'activation, transits actuels
- Réponses précises sans re-saisie
- Personnalisées et non génériques
- Mémoire conversation persistante (intra et idéalement inter-session)

**Note technique**: contexte injecté via system prompt LLM. Template par agent avec variables dynamiques. Prompt engineering critique.

**Demande**: évaluer si le modèle LLM actuel est suffisamment performant; sinon explorer fine-tuning ou modèle plus puissant (Claude 3.5 Sonnet, GPT-4o). **Qualité agents = facteur de rétention n°1**.

### Priorité 3 — Mon Entourage avec toutes les chartes calculées par profil

**Attendu**:
- Création d'un profil → toutes les chartes calculées automatiquement (astro, numéro, HD, Gene Keys)
- Page profil affiche les 4 chartes complètes en onglets
- Bouton **"Lecture Croisée"** lance une analyse de synthèse par l'Oracle (agent maître)
- Matching de compatibilité entre 2 profils: synastrie astrologique simplifiée, compatibilité HD (canaux complémentaires, centres qui s'activent mutuellement), Gene Keys en résonance, dynamique numérologique

---

## Partie 3 — Fonctionnalités différenciantes (au-delà du contrat, à intégrer si validées au kickoff)

### A — Agent Oracle: Maître des Chartes (synthèse cross-systèmes)

**7ème agent** (distinct des 6 spécialisés) dont la mission exclusive est de **croiser tous les systèmes** pour produire une lecture unifiée.

Ce qu'il fait que les autres ne font pas: identifie thèmes apparaissant dans plusieurs systèmes (ex: *"ton Soleil Lion + ton type Projecteur + ton Chemin de Vie 9 + ta Porte 1 disent tous la même chose — tu es ici pour maîtriser quelque chose en profondeur avant de le transmettre"*), révèle contradictions apparentes et les résout, produit un "portrait d'âme" synthétique sauvegardable et partageable.

### B — Planning Cosmique Personnel *(si on a le temps)*

Page timeline annuelle personnalisée: événements collectifs (rétrogrades, éclipses, planètes lentes) croisés avec cycles personnels (transits, année numérologique, phases du design).

Contenu minimum: timeline 12 mois nav mensuelle, rétrogrades Mercure (pré-shadow/rétro/post-shadow), éclipses, mouvements Jupiter/Saturne/Nœud Nord, année personnelle, transits majeurs (Jupiter/Saturne/Uranus/Neptune/Pluton), conseils personnalisés selon type HD.

### D — Rapport PDF de lecture pour praticiens (plan Business)

Utilisatrices plan Business génèrent rapport PDF complet pour un profil de leur entourage: roue natale, bodygraph HD, profil numérologique, Gene Keys, lecture IA Oracle (éditable avant export), logo + coordonnées de la praticienne.

Généré côté serveur (**Puppeteer ou WeasyPrint**), téléchargeable depuis l'app. **Justifie à lui seul l'abonnement Business à 49 €/mois**.

### E — Carte de Relation avec lien de partage viral

Compare 2 profils Mon Entourage → "Carte de Relation" visuelle (résonance, friction, thème). Partageable via lien public unique (valable 30 jours). La personne qui reçoit voit aperçu + invitation à créer compte. **Mécanisme de croissance organique le plus puissant** — chaque utilisatrice devient vecteur d'acquisition.

---

## Partie 4 — Exclus du Build #2 (rappel contractuel)

**Pas dans les 60 jours**:
- Agent "Alix AI" personnifié (voix/style d'Alix)
- Intégration WhatsApp ou messageries externes
- Connecteurs Notion / Google Calendar
- Roadmap d'actions personnalisée post-onboarding
- Application mobile native (iOS/Android)
- Fonctionnalités communautaires (forum, messagerie entre utilisatrices)

---

## Partie 6 — Roadmap proposée 60 jours

| Semaine | Phase | Livrables prioritaires |
|---------|-------|------------------------|
| S1 | Fondations & Décisions techniques | Choix moteur calcul astro, schéma DB finalisé, design system V2, setup Stripe, nouveau domaine, décision modèle LLM |
| S2 | Rebranding + Roue natale (P1) | Nouveau branding déployé, inscription publique ouverte, **roue natale SVG fonctionnelle** avec Swiss Ephemeris, système de rôles |
| S3 | Abonnements + Agents IA (P2) | Checkout Stripe 3 plans, dashboard admin MRR, **agents IA avec injection complète du contexte**, Oracle (7ème agent) |
| S4 | Mon Entourage (P3) + Viralité | Profils avec toutes les chartes calculées, invitations, **Carte de Relation + lien de partage**, programme d'affiliation |
| S5 | API + Nouvelles chartes | API headless documentée, astrocartographie, transits, Planning Cosmique personnel |
| S6 | LMS + Droits d'accès | Admin LMS, contenus multi-format, droits granulaires, rapport PDF praticien (plan Business) |
| S7 | Entrée vocale + Polish UX | Microphone Whisper sur tous agents, UX polish, responsive, edge cases |
| S8 | Intégration & Tests | Tests end-to-end, correction bugs, optimisation performances |
| S9 | Pré-prod & Lancement | Deploy production, monitoring, formation, go-live |

> **Diff vs Quentin's [[roadmap-alix]] (2026-05-11)**: this brief has API+chartes on S5, LMS on S6, voice on S7 — Quentin's has agents+API parallel S5-6, LMS+chartes S7, no explicit voice slot. **Reconcile at kickoff.**

---

## Résumé exécutif

Build #2 doit livrer **tous les systèmes de connaissance de soi (astro, HD, numéro, Gene Keys) en un seul endroit, avec des agents IA qui connaissent réellement l'utilisatrice**. C'est la raison pour laquelle les utilisatrices paieront 30 €/mois et ne partiront pas.

3 différenciateurs:
- Qualité roue natale (niveau Astro.com)
- Pertinence agents IA (vraies données, pas générique)
- Viralité Mon Entourage (utilisatrice → ambassadrice naturelle)

---

## Partie 7 — Vision produit long terme (Build #3+)

*Non engagé pour Build #2 mais à anticiper architecturalement.*

**Objectif 12 mois**: 1 000 abonnées à 30 €/mois = **30 000 €/mois MRR**.

### Vision 1 — Le Miroir Vivant (biométrie cosmique personnalisée)
Check-in 30s chaque matin (énergie, humeur, focus). Après 30 jours, Oracle identifie patterns personnels en croisant ces données avec transits planétaires réels. *"Les lundis avec la Lune en Capricorne, tu rapportes systématiquement un niveau d'énergie bas. Évite de planifier des appels de vente ces jours-là."*

**Impact archi**: table `daily_checkins(user_id, date, energy_level, mood, focus, notes)` + moteur de corrélation. **À prévoir dès Build #2.**

### Vision 2 — Le Journal de Vie Cosmique
Oracle génère automatiquement rapport hebdo (dimanche soir) et mensuel (1er du mois). Croise transits + check-ins + événements partagés. Au bout d'un an, archive corrélée — **switching costs naturels**.

### Vision 3 — L'Espace Praticien Professionnel
Outil de travail pour astrologues / praticiens HD / coachs. **Segment prêt à payer 49–99 €/mois.**
- Séparation "Mon Profil" / "Mes Clients"
- Rapports PDF brandés (logo, couleurs praticienne)
- Notes session privées par client
- Agenda cosmique clients (transits majeurs sur le mois): *"3 de tes clients ont Jupiter sur leur Soleil ce mois"*
- Templates réutilisables ("Lecture démarrage business", "Lecture compatibilité")

### Vision 4 — Le Briefing Cosmique Matinal Vocal
Bouton "Mon briefing du jour" → Oracle parle 60–90s: transits du jour, énergie lunaire, conseil personnalisé, rappel prochain événement. **OpenAI TTS**, voix Alloy/Nova en français, ~0,0075 $/utilisatrice/jour (~225 $/mois pour 1k actives).

**Dans 12–18 mois, les interfaces vocales deviendront la norme pour les outils d'IA.**

### Vision 5 — La Mémoire Long-Terme de l'Oracle
Oracle se souvient de tout (projets, peurs, questions récurrentes). *"Il y a 3 mois, tu m'avais parlé de ce projet — voici comment les transits actuels l'éclairent différemment."* **DB vectorielle** (Pinecone/Weaviate/pgvector).

**Impact archi**: décision Build #2 sur stockage conversations (format + indexation). **À anticiper dès maintenant.**

### Vision 6 — Croissance virale par Carte de Relation
Si chaque utilisatrice amène 0,3 nouvelle/mois, base double tous les 3-4 mois sans dépenses pub.

---

## Note d'architecture pour l'équipe technique

Décisions à prendre dès Build #2 pour ne pas se bloquer pour Build #3:

| Décision | Impact | Recommandation |
|----------|--------|----------------|
| Schéma DB check-ins quotidiens | Table `daily_checkins(user_id, date, energy, mood, focus)` | Créer la table vide dès Build #2 |
| Stockage positions planétaires par date | Cache pour éviter recalcul | Table `ephemeris_cache(date, planète, position)` |
| Format conversations Oracle | Queryable par similarité sémantique | Champ `embedding` ou table dédiée |
| Architecture rapports automatiques | Jobs cron hebdo/mensuel par utilisatrice | Prévoir infra de jobs asynchrones |
| Notifications push | Briefing matinal + alertes | Intégrer dès Build #2 (ex: Firebase Cloud Messaging) |
