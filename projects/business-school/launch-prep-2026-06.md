---
type: tracking-doc
status: active
side: pro
client: business-school
project: business-school
source: slack #business-school-ai (C0A773J15FF)
launch_target: 2026-06-26
ready-for-setup: 2026-06-16
compiled: 2026-06-10
last_checked: 2026-06-17 (session Léonard ↔ Alix)
last_checked_ts: "1781254381.950919"  # newest top-level msg (12-06 10:53 «pratique d'avoir les vraies clientes»); threads lus jusqu'à 12:27 (TS 1781260028.434779) — resume after this TS. NB: items #25–#30 (17-06) viennent d'une session/notes Léonard, pas du flux Slack — resume Slack toujours après le TS ci-dessus.
---

# AliXAi — Launch prep & to-do (Build #2)

Canonical source = Alix's **recap message 2026-06-09 21:23** ([Slack](https://42lab.slack.com/archives/C0A773J15FF/p1781033012964989)). Everything below is checked against the **`staging`** branch of `~/Repos/business_school_ai_platform`. Update/prune as items ship.

## 🏁 Quand un item passe à « Done » (process)

Quand un item de ce doc est implémenté, **avant de le clore** l'agent (Claude) doit demander à Léonard :

1. **Vérification** — lui dire **exactement quoi tester et où** : la route/page concernée (ex. `/charts/acg`), le geste précis et le résultat attendu (ex. « clique une ville → plus de message "aucune ligne", une mini-interprétation IA s'affiche à droite »). Jamais un « c'est fait » vague.

---

## Dates
- **26 juin (vendredi)** = target launch (Alix's proposal — she wants it before but must close her high-ticket sales first). *Quentin/today.md previously said 28 juin — align on 26.*
- **16 juin** = **NOT** feature-complete. It's the date to start **admin setup**: domain name + deploy on the domain, Google Admin Console, Stripe tests (Léonard reply [10 juin 08:08](https://42lab.slack.com/archives/C0A773J15FF/p1781071721264279)).
- **Après 3 juillet** (fin semaine de lancement) = Alix books her tech friend for the **API integration** call. Not a launch blocker.

---

## 🆕 Demandes 2026-06-11 (post-recap)

> Arrivées **après** le recap du 09-06 sur lequel ce doc est bâti. Détail verbatim (questions exactes des 7 agents, citations, permaliens) → **§ Détail / verbatim** en bas de page. Dernier message Slack lu : **2026-06-12 12:27** (threads inclus).

| # | Item | Size | Code status (staging) |
|---|------|------|------------------------|
| 12 | **Questions de départ pré-écrites éditables par agent** — Alix veut remplacer les 4 questions cliquables de chaque agent. Nouvelles fournies pour **les 7 agents** (Oracle, Astra, Vera, Clara, Noa, Luna, Ava — Luna + Ava ajoutés le 11-06 11:18/11:20). Léonard : « Oui bien sûr ». | 🟢 SMALL | ✅ **fait + poussé staging** (`891faf2`) — les 7 agents (Oracle, Astra, Vera, Clara, Noa, Luna, Ava) reçoivent les questions d'Alix **verbatim** dans `lib/constants/agents.ts`. Corrigé « Ma branding » → « Mon branding » ; « Les signes que je ne suis pas alignée ? » gardé tel quel (à smoother si Léonard veut). À vérifier sur `alix.42lab.co`. |
| 13 | **Micro vocal à droite** — déplacer le bouton micro (parler à l'IA) à **droite** de la barre de saisie, **partout dans l'appli** (comme ChatGPT/Manus). Léonard : « Oui bien sûr ». | 🟢 SMALL | ✅ **fait + poussé staging** (`cfa4937`) — micro déplacé dans un cluster à **droite**, juste avant Envoyer (`components/multimodal-input.tsx`) ; la pièce jointe reste à gauche. App-wide (input partagé, seul endroit du `VoiceInputButton`). À vérifier sur `alix.42lab.co`. |
| 14 | **Roue astro — placements plus lisibles** — glyphes des planètes/points (nœud nord, Pluton…) un peu plus grands + **bold** ; lignes de séparation des maisons plus **claires/légères** pour que les placements ressortent au premier coup d'œil. | 🟢 SMALL | ✅ **fait + poussé staging** (`8a05c88` + `c57ee4a`) — glyphes 17/14 → **22/19** (`astrology-section.tsx`), font-weight 700 → **800** + stroke faux-bold (`paintOrder`) ; cuspides de maisons non-angulaires **bien plus légères** (width 0.7→0.3, opacity 0.6→0.16, dash plus espacé) tandis que les axes ASC/MC/DSC/IC sont **renforcés** (opacity 0.9). Hover : glyphe actif grossit (+4) + stroke épais + halo doré annelé, les autres tombent à 0.12, glyphe actif reste **brun foncé (bronze)** pour contraster sur le halo. À vérifier sur `alix.42lab.co`. |
| 15 | **Panneau « Positions planétaires »** — (a) liste plus **grande/lisible** (degrés bien visibles) ; (b) **ajouter Ascendant + MC** à la liste ; (c) **bug : maison « cropped »** (Saturne/Uranus/Neptune affichent « … » au lieu de la maison). Léonard : « Ok ça marche » + « je vais le corriger aussi ». | 🟠 SMALL–MED | ✅ **fait + poussé staging** (`8a05c88`) — (a) texte agrandi (nom `text-xs`→`text-sm`, méta `text-[10px]`→`text-[11px]`) ; (c) **`truncate` retiré** sur la ligne signe+degré+maison → plus de crop maison ; (b) **section « Axes »** ajoutée avec **ASC + MC** (signe + degré). `orbital-lanes-chart.tsx`. À vérifier sur `alix.42lab.co`. |
| 16 | **Typo numérologie** — mettre « année personnelle » + « mois personnel » dans la **même Poppins bold** que « chemin de vie » / « désir de l'âme ». (Léonard 👌) | 🟢 SMALL | ✅ **fait + poussé staging** (`36013ae`) — « Année personnelle » / « Mois personnel » passés en **Poppins bold text-base** (span `font-sans` direct qui bat le `font-heading` hérité du `CardTitle`), même rendu que « chemin de vie ». `components/charts/numerology-summary.tsx`. À vérifier sur `alix.42lab.co`. |
| 17 | **Menu agents — spécialité entre parenthèses** — ex. « Astra (Astrologie) », « Noa (Numérologie) » (elle-même ne sait pas encore qui est qui). (Léonard 👌) | 🟢 SMALL | ✅ **fait + poussé staging** (`460a6bb`) — nom + domaine entre parenthèses (muted, plus petit, `truncate`) dans `components/v2/sidebar.tsx` : « Astra (Astrologie) », « Noa (Numérologie) », « Luna (Astrologie géographique) »… À vérifier sur `alix.42lab.co`. |
| 18 | **Astro-géo — un box par transit** — elle voit le même transit (« Pluton opposé Jupiter ») répété ~9× (1 box/semaine). Veut **1 box par transit** avec les **dates complètes de la fenêtre** (début–fin). | 🟠 MED | `app/(dashboard)/charts/acg/acg-info-panel.tsx` — `TransitView` mappe `activatedLines` l.~528–577 (entrées par semaine/snapshot, non dédupliquées) ; carte = `acg/active-transit-card.tsx`. Dédupliquer par transit. |
| 19 | **« Juin » caché derrière les points** — le mois est encore partiellement masqué par les points (déjà signalé le 02-06). | 🟢 SMALL | ✅ **fait + poussé staging** (`8a05c88`) — cause trouvée : timeline `/transits` (`app/(dashboard)/transits/page.tsx`), le label date (right-edge à 90px) affleurait la pastille du transit majeur. Fix : `paddingRight: 24` sur le label → le mois ne passe plus derrière la pastille. (Ce n'était pas `upcoming-transit.tsx`.) À vérifier sur `alix.42lab.co/transits`. |
| 20 | **Astro-géo — refonte panneau « Croisements »** (Léonard, 11-06) : dédupliquer les croisements (variantes ASC/DSC = même texte) + cartes compactes repliables ; bouton IA **au-dessus** du panneau, reformulé « Luna, que vaut ce lieu pour moi ? » ; interprétation inline signée **Luna** + nourrie des lieux enregistrés. | 🟠 MED | ✅ **fait + poussé staging** (`00254ca`) — `acg-info-panel.tsx` (dédup `useMemo`, `CrossingCard` repliable, reorder, ChevronDown) + `acg-interpretation.ts` (persona Luna + `savedPlaces`). À vérifier sur `alix.42lab.co` une fois le build vert. |
| 21 | **Boxes agents inégales sur la home** (`alix.42lab.co/`) — le fix equal-height #7 ne couvrait que le grid `/agents`, **pas le carousel agents du tableau de bord d'accueil**. Alix (12-06, capture `F0BA48RTMNE`) : « sur mon macbook les agents s'affichent encore à des tailles différentes ». Léonard en thread : « je vais le régler là-bas aussi ». | 🟢 SMALL | ✅ **fait + poussé staging** (`94cc732`) — cause : wrapper `<Link>` des cartes en `display:block` (annulait `flex:0 0 280px` + bloquait l'étirement vertical). Passé en `flex` + `items-stretch` sur le rail → cartes même largeur (280) **et** même hauteur. `components/dashboard/guides-carousel.tsx` ; `tsc --noEmit` exit 0 ; 1 warning lint **pré-existant** (`import type React`, déjà sur HEAD). À vérifier sur `alix.42lab.co/` une fois le build vert. |
| 22 | **Whole Signs (système de maisons astro)** — Alix (12-06) : « c'est trop tard pour rendre le système whole signs ? ». **Double signal** : élève astrologue (20 ans, prof Gene Keys) « embêtée par les réponses » à cause de **Placidus**. Léonard s'est **engagé** (« j'ai déjà des fondations »). | 🟠 MED | **À FAIRE** — toggle Placidus ↔ Whole Signs : cuspides (maison = signe entier), remap maisons des planètes, roue (`orbital-lanes-chart.tsx`), panneau positions, cohérence prompts IA. Détail → § verbatim. |
| 23 | **Transits mis en avant (effet WOW / usage quotidien)** — 2 retours clientes citent les transits comme LA raison de s'abonner : (a) transits dans les **portes HD** + impact énergie ; (b) **conseils numéro du mois** ; (c) surfacer davantage au quotidien. | 🟠 MED (a) · 🟢🟠 (b) · produit (c) | **À FAIRE / partiel** — base existe (`today-energy.tsx`, `/transits`). Détail → § verbatim. |

---

## 🆕 Demandes 2026-06-17 (session Léonard ↔ Alix)

> Issues d'une session de travail 2026-06-17 (notes Léonard, pas un permalien Slack). **Code status non vérifié contre `staging`** pour les items net-new ci-dessous — à confirmer dans `~/Repos/business_school_ai_platform` avant de chiffrer fermement. Plusieurs items recadrent des features déjà au tableau (#1 LMS, #2 Webinaires, #3 Affiliation) — voir « Mises à jour » dessous.

| # | Item | Size | Statut |
|---|------|------|--------|
| 25 | **Bibliothèque de prompts** — page dédiée, prompts **catégorisés par agent**. Alix dispose d'un **e-book de prompts** à intégrer. | 🟠 MED | **À FAIRE / net-new** — page catalogue + données prompts (depuis l'e-book). Distinct de la box Oracle embarquée dans le cours Prompts (#1 LMS). |
| 26 | **Optimisation mobile** 🔴 — la **navigation mobile n'est pas fonctionnelle** à ce stade : le **menu latéral est inaccessible**. Bloquant pour l'usage mobile. | 🔴 BIG | **À FAIRE / net-new** — sidebar/drawer mobile cassé (`components/v2/sidebar.tsx` ?). Pré-requis du flow mobile #30. |
| 27 | **Onboarding de présentation de la plateforme** — parcours guidé qui **présente la plateforme** à la première connexion (découverte des agents / chartes / sections). | 🟠 MED | **À FAIRE / net-new** — rejoint le critère d'acceptation Module 1 du scope (`roadmap-alix.md`) : nouvelle utilisatrice comprend la proposition de valeur en < 2 min. |
| 28 | **Pages légales** — CGU + politique de confidentialité + **mentions légales**. **Bloquant lancement public** (SaaS payant + ads FR). | 🟢 SMALL | ✅ **CODE FAIT — [PR #9](https://github.com/42Lab-co/business_school_ai_platform/pull/9) → staging** (`legal/mentions-legales`). (a) ✅ page `/mentions-legales` créée (groupe `(auth)` public, même layout que cgu/privacy) ; (c) ✅ « Mentions légales » liée dans les **deux** footers (public + in-app — le footer in-app liait déjà CGU+privacy). **Reste côté Alix** : ⚠️ (1) **remplir les placeholders légaux** de la page mentions légales (`[RAISON SOCIALE]`, `[FORME JURIDIQUE]`, `[CAPITAL SOCIAL]`, `[ADRESSE SIÈGE]`, `[SIRET]`, `[N° TVA]`, `[DIRECTEUR PUBLICATION]`) — non inventés ; (2) **validation juriste du contenu CGU/privacy** (réel, pas lorem, mais gaps signalés dans la PR : identité éditeur absente de la privacy, pas de clause droit applicable/juridiction ni prix/rétractation dans les CGU, transferts hors-UE Anthropic/Vercel à cadrer RGPD, pas de DPO postal, tutoiement/vouvoiement incohérent, « dernière mise à jour » = `new Date()` toujours la date du jour). |
| 29 | **Programme d'ambassadrices — affiliation externe (plateforme SaaS dédiée)** — **auto-payout**, **dashboard affiliée**, **lien tracké Stripe**, **paliers de commission**. Recadre le modèle interne #3b. | 🔴 BIG | **DÉCISION build vs buy** — adopter une plateforme d'affiliation SaaS dédiée (type Rewardful / FirstPromoter / PartnerStack branchée sur Stripe) plutôt que construire le payout %/dashboard en interne. Supersède la piste #3b « 8% trimestriel » fait maison. À trancher avec Alix. |
| 30 | 📈 **Flow mobile « contexte social » (dîner, événement)** — **ajout rapide d'un contact**, **affichage QR code**, **invitation par email en temps réel**. **Proposé par Léonard** sur la base du cas d'usage d'Alix — **accueil très positif**. | 🟠 MED | **À FAIRE / net-new** — dépend de #26 (nav mobile). Capture rapide de lead en mobilité (QR + invite email instantanée). |
| 31 | **Admin — « dernière connexion » par utilisatrice** — les admins doivent voir **quand chaque utilisatrice s'est connectée pour la dernière fois** (suivi d'activation / churn). | 🟢🟠 SMALL–MED | **À FAIRE / net-new** — capturer `lastSignInAt` (Better Auth session ?) + colonne dans la liste admin des utilisatrices. Vérifier si la donnée est déjà persistée. |
| 32 | **Accès gratuit à l'application (comptes d'essai)** — prévoir un moyen (ex. **URL dédiée**) pour qu'Alix **crée des comptes d'essai gratuits** pour des prospects. Le **flow reste à décider** (avec ou sans carte bancaire) — **proposer les options à Alix**. | 🟠 MED | **À FAIRE + DÉCISION flow** — recoupe #5a (essai 7j), #5c (Fondatrices comp), #3a (VIP comp). À cadrer : (a) trial CB-required vs no-CB ; (b) lien d'invitation / comptes comped générés par Alix. Présenter 2-3 options à Alix. |

**Mises à jour d'items existants :**
- **#1 LMS** — préciser : **déblocage des leçons l'une après l'autre** (séquentiel, *intra-cours*), en plus du déverrouillage à 7 jours au niveau du cours (Prompts → EFT). À refléter dans le modèle de progression (une leçon se débloque quand la précédente est terminée).
- **#2 Webinaires (Zoom)** — **décidé en séance** : **page événement** avec **intégration Zoom Webinars**, **embed du live Zoom directement sur la plateforme**. Masterclasses d'**experts externes invités ~1×/mois**. (Confirme la nature de #2 ; reste 🔴 BIG / absent côté code.)
- **#3 Affiliation** — direction confirmée : **plateforme de commission dédiée** (lien lancement / commission → SaaS d'affiliation, voir #29). #3c (widget rappel lien) reste acquis ; #3b (payout % maison) probablement abandonné au profit du SaaS externe.
- **#26 Optimisation mobile** — élargir : pas seulement le menu latéral cassé — l'app doit être **globalement plus responsive et optimisée mobile** (toutes les vues, pas juste la nav).
- **#27 Onboarding** — préciser : onboarding **basé sur des modales** (parcours guidé en modals à la 1ère connexion), pas une page séparée.

---

## ⭐ REMINDER — Astro-cartographie vs astro.com (keep checking)

> **Action standing:** before each astro-géo work session, re-open astro.com side-by-side and confirm parity. Surface this to Léonard. Kept here on purpose.

Her exact words (2026-06-09, ~15h):
- *"la partie astro-cartographie ne montre pas encore la même chose que astro.com n'est-ce pas?"* — [post](https://42lab.slack.com/archives/C0A773J15FF/p1781010382669069)
- *"j'ai clické sur recalculer mais il me dit toujours « aucune ligne dans un rayon de 500 km »"* — [post](https://42lab.slack.com/archives/C0A773J15FF/p1781010400529489)
- *"il faudrait idéalement que peut importe la ville que je choisis, il y a sur la droite une liste des lignes / latitude etc — et il faudrait une mini-interprétation aussi automatiquement générée par exemple: « ici ton énergie est sérieuse et disciplinée car ta ligne saturne est proche... Un endroit parfait pour ___ mais déconseillé pour ___ »"* — [post + image](https://42lab.slack.com/archives/C0A773J15FF/p1781010590197769)

Earlier framing of the same ask (2026-05-27): astro.com shows **same-latitude lines (parans)** even with no line within 500 km — [post + 2 images](https://42lab.slack.com/archives/C0A773J15FF/p1779908052415269) · richer right-panel text for ChatGPT copy-paste — [post + image](https://42lab.slack.com/archives/C0A773J15FF/p1779908593722039).

**Reference captures (astro.com, 10 juin):** `assets/astro-reference/` — `astro-com-simple-distance-to-line` (vue simple), `astro-com-show-details-parans` (vue détails), `…-astroclick-travel-map`, `…-rightpanel`.

> ⚠️ **Correction (2026-06-10, validée sur captures astro.com réelles):** astro.com **ne dessine pas de bandes horizontales**. La piste "rendre les parans en bande latitudinale" était **fausse — abandonnée**. Voir le vrai modèle ci-dessous.

**Three concrete dev tasks** (code-confirmed, recalibrés 2026-06-10):
1. **Fix le faux état vide + exposer les parans "même latitude".** (a) Vue simple : astro.com montre **toujours la ligne la plus proche + sa distance** (ex. "Moon/AS · 228 km") — notre "aucune ligne dans un rayon de 500 km" est le bug, il faut afficher la plus proche au lieu d'un message vide. (b) Vue détails : **lister les croisements (parans) à la même latitude que le clic**, même si le croisement réel est hors carte (ex. "3812 km à l'est"), avec paire + interp + coords + distance/direction. **On a déjà toutes les données** (`computeAcg → parans[]` incl. Nœuds via `persist.ts`, `getAcgParanInterpretation`, `greatCircleDistanceKm`) — il manque le **câblage** : lookup même-latitude (indépendant longitude), section panneau, helper bearing. 🟠 MEDIUM
2. **Right panel per clicked city**: list of lines/latitudes **+ auto-generated AI mini-interpretation**. Panel currently lists lines+distance only, no AI text (`acg-info-panel.tsx`; AI plumbing via `getLanguageModel()` + `lib/ai/context.ts` exists). NB : le texte d'astro.com est **statique** (Jim Lewis) — la version IA personnalisée va **au-delà** d'astro.com. 🟠 MEDIUM
3. **Rename "astrocartographie" → "astrologie géographique"** everywhere user-facing (~6–7 strings; keep `/charts/acg` route). Reason: trademark scare in FR astro community + she runs FR-targeted ads ([2026-06-03](https://42lab.slack.com/archives/C0A773J15FF/p1780503244079569)). Léonard said this + PDF export already in progress but *"une version du code ne s'est pas déployée"* ([10 juin thread](https://42lab.slack.com/archives/C0A773J15FF/p1781010815461399)). 🟢 SMALL — ✅ **DONE & VERIFIED (10 juin)**: full-codebase audit confirms every user-facing string now reads "astrologie géographique" (sidebar, charts nav, `/charts/acg` page, ACG client, FAQ labels, méthode page, agent-data scope, AI prompt header, refresh API error). Only code identifiers keep the legacy term (route, `hasAstrocartography`, FAQ category `id`, nav `value`, DB `acgChart`, agent key `acg`) — exactly as the brand rule requires.

---

## 📚 Académie / Cours en ligne — assets for implementation

Keep handy when building the LMS:
- **Mockup (download/inspect):** <https://alixai-mockup.netlify.app/academie.html>
- **Course HTML files (local copy):** [`assets/cours-en-ligne-alixai.zip`](assets/cours-en-ligne-alixai.zip) (from her Drive — [post](https://42lab.slack.com/archives/C0A773J15FF/p1781029491970839))
- Her design notes — [post 21:01](https://42lab.slack.com/archives/C0A773J15FF/p1781031717605089):
  - Ignore the mockup's **left menu** (not aligned to our design).
  - **2 courses live now:** *Séquences EFT*, *Ton Guide Complet de Prompts IA*. Two others shown **locked-but-visible** (FOMO; she'll add surprise courses ~1/month by email later — don't show those yet).
  - **Oracle agent box embedded in each chapter (1–8)** of the Prompts course, so users run prompts without leaving the module. *(She's unsure it's technically feasible — it is, but it's part of the LMS build.)*
  - Ignore the stray **"Astra"/"Oracle"/"Vera"** buttons above the box — only the Oracle box stays.
  - **Unlock logic:** *Guide Complet de Prompts IA* opens first → exactly **7 days later** *Séquences EFT* auto-unlocks.
  - She decided **not** to import from Thinkific; she'll add remaining course content herself over time.

---

## Pre-launch to-do (grouped, code-confirmed)

Sizes: 🟢 small · 🟠 medium · 🔴 big.

### From her recap — features to implement before launch

| # | Item | Size | Code status (staging) |
|---|------|------|------------------------|
| 1 | **LMS / Académie** — course catalog, locked-but-visible courses, lesson pages, 7-day unlock, embedded Oracle box | 🔴 BIG | **SKELETON** — `app/(dashboard)/lms/page.tsx` UI only, hardcoded cards + WIP banner; **zero** Prisma models (Course/Section/Lesson/Progress); no unlock logic, no Oracle box |
| 2 | **Webinaires (Zoom Webinars)** — monthly, list upcoming + register; must be Zoom **Webinars** (paid acct), not Zoom Pro | 🔴 BIG | **ABSENT** — no route/model/Zoom ref anywhere. Net-new (wasn't in today.md) |
| 3a | **Affiliation — VIP free/comped accounts** for ambassadrices | 🟠 MED | **ABSENT** — no VIP/comp flag |
| 3b | **Affiliation — 8% commission auto-paid quarterly** | 🔴 BIG | **ABSENT** — current model pays *free months* not %; no cron/batch payout. *Post-launch-tolerable (quarterly).* |
| 3c | **Affiliation — personalized link visible/shareable from her space + reminder widget (bottom of sidebar + bottom of dashboard)** | 🟢 SMALL | ✅ **DONE (10 juin, branch `launch-prep-alix`)** — new `AffiliateReminder` widget (`components/affiliation/affiliate-reminder.tsx`) pinned to the sidebar bottom + dashboard foot; one-click *Copier mon lien* + link to `/entourage`. Referral code now backfilled in the dashboard layout via shared `lib/affiliation/referral-code.ts` so the widget always resolves. She loves the Manus-style reminder (earned 40k credits) — [post + image](https://42lab.slack.com/archives/C0A773J15FF/p1781020925970639) |
| 4 | **Feedback intégré** — in-app (a) report a bug, (b) **vote** among proposed features for next sprint | 🟠 MED | Bug report **DONE** (`feedback-dialog.tsx` → admin tab); **feature-voting UI ABSENT** |
| 5a | **Stripe — 7-day trial → monthly auto-convert** | ✅ | **DONE** (config) |
| 5b | **Stripe — single Business plan 49€/mois** | — | Alix configures herself in admin ([Léonard 10 juin](https://42lab.slack.com/archives/C0A773J15FF/p1781071764738469)) — off our plate |
| 5c | **Stripe — "Fondatrices" = 6 mois Business offerts** (limited launch offer) | 🟠 MED | **ABSENT** — no coupon/promo system in checkout; needs Stripe coupon or 180-day comp |
| 5d | **Show only those 3 options** on public landing + in-app subscription space | 🟢 SMALL | **NO CODE NEEDED** — pricing is 100% DB-driven; the landing just links to `/pricing`, which already filters `isActive`. Hiding tiers = Alix toggles the non-launch plans `inactive` in the admin Plans panel. Data/admin task, not a deploy. |

### Astro & polish (her 9-June + acknowledged WIP)

| # | Item | Size | Code status |
|---|------|------|-------------|
| 6 | **Astro-géo** (3 tasks) | 🟠 MED ×2 + 🟢 SMALL | see ⭐ section above |
| 7 | **Dashboard — agent boxes all same size** | 🟢 SMALL | ✅ **DONE (10 juin)** — added `auto-rows-fr` to the `/agents` grid so every row (and thus every card) is equal height (`app/(dashboard)/agents/page.tsx`). The dashboard `GuidesCarousel` was already equal-height via flex-stretch. — [post + image](https://42lab.slack.com/archives/C0A773J15FF/p1781011634222999) |
| 8 | **Dashboard AI phrases** ("ta transformation profonde…") harden to concrete/actionable | 🟢 SMALL | prompts are **DB-editable**, no deploy — content edit for Alix, not a code task |
| 9 | **Transit duration "jusqu'à quand"** | 🟢 SMALL | ✅ **DONE (10 juin)** — short/medium transits already showed the end date; long (multi-mois/an) transits now append `· jusqu'au <date>` too, so every transit answers "jusqu'à quand" (`today-energy.tsx`) |
| 10 | **Synastrie** — add minor aspects/orbs/calculated points | 🟢 SMALL | ✅ **DONE (10 juin)** — added 3 minor aspects (quinconce 150°, demi-sextile 30°, quintile 72°) with tight orbs, **scoped to synastry only** (transits stay major-only to avoid flooding the daily feed). Labels/colors/interpretations already existed in `wheel/constants.ts`; grid + bi-wheel render them automatically. `lib/charts/types/transits.ts` + `lib/charts/synastry.ts`; 10/10 unit tests green. · ✅ **vérifié staging 11-06** ; 🆕 retouche : panneau d'aspects = hauteur de la roue (cap `maxHeight:540` → prop `fillHeight` ; `aspect-grid.tsx` + `comparison-dialog.tsx`), **pending deploy** |
| 11 | **Synastrie PDF download** | 🟠 SMALL–MED | **WIP/absent** |
| 24 | **Vérifier la nouvelle UI synastrie + intégrer dans les rapports PDF** — les 4 onglets remaniés (Gene Keys 3-vues, Human Design explorer, Astrologie géographique 3-vues, Numérologie rebuild) sont mergés sur staging (PR #7, `03027c4`). À faire : (a) walk-through manuel sur `/entourage` (4 onglets, pair complet + cas proche sans charte) ; (b) vérifier que `/charts` HD solo n'est pas cassé (attribut `data-gate` ajouté) ; (c) intégrer le contenu des 4 onglets dans les templates de rapport PDF (module D). | 🟠 MED | **staging** — à vérifier + intégrer PDF |

---

## Setup track for 16 juin (admin, not features)
- [ ] Connect final domain + deploy on it (`alixai.co` / `app.alixai.co` direction — landing on root, app on `app.`). **App goes on `app.alixai.co`** (decided 02-06 ; Alix has `alixai.co` landing on Netlify). Vercel: add `app.alixai.co` as domain → CNAME to provided `*.vercel-dns.com` value (Alix sets at her registrar) ; then set `BETTER_AUTH_URL` + `NEXT_PUBLIC_APP_URL` = `https://app.alixai.co` on the prod project.
- [ ] Google OAuth (« Sign in with Google ») — **code done (16-06, staging)** : `socialProviders.google` in `lib/auth.ts` (gated on `GOOGLE_CLIENT_ID`/`SECRET`), account-linking for trusted google, « Continuer avec Google » button on `/login` (gated on `NEXT_PUBLIC_GOOGLE_AUTH_ENABLED`). **Remaining (admin)**: create OAuth client in Google Cloud Console, set redirect URIs `<origin>/api/auth/callback/google` for prod/staging/dev, paste `GOOGLE_CLIENT_ID`/`GOOGLE_CLIENT_SECRET` + `NEXT_PUBLIC_GOOGLE_AUTH_ENABLED=true` into Vercel env. NB: « Google Admin Console » in the brief = this OAuth setup (Google Cloud Console), not Workspace.
- [ ] Stripe test pass (Alix self-configures the 3 plans in admin to surface gaps)
- [ ] **Pré-lancement clientes (qqs jours avant le 26 juin)** — migrer les comptes clientes existantes sur la **prod** + l'URL finale pour récolter des feedbacks avant le public, avec **redirection depuis l'ancien domaine**. (Alix 10-06 → Léonard OK — détail en bas de page)

## Image-bearing posts (open for the screenshot)
| Post | What she shows |
|------|----------------|
| [15:09](https://42lab.slack.com/archives/C0A773J15FF/p1781010590197769) | astro-géo right-panel + mini-interprétation ask |
| [15:27](https://42lab.slack.com/archives/C0A773J15FF/p1781011634222999) | agent boxes uneven sizes |
| [18:02](https://42lab.slack.com/archives/C0A773J15FF/p1781020925970639) | Manus-style affiliate reminder she wants copied |
| [05-27 20:54](https://42lab.slack.com/archives/C0A773J15FF/p1779908052415269) | our ACG vs astro.com (Bruxelles), 2 images |
| [05-27 21:03](https://42lab.slack.com/archives/C0A773J15FF/p1779908593722039) | sparse right-panel text |

---

## Headline read
Gros chantiers qui gardent le lancement : **LMS** (skeleton) + **Webinaires Zoom** (absent) + **nav mobile cassée** (#26 🔴, bloque tout l'usage mobile + le flow social #30). **Pages légales** (#28) = bloquant **dur** du lancement public (SaaS payant + ads FR), petit en effort mais non négociable. **Affiliation** bascule probablement vers un **SaaS externe** (#29) — décision build-vs-buy à trancher, ce qui retire le payout %/dashboard maison du chemin critique. Le reste = polish small/medium. 16 juin = jalon setup, pas feature-freeze.

> ⚠️ La session du 17-06 a ajouté **2 vrais bloqueurs lancement** non identifiés au recap : **nav mobile** (#26) et **pages légales** (#28). À prioriser avec LMS + Webinaires.

---

## Changelog

**2026-06-17 (#28 pages légales → code, [PR #9](https://github.com/42Lab-co/business_school_ai_platform/pull/9) → staging) :**
- ✅ Page `/mentions-legales` créée (`app/(auth)/mentions-legales/page.tsx`) — publique, même layout/typo que cgu/privacy, sections FR standard (éditeur, directeur publication, hébergeur Vercel, PI, RGPD, contact) avec **placeholders explicites** pour les identifiants légaux d'Alix (SIRET/raison sociale/etc. — non inventés).
- ✅ Lien « Mentions légales » ajouté dans le **footer public** (`public-footer.tsx`) ET le **footer in-app** (`footer.tsx`, qui liait déjà CGU+privacy) → les 3 pages atteignables des deux côtés.
- 🔎 Contrôle contenu cgu/privacy : réel (pas lorem) mais gaps légaux listés dans la PR pour Alix/juriste (identité éditeur, droit applicable, transferts hors-UE, DPO…).
- Branche `legal/mentions-legales`, base `staging`. `tsc` sans nouvelle erreur, Biome clean. **Reste : Alix remplit les placeholders + validation juriste.**

**2026-06-17 (session Léonard ↔ Alix → doc, 6 items net-new #25–#30 + 3 recadrages) :**
- 🆕 **#25** Bibliothèque de prompts — page dédiée, prompts par agent, intégrer l'e-book de prompts d'Alix. 🟠 MED.
- 🆕 **#26** Optimisation mobile 🔴 — navigation mobile non fonctionnelle (menu latéral inaccessible). Bloquant mobile + pré-requis #30. 🔴 BIG.
- 🆕 **#27** Onboarding de présentation de la plateforme (parcours guidé 1ère connexion). 🟠 MED.
- 🆕 **#28** Pages légales (CGU, confidentialité, mentions légales) absentes — bloquant lancement public. 🟢🟠 SMALL–MED.
- 🆕 **#29** Programme d'ambassadrices via **affiliation externe (SaaS dédiée)** : auto-payout, dashboard affiliée, lien tracké Stripe, paliers de commission. **Décision build vs buy** ; supersède probablement #3b. 🔴 BIG.
- 🆕 **#30** 📈 Flow mobile « contexte social » (dîner/événement) — ajout rapide contact + QR code + invite email temps réel. Proposé par Léonard, accueil très positif. Dépend de #26. 🟠 MED.
- 🆕 **#31** Admin voit la **dernière connexion** de chaque utilisatrice (activation/churn). 🟢🟠.
- 🆕 **#32** **Accès gratuit / comptes d'essai** via URL dédiée — flow CB ou non **à décider**, proposer options à Alix. 🟠 MED.
- ♻️ Recadrages : **#1 LMS** = leçons débloquées **l'une après l'autre** (séquentiel intra-cours, en + du 7-jours) ; **#2 Webinaires** = page événement + embed live Zoom Webinars (experts externes ~1×/mois), décidé en séance ; **#3 Affiliation** = **plateforme de commission dédiée** (cf. #29) ; **#26** = responsive global, pas que la nav ; **#27** = onboarding **modale**.
- Source = session/notes Léonard (pas Slack) ; code status non vérifié contre `staging` pour les net-new.

**2026-06-15 (batch #14/#15/#19 → staging, 2 commits `8a05c88` + `c57ee4a`) :**
- ✅ **#19** « Juin » caché derrière les points — c'était la timeline `/transits` (`app/(dashboard)/transits/page.tsx`), pas `upcoming-transit.tsx` : le label date affleurait la pastille du transit majeur. Fix `paddingRight: 24`.
- ✅ **#14** Roue astro lisibilité — glyphes 17/14 → **22/19**, weight 700→**800** + stroke faux-bold (`paintOrder`) ; cuspides non-angulaires bien plus légères (width 0.7→0.3, opacity 0.6→0.16) vs axes ASC/MC/DSC/IC renforcés (opacity 0.9). Hover repassé itérativement avec Léonard : glyphe actif +4 / stroke épais / halo doré annelé, autres à 0.12, **actif reste brun foncé (bronze)** pour contraster sur le halo (pas noir, pas doré). `orbital-lanes-chart.tsx` + `astrology-section.tsx`.
- ✅ **#15** Panneau « Positions planétaires » — texte agrandi (`text-sm`/`text-[11px]`), `truncate` retiré (fin du crop maison), **section « Axes » ASC + MC** (signe + degré) ajoutée. `orbital-lanes-chart.tsx`.
- `tsc --noEmit` propre sur les fichiers touchés. Poussé sur **staging** (pas main — confirmé avec Léonard ; PR #8 = même branche). À vérifier sur `alix.42lab.co`.

**2026-06-12 (#21 home + 2 retours clientes → doc) :**
- ✅ **#21** Boxes agents inégales sur la **home** (`alix.42lab.co/`) — le fix #7 (`auto-rows-fr`) ne touchait que `/agents` ; la home utilise `GuidesCarousel` (carousel flex). Cause : wrapper `<Link>` en `display:block` → `flex:0 0 280px` inerte + pas d'étirement. Fix : `<Link>` → `flex` + `items-stretch` sur le rail. `components/dashboard/guides-carousel.tsx`. `tsc` exit 0 ; lint warning **pré-existant**. Poussé sur **staging** (`94cc732`) — à vérifier sur `alix.42lab.co/` une fois le build vert.
- 🆕 **#22** Whole Signs (système de maisons astro) — demandé par Alix + élève astrologue (Placidus = « embêtée par les réponses ») ; Léonard engagé. 🟠 MED.
- 🆕 **#23** Transits mis en avant (transits portes HD + impact énergie ; conseils numéro du mois ; surfacer au quotidien) — issu de 2 retours clientes. 🟠 MED.
- Watermark → 2026-06-12 (top-level 10:53 TS `1781254381.950919` ; threads jusqu'à 12:27 TS `1781260028.434779`).

**2026-06-11 (batch #12/#13/#16/#17 → staging, 4 commits `00254ca..cfa4937`) :**
- ✅ **#12** Questions de départ par agent — les 7 agents reçoivent les nouvelles questions d'Alix (verbatim ; « Ma branding » → « Mon branding » ; « Les signes que je ne suis pas alignée ? » gardé tel quel). `lib/constants/agents.ts` (`891faf2`).
- ✅ **#13** Micro vocal déplacé **à droite** de la barre, juste avant Envoyer, partout dans l'appli — `components/multimodal-input.tsx` (`cfa4937`).
- ✅ **#16** « Année personnelle » / « Mois personnel » en **Poppins bold** (même police que « chemin de vie ») — `components/charts/numerology-summary.tsx` (`36013ae`).
- ✅ **#17** Menu agents : spécialité entre parenthèses (« Astra (Astrologie) »…) — `components/v2/sidebar.tsx` (`460a6bb`).
- `tsc --noEmit` clean ; findings lint = **pré-existants** (vérifiés sur HEAD, aucun nouveau introduit). Poussés sur **staging** (pas main). À vérifier sur `alix.42lab.co` une fois le build Vercel vert.

**2026-06-11 (astro-géo — refonte panneau « Croisements » + Luna, branch→staging `00254ca`) :**
- « Croisements à ta latitude » **dédupliqués par paire de planètes** (les variantes ASC/DSC partageaient le même texte d'interprétation) + cartes **compactes repliables** (une ligne, tap pour le détail). Fini le mur de cartes.
- Bouton IA déplacé **au-dessus** du panneau (avant : en bas) + reformulé **« Luna, que vaut ce lieu pour moi ? »** (au lieu de « Générer l'interprétation »).
- Interprétation inline désormais **signée Luna** (persona) et nourrie des **lieux enregistrés** de la personne (`acg-interpretation.ts`). En chat, Luna avait déjà accès aux lieux enregistrés (scope `acg`).
- `acg-info-panel.tsx` + `acg-interpretation.ts` ; tsc + biome clean. **Poussé sur staging** (pas main). Build Vercel vert attendu (base = fix chromium `8c5ea0f`). À vérifier sur `alix.42lab.co`.

**2026-06-11 (vérifs staging par Léonard) :**
- ✅ Vérifiés OK : **#7** (boxes agents même taille), **#9** (transit « jusqu'à quand »), **#3c** (widget affiliation), **rename** astrologie géographique.
- **#10** synastrie : aspects mineurs OK (demi-sextile / quintile / quinconce visibles avec orbe + poids). Retouche demandée par Léonard : le **panneau d'aspects doit remplir la hauteur de la roue** (avant : cap `maxHeight:540`, plus court que la roue) → **fait en code** (`aspect-grid.tsx` prop `fillHeight` + flex dans `comparison-dialog.tsx` ; tsc clean), **pending deploy**.


**2026-06-11 (suite, 11:18–13:14) — 2nd batch from Alix + Léonard exchanges:**
- ✅ #12 Luna + Ava starter questions now provided → **all 7 agents covered** (was 5/7).
- 🆕 #14 astro wheel: glyphs bigger/bolder, house lines lighter.
- 🆕 #15 « Positions planétaires » panel: bigger/legible + add ASC & MC + fix cropped house (Léonard: will fix the crop).
- 🆕 #16 numerology typo: « année personnelle » + « mois personnel » → Poppins bold (Léonard 👌).
- 🆕 #17 agent menu: append specialty in parens, e.g. « Astra (Astrologie) » (`domain` field already exists; Léonard 👌).
- 🆕 #18 astro-géo: dedupe repeated transit boxes → one per transit with full window dates.
- 🆕 #19 « juin » still hidden behind the dots (recurring since 02-06; candidate component, confirm on screenshot).
- ℹ️ Non-action: dotted-lines-in-wheel question — Léonard explained (planets vs calculated-points separation; hover highlight exists).
- Watermark moved to 2026-06-11 13:14 (TS `1781171696.159029`). Verbatim consolidé dans § Détail / verbatim (bas de page) ; annexe séparée supprimée.

**2026-06-11 — new asks from Alix (post-recap, Slack #business-school-ai):**
- 🆕 #12 editable per-agent starter questions (5/7 agents specified — Oracle/Astra/Vera/Clara/Noa; Luna+Ava pending). Hardcoded in `lib/constants/agents.ts` → code change. Léonard: « Oui bien sûr ».
- 🆕 #13 move voice mic to the right of the input, app-wide. Currently left. Léonard: « Oui bien sûr ».
- 📋 setup track: pre-launch client migration to prod + final URL a few days before 26 juin, with redirect (Alix 10-06).
- Verbatim content → § Détail / verbatim (bas de page). Last Slack msg read: 2026-06-11 11:07 (TS `1781168831.538219`).

**2026-06-10 — easy-fix batch (branch `launch-prep-alix`, not yet pushed to staging):**
- ✅ #7 agent boxes equal height (`auto-rows-fr` on `/agents` grid)
- ✅ #9 transit "jusqu'à quand" (end date now shown for long transits too)
- ✅ #10 synastrie minor aspects (quinconce / demi-sextile / quintile, synastry-only)
- ✅ #3c affiliation reminder widget (sidebar bottom + dashboard foot; shared referral-code backfill helper)
- ✅ astro-géo rename verified complete (audit, no code change needed)
- ⏭️ #5d "show only 3 plans" = data config in admin (no code); #8 dashboard phrases = DB prompt edit (no code)

Typecheck clean (`tsc --noEmit` exit 0); synastry unit tests 10/10 green; touched files lint-clean (2 pre-existing lint warnings in `sidebar.tsx` left untouched). **Next:** review + PR to `staging`.

---

## 📎 Détail / verbatim — demandes 10–12 juin (élaguer après livraison)

> Contenu brut conservé pour l'implémentation des items #12–#23. **Une fois livrés, cette section peut être supprimée** — le suivi (tâche + statut) reste dans les tableaux ci-dessus. Watermark Slack dans le frontmatter (`last_checked_ts`).

### Retours clientes (questionnaire) — 11–12 juin

Deux retours d'élèves transmis par Alix (captures illisibles via MCP — canal Slack Connect ; texte fourni par Léonard). Convergent sur **Whole Signs** (#22) + **transits** (#23) ; **Stratégie** = point fort confirmé (aucune action).

**Élève astrologue (20 ans, enseignante Gene Keys)** — [11-06 17:18](https://42lab.slack.com/archives/C0A773J15FF/p1781191113316829) (capture `F0B9RFT6STV`) :
- *« J'attends avec impatience la nouvelle version ;) »*
- *« Je ne travaille pas du tout avec **placidus** alors j'étais embêtée par les réponses apportées. »*
- *« j'ai **adorée la partie Stratégie** parce que ça permet vraiment de créer une stratégie 100% en lien avec nos chartes. »*
- Effet WOW : *« Le système **Whole Signs** pour l'astro. La prise en considération des **transits**. »*

**Autre retour cliente** — [12-06 10:50](https://42lab.slack.com/archives/C0A773J15FF/p1781254231593789) (capture `F0B9Y3ZFEH1`) :
- Effet WOW / usage quotidien : *« je voudrais mes **transits**, les **conseils numérologiques du mois**, les **transits dans les portes HD** et leur impact sur mon énergie »*

### #21 — Boxes agents inégales sur la home (2026-06-12)

Alix ([10:21](https://42lab.slack.com/archives/C0A773J15FF/p1781252510835439), capture `F0BA48RTMNE`) : *« peut-être que ça dépend de chaque écran ? j'ai rafraîchi et sur mon macbook les agents s'affichent encore à des tailles différentes »* — sur `alix.42lab.co/` (la **home**, pas `/agents`). Léonard ([10:45](https://42lab.slack.com/archives/C0A773J15FF/p1781253953070869)) : *« on regardait sur un url différent, je vais le régler là-bas aussi »*.

Code : le fix #7 (`auto-rows-fr`) ne couvrait que le grid `/agents`. La home rend les agents via `GuidesCarousel` (carousel flex horizontal) — `components/dashboard/guides-carousel.tsx`. Cause : wrapper `<Link>` en `display:block` → `flex:0 0 280px` (largeur) inerte + pas d'étirement vertical. Fix : `<Link>` → `flex` + `items-stretch` sur le rail (les cartes s'étirent sur la plus haute, largeur 280 garantie).

### #22 — Whole Signs (système de maisons astro) (2026-06-12)

Alix ([10:52](https://42lab.slack.com/archives/C0A773J15FF/p1781254346347289)) : *« j'imagine que c'est trop tard pour rendre le système whole signs disponible pour l'astrologie ? »*. Léonard ([11:17](https://42lab.slack.com/archives/C0A773J15FF/p1781255871482929)) : *« je vais le mettre en place, j'ai déjà des fondations, et c'est un système important ce serait dommage que tu ne l'aies pas »*. Alix : *« Ok génial 🙌🔥 »*. Renforcé par l'élève astrologue (Placidus = « embêtée par les réponses »).

Portée : toggle Placidus ↔ Whole Signs — en Whole Signs, la maison N = le signe entier (cuspide = 0° du signe). Impacte le calcul des cuspides, le remap des maisons des planètes, l'affichage roue (`orbital-lanes-chart.tsx`), le panneau positions, et la cohérence des prompts IA. Fondations déjà posées (d'après Léonard).

### #23 — Transits mis en avant (effet WOW / usage quotidien) (2026-06-12)

Issu des 2 retours clientes (ci-dessus). Les transits sont cités comme LA raison de garder l'abonnement. Décomposition :
- **(a) Transits dans les portes HD + impact énergie** — net-new : mapper les transits planétaires sur les portes/lignes Human Design + interpréter. 🟠 MED–BIG.
- **(b) Conseils numérologiques du mois** — étendre le « mois personnel » avec un conseil mensuel. 🟢🟠 SMALL–MED.
- **(c) Surfacer davantage les transits au quotidien** — la base existe (`today-energy.tsx`, page `/transits`). Direction produit.

### #12 — Questions de départ pré-écrites par agent (2026-06-11)

Alix : *« pour oracle, peut-on ajuster les questions initiales pré-écrites ? »* — Léonard : *« Oui bien sûr »* ([11:03](https://42lab.slack.com/archives/C0A773J15FF/p1781168583079829)). Elle a fourni les questions pour **les 7 agents**.

Code : hardcodé par agent dans `lib/constants/agents.ts` (champ `suggestions`, ~l.36–161) ; fallback `DEFAULT_SUGGESTIONS` dans `components/suggested-actions.tsx`. Pas d'édition admin → changement de code.

> NB grammaire/accents à corriger (règle FR). Ex. Astra « Ma branding » → « Mon branding ».

**Oracle** — [10:50](https://42lab.slack.com/archives/C0A773J15FF/p1781167815224539)
- _Actuel :_ « Par où je commence aujourd'hui ? » · « Fais-moi une synthèse de mes chartes » · « Qu'est-ce qui se joue pour moi cette semaine ? » · « Aide-moi à clarifier mes priorités »
- _Demandé :_ « Quels sont mes dons uniques ? » · « Quelle est l'énergie de ce mois pour moi ? » · « Ma façon unique de manifester ? » · « Fais-moi une synthèse de mes chartes »

**Astra** — [10:56](https://42lab.slack.com/archives/C0A773J15FF/p1781168197704749)
- _Actuel :_ « Que dit mon thème natal sur mon énergie business ? » · « Lis-moi mes transits importants du moment » · « Quels sont mes points forts d'après mon ciel ? » · « Explique-moi ma maison 10 »
- _Demandé :_ « Ma façon alignée de générer des revenus ? » · « Mon branding le plus magnétique ? » *(écrit « Ma branding »)* · « Mes transits importants du moment ? » · « Ma mission de vie ? »

**Vera** — [10:58](https://42lab.slack.com/archives/C0A773J15FF/p1781168334123419)
- _Actuel :_ « Rappelle-moi ma stratégie et mon autorité » · « Comment prendre une décision alignée cette semaine ? » · « Quels sont mes centres définis et ouverts ? » · « Explique-moi mon profil et ma signature »
- _Demandé :_ « Les signes que je ne suis pas alignée ? » · « Rappelle-moi ma stratégie et mon autorité » · « Mes superpouvoirs uniques ? » · « Comment attirer mes clients alignés ? »

**Clara** — [11:05](https://42lab.slack.com/archives/C0A773J15FF/p1781168713750179)
- _Actuel :_ « Quelle est ma Clé de Travail de Vie ? » · « Aide-moi à contempler ma Shadow du moment » · « Que m'enseigne ma Séquence de Vénus ? » · « Explique-moi le Golden Path »
- _Demandé :_ « Tes 5 conseils pour mon abondance ? » · « Mes 5 parts d'ombre ou faiblesses ? » · « Ma mission de vie ? » · « Mes superpouvoirs ? »

**Noa** — [11:07](https://42lab.slack.com/archives/C0A773J15FF/p1781168831538219)
- _Actuel :_ « Quel est mon chemin de vie ? » · « En quelle année personnelle suis-je ? » · « Que dit mon nom de naissance ? » · « Décris-moi mon cycle actuel »
- _Demandé :_ « Explique-moi mon chemin de vie » · « En quelle année personnelle suis-je ? » · « En quel mois en numérologie suis-je ? » · « Analyse ma numérologie entière »

**Luna** — [11:18](https://42lab.slack.com/archives/C0A773J15FF/p1781169514770399)
- _Actuel :_ « Où sont mes lignes Jupiter et Vénus ? » · « Quelle ville me serait favorable pour mon business ? » · « Y a-t-il une ligne Saturne près de chez moi ? » · « Conseille-moi un lieu pour une retraite »
- _Demandé :_ « Mes 5 endroits dans le monde pour l'abondance ? » · « Où est-ce que ma vie est le plus fluide ? » · « Des endroits dans le monde pour me détendre et ressourcer ? » · « Meilleures villes pour mon business ? »

**Ava** — [11:20](https://42lab.slack.com/archives/C0A773J15FF/p1781169643320949)
- _Actuel :_ « Aide-moi à clarifier mon offre » · « Construis-moi un plan d'action pour la semaine » · « Comment attirer plus de clients alignés ? » · « Revoyons mes prix ensemble »
- _Demandé :_ « Comment attirer plus de clients alignés ? » · « Que doit communiquer mon branding ? » · « Les clés pour augmenter mes revenus ? » · « Que dire sur les réseaux ? »

*(Léonard 11:18 : « Pour Luna et Ava tu veux aussi changer ? » → elle a répondu par les deux listes.)*

### #13 — Micro vocal à droite (2026-06-11)

*« le micro pour parler à l'IA est toujours à droite [ChatGPT/Manus] — pourrait-on le mettre à droite pour plus de fluidité ? (partout dans l'appli) »* ([11:01](https://42lab.slack.com/archives/C0A773J15FF/p1781168474736089)) — Léonard : *« Oui bien sûr »*.

Code : `components/voice-input-button.tsx`, placé **à gauche** (cluster `PromptInputTools` après la pièce jointe) dans `components/multimodal-input.tsx` ~l.389–401 ; ordre via `components/elements/prompt-input.tsx`. → déplacer à **droite**, près d'Envoyer.

### #14 — Roue astro : placements plus lisibles (2026-06-11)

*« rendre les icônes des placements plus prominents […] les lignes qui délimitent les maisons […] un peu plus light, un peu moins marquée […] les placements type nœud nord, pluton […] un tout petit peu plus grands, et plus marqués en "bold" »* ([11:29](https://42lab.slack.com/archives/C0A773J15FF/p1781170193718589)). Réf. image astro-carto *« on voit immédiatement bcp plus facilement quels placements se trouvent où »* ([11:30](https://42lab.slack.com/archives/C0A773J15FF/p1781170242814409)).

Code : `components/charts/orbital-lanes-chart.tsx` — glyphes l.~1445–1461 (`baseSize`, font-weight 600) ; cuspides de maisons l.~1063–1089.

> Q. liée (non-action) : *« c'est quoi les "dotted lines" au milieu d'une maison ? »* ([11:25](https://42lab.slack.com/archives/C0A773J15FF/p1781169939262209)) → Léonard a expliqué (séparation planètes / points calculés ; le hover surligne déjà). Pas de tâche.

### #15 — Panneau « Positions planétaires » (2026-06-11) — [thread 11:36](https://42lab.slack.com/archives/C0A773J15FF/p1781170591296069)

- *« la partie "positions planétaires" peut être un peu plus grande »* → précise (11:46) : *« pour que toute cette liste "planètes" et "points calculés" soit bcp plus lisible et qu'on puisse bien voir les degrés »*. Léonard : *« Ok ça marche »*.
- *« le signe et position de l'ascendant aussi sur la liste — c'est un point important »* + *« le MC aussi sur cette liste »*.
- Bug : *« pas de maison […] pour saturne, uranus, neptune […] au lieu d'indiquer dans quelle maison se trouve neptune, il y a trois petits points »*. Léonard : *« c'est "cropped" pour ne pas déborder […], je vais le corriger aussi »*.

Code : `components/charts/orbital-lanes-chart.tsx` — titre l.2637, tailles l.~2715–2724 (`text-[10px]`), **`truncate` l.2718 = la cause du crop maison**. ASC/MC actuellement seulement dans `astrology-summary.tsx` l.149–156, pas dans la liste.

### #16 — Typo numérologie (2026-06-11)

*« mettre la même police "poppins bold" qui est sur "chemin de vie" ou "désir de l'âme" pour "année personnelle" et "mois personnel" aussi »* ([11:45](https://42lab.slack.com/archives/C0A773J15FF/p1781171128855029) 👌).

Code : libellés « chemin de vie » / « désir d'âme » dans `numerology-wheel.tsx` l.74–79 + légende l.945–992 ; « année personnelle » / « mois personnel » dans `numerology-summary.tsx`. Aligner les classes.

### #17 — Menu agents : spécialité entre parenthèses (2026-06-11)

*« mettre entre parenthèses à côté du nom de chaque agent sa spécialité […] je ne sais pas encore qui est qui »* — ex. « Astra (Astrologie) », « Noa (Numérologie) » ([11:49](https://42lab.slack.com/archives/C0A773J15FF/p1781171382626619) 👌).

Code : champ `domain` déjà présent par agent dans `lib/constants/agents.ts` (ex. `domain: "Astrologie"`) ; nom rendu dans `components/v2/sidebar.tsx` l.638 (`{agent.name}`) — y appondre `(domain)`.

### #18 — Astro-géo : un box par transit (2026-06-11)

*« dans astrologie géographique — […] 9 fois de suite la même box qui me rappelle que pluton est opposé à mon jupiter — est-ce que c'est un box par semaine ? est-ce qu'on ne pourrait pas avoir un box par transit tout simplement ? avec les dates complètes de la "fenêtre" du transit ? »* ([11:54](https://42lab.slack.com/archives/C0A773J15FF/p1781171654007829)).

Code : `app/(dashboard)/charts/acg/acg-info-panel.tsx` — `TransitView` mappe `activatedLines` (l.~528–577), une entrée par semaine/snapshot → non dédupliqué. Carte = `acg/active-transit-card.tsx` (affiche déjà début/pic/fin). Dédupliquer par transit (paire + aspect), garder la fenêtre complète.

### #19 — « Juin » caché derrière les points (2026-06-11)

*« je vois encore le mois de juin caché derrière les points »* ([11:54](https://42lab.slack.com/archives/C0A773J15FF/p1781171696159029)). Déjà signalé le 02-06 (*« les points se situent au dessus du mot juin »*).

Code : candidat `components/dashboard/upcoming-transit.tsx` (overlap mois / points, z-index/chevauchement) — **à confirmer sur la capture**.

### Pré-lancement clientes — migration prod (2026-06-10)

Alix ([12:01](https://42lab.slack.com/archives/C0A773J15FF/p1781085676226689)) : *« mettre à jour l'interface de mes clientes qques jours avant le 26 juin pour voir si elles ont des feedbacks ? »* + *« avant que ce soit public »*. Léonard ([14:18](https://42lab.slack.com/archives/C0A773J15FF/p1781093882101609)) : *« On peut toutes les passer sur la production et l'url final que tu choisis quelques jours avant — avec une redirection depuis l'ancien (actuel) nom de domaine »*.

→ Migrer les comptes clientes existantes sur la prod + URL finale quelques jours avant le 26 juin, avec redirection depuis l'ancien domaine. Logistique du setup track, pas une feature.

### #20 — Astrologie géographique : latitude Chiron manquante (2026-06-12) ⭐ PREMIER À DÉMARRER

Alix a remarqué que le croisement Chiron/Neptune visible sur astro.com n'apparaît pas dans notre appli ([Slack 14:00](https://42lab.slack.com/archives/C0A773J15FF/p1781265375779889)).

**Diagnostic (vérifié) :** il ne manque qu'**une seule donnée** : la latitude écliptique de Chiron, que Bodygraph ne renvoie pas. Sans elle, la déclinaison de Chiron est fausse, le croisement se déplace de ~16° et sort de la zone d'Alix → filtré. Astro.com (Swiss Ephemeris) utilise la vraie valeur (~+2,5°) et le croisement atterrit bien à ~51°N.

**Déjà livré sur `kathmandu-v1` (à merger) :**
- Toutes les planètes principales utilisent désormais la vraie latitude (corrige le Mars × Lune parasite).
- Luna prend en compte les croisements à la latitude dans ses interprétations de lieu.
- `ACG_ENGINE_VERSION` : 1.2.0 → 1.3.0.

**Reste à faire — Solution B (table Chiron précalculée, sans dépendance) :**

Coller ce prompt dans une nouvelle conversation Conductor :

```
Implement Chiron's true ecliptic latitude in the astro-géo (ACG) engine via a
precomputed, dependency-free latitude table (license-clean) so Chiron's lines and
same-latitude crossings (parans) match astro.com.

CONTEXT
- AliXAi astro-géo feature: code under lib/charts/acg/, route /charts/acg.
  User-facing name is "astrologie géographique"; code identifiers keep the legacy
  "acg"/"astrocartography" terms — do NOT rename them (see CLAUDE.md).
- The ACG engine converts each body's ecliptic (longitude, latitude) -> equatorial
  (ra, dec) via lib/charts/acg/coords.ts. Chiron's ecliptic latitude is currently
  FORCED TO 0 in lib/charts/acg/index.ts (the ZERO_LAT_BODIES set + the eclLat
  branch in computeAcg) because astronomy-engine doesn't ship Chiron. That wrong
  latitude corrupts Chiron's declination, which shifts its ASC/DSC lines and —
  critically — its parans: the crossing latitude moves ~5° per 1° of body latitude.
  With lat=0, the Chiron/Neptune crossing lands ~16° off and is filtered out by the
  1° paran orb (PARAN_LAT_ORB_DEG in lib/charts/acg/nearby.ts), so it never appears
  — while astro.com (true Chiron lat ~+2.5°) shows it. Verified numerically; see
  memory note "project_acg_paran_ecllat_bug".
- ALREADY DONE on branch kathmandu-v1 (build on it): the 8 main planets now use
  true ecliptic latitude (eclLatViaAstronomyEngine), and the Luna place-prompt was
  fixed to use crossings. ACG_ENGINE_VERSION was bumped to "1.3.0". Only Chiron is
  still pinned at 0. If those changes aren't committed yet, commit them first.
- Bodygraph (our data API) returns Chiron's ecliptic LONGITUDE (abs_pos) but NO
  latitude (confirmed in their docs). So keep Bodygraph's longitude; we only need to
  supply Chiron's latitude.

TASK (Solution B)
1. Offline/dev-only generation script (e.g. scripts/gen-chiron-latitude.ts): fetch
   Chiron's geocentric ecliptic latitude across ~1900-01-01..2030-01-01, monthly
   step, from JPL Horizons (public domain — license-clean):
   body COMMAND='2060;' (Chiron), CENTER='500@399' (geocentric Earth),
   QUANTITIES='31' (observer ecliptic lon & lat), of-date ecliptic. (Alternative
   source: Swiss Ephemeris via sweph-wasm in the script — but Horizons keeps it
   license-clean.) Do NOT ship the raw response, only the derived table.
2. Ship a compact dependency-free TS module lib/charts/acg/chiron-latitude.ts: a
   sampled table + interpolation (cubic / Catmull-Rom) or a piecewise polynomial
   fit, a few KB. Export chironEclLat(utc: Date): number.
3. Wire into computeAcg (lib/charts/acg/index.ts): remove "Chiron" from
   ZERO_LAT_BODIES (or special-case it ahead of the zero-lat branch) so Chiron's
   eclLat = chironEclLat(birthDateUtc). Keep abs_pos for its longitude. Clamp/handle
   out-of-range dates (document the choice). Update the ZERO_LAT_BODIES comment.
4. ACCURACY BUDGET: crossing latitude moves ~5°/1° of Chiron latitude and the orb is
   1.0°, so chironEclLat must be accurate to ~±0.1-0.2°. Chiron's latitude varies
   slowly, so monthly samples + cubic interpolation easily clear that — verify and
   document the achieved max interpolation error.
5. VALIDATE:
   - Unit test chironEclLat vs the Horizons reference for ~10 dates spanning the
     range (assert error < ~0.1°).
   - Integration: for Alix (1990-08-18 ~04:00 UTC, Chiron lon ~112.7° = 22.7°
     Cancer) confirm Chiron lat ≈ +2.5° and that the Chiron/Neptune paran now lands
     near 50-51°N (within the 1° orb of Brussels 50.86°N), matching astro.com. Use
     the repo's computeParans + eclipticToEquatorial.
   - Existing lib/charts/acg/*.test.ts still pass.
6. Bump ACG_ENGINE_VERSION "1.3.0" -> "1.4.0". The persisted charts go stale, so
   note that scripts/backfill-acg.ts (version-gated, no schema migration) must run
   on staging then prod to recompute AcgChart rows. Do NOT run the prod backfill
   without explicit approval.

CONSTRAINTS
- Never push to main — staging only; PRs target staging (gh pr create --base staging).
- Keep the generation script out of the runtime bundle (under scripts/).
- Follow lib/CLAUDE.md constants/style conventions. No emoji in any shipped copy.
```

**Après merge :** lancer `scripts/backfill-acg.ts` sur staging (puis prod sur OK explicite) — recalcule tous les `AcgChart` dont `engineVersion != 1.4.0`, sans migration de schéma.

---

*Compiled by Claude 2026-06-10 from #business-school-ai. Supersedes the launch portions of [[alix-feedback-2026-05-27]] for sequencing. Prune items as they ship.*
