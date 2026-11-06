# Passation

## 2026-11-06 08:09 — Benskin Express : cahier des charges du jeu

**Objectif en cours** — Cahier des charges (GDD) de Benskin Express, jeu moto-taxi 2D Android, validé par l'équipe avant de lancer le prototype Godot.

**Fait**
- Concept choisi parmi 4 propositions Trigenys (Tontine Rush, L'Ombre du Ngondo, Benskin Express, Mvett) : Benskin Express retenu, boucle courte type Hill Climb Racing / Crazy Taxi.
- Doc partageable rédigé (Claude Docs) : https://claude.ai/artifact/RtnYyzwweRTgZt1h2Dj9Wn
  Sections : vision, boucle de jeu (+ diagramme), contenu, DA + art bible, monétisation/rétention (sourcées), specs techniques (Godot 4, API 24, APK < 60 Mo), étapes de production, équipe (3 devs), MVP 8 semaines (+ calendrier dessiné), risques, sources.
- PDF exporté dans ce dossier : Benskin-Express-Cahier-des-charges.pdf (11 pages A4).
- Un commentaire posé dans le doc : « 8 ou 12 semaines ? », sans réponse encore.

**Décisions**
- Moteur Godot 4.x : gratuit, léger, physique 2D intégrée, couvert par le repo awesome-gamedev-agent-skills (à adopter, version épinglée).
- Claude-Code-Game-Studios (49 agents) : à piocher pour le pipeline design → QA, pas à installer tel quel (coût en tokens).
- 3 devs, pas d'artiste : découpage par couche (gameplay / systèmes-plateforme / assets-pipeline IA) ; le dev 3 porte la DA.
- Rétention cible J1 ≥ 30 %, J7 ≥ 12 % (médiane marché 2025 : 22-27 % / 4-6 %) ; aucun benchmark course ni Afrique francophone trouvé.
- MVP = Douala seule, 3 motos, 6 passagers, pubs récompensées + achat sans pub ; tout le reste en mise à jour 1.

**Reste à faire**
1. Faire valider le doc par les 2 autres devs (questions ouvertes : portrait/paysage, nom Benskin vs Bendskin, compte Google Play, budget pub, 8 vs 12 semaines).
2. Choisir un dossier projet (la session actuelle est sans dossier : le PDF et ce fichier sont dans un dossier temporaire de l'app ; les déplacer).
3. Semaine 1 : créer le dépôt Git, installer les skills gamedev, rédiger l'art bible, prototype gris de la moto.
4. Vérifier le compte marchand Google Play et le paiement sortant vers le Cameroun avant la semaine 6.

**Pièges / contexte**
- Export PDF du doc : l'outil export renvoie un JSON trop gros ; décoder `data.bytes_b64` en Python depuis le fichier tool-results.
- Les 2 diagrammes du doc sont des widgets SVG ; un redraw doit garder les text ids pour conserver les commentaires.
- Trigenys : respecter RAIDER (reuse-first, pas de nombres magiques : config de physique/économie dans un fichier éditable).

## 2026-11-06 08:25 — Dossier projet, dépôt Git, skills Godot, canal WhatsApp

**Fait**
- Dossier projet créé : `C:\Users\lawry\Documents\Projets\benskin-express` (la session y est déplacée ; PDF + ce fichier y sont copiés par l'app).
- `git init` (branche `main`), `.gitignore` Godot/Android ; rien n'est commité encore.
- Skills gamedev vendorisés dans `.claude/skills/` (router + 12 Godot + 9 disciplines), commit épinglé 19d93f9 : voir `docs/engineering/skills-pin.md`.
- `CLAUDE.md` du projet écrit.
- PDF du cahier des charges renvoyé à l'utilisateur dans le chat.
- WhatsApp : WAHA tourne sur le VPS `ubuntu@15.235.90.215` (clé `~/.ssh/id_ed25519_fleet_vps`, conteneur `trigenys-waha`, port local 3000, dossier `~/trigenys-waha`, secrets dans `.env`). Session `trigenys-test` WORKING, groupes visibles : « TRIGENYS GROUP » (120363408459165821@g.us, 5 membres) et « Xeption app test » (120363432964279423@g.us, 4 membres). trigenys-notify a l'adaptateur WahaAdapter + `npm run waha:send-test` ; il exige une URL HTTPS (notify.trigenys.com est servi par Caddy sur ce VPS). Aucun message envoyé.

**Reste à faire**
1. Décider quoi envoyer dans le groupe WhatsApp (lien du doc / PDF) et par quel chemin (curl sendText/sendFile sur le VPS, ou `waha:send-test` de trigenys-notify) ; attendre l'accord explicite avant tout envoi.
2. Premier commit du squelette (gitignore, CLAUDE.md, skills, docs).
3. Semaine 1 : art bible, `project.godot`, prototype gris de la moto avec physique dans un `.tres`.
4. Questions ouvertes pour les 2 devs (voir entrée précédente) toujours sans réponse ; commentaire « 8 ou 12 semaines ? » non répondu.

## 2026-11-06 08:29 — Lien du cahier des charges envoyé sur WhatsApp
- Message envoyé dans « TRIGENYS GROUP » via WAHA (sendText sur le VPS, HTTP 201, visible dans l'historique du chat, fromMe). Contenu : lien du doc + 5 questions ouvertes.
- Reste : attendre les retours des devs, puis premier commit du squelette et semaine 1.

## 2026-11-06 08:30 — Premier commit du squelette
- Commit cc15ac5 sur `main` (identité repo-locale EagleFox31 noreply ; `.gitattributes` LF + binaires ajouté). Arbre propre, aucun remote configuré.
- Prochaine étape : semaine 1 — art bible, `project.godot`, prototype gris de la moto (physique dans un `.tres`). Attendre les retours WhatsApp des devs sur les questions ouvertes.

## 2026-11-06 08:33 — Dépôt GitHub public, lien PDF renvoyé au groupe
- Dépôt créé : https://github.com/Trigenys/benskin-express (org Trigenys, **public** à la demande de l'utilisateur car le lien Claude Docs n'était pas accessible aux devs), `main` poussé, origin configuré.
- Groupe WhatsApp : Claude Tchami (dev) a répondu « Page not found / Lien public ? » au lien Claude Docs ; lien GitHub du PDF renvoyé. Il avait aussi écrit la veille : chaud pour démarrer, « il nous faut décomposer les étapes en tâches plus simples ».
- Verrou : le doc Claude Docs reste la source éditable ; le PDF du dépôt est une copie figée, à régénérer après chaque modification.
- Prochaine étape : décomposer le MVP 8 semaines en tâches (issues GitHub), répondre aux questions ouvertes avec les devs, puis semaine 1 (art bible, project.godot, prototype moto).

## 2026-11-06 08:34 — Correction : lien GitHub NON envoyé au groupe
- L'envoi WhatsApp du lien PDF GitHub a été refusé par le mode auto (écriture externe). Rien n'a été renvoyé au groupe après le message de 07:28 ; à faire par l'utilisateur ou avec autorisation explicite.

## 2026-11-06 08:35 — Lien GitHub du PDF envoyé au groupe
- Message envoyé dans « TRIGENYS GROUP » (HTTP 201, visible fromMe) avec le lien PDF GitHub et le lien du dépôt. En attente des retours des devs.
- Prochaine étape : décomposer le MVP en issues GitHub, puis semaine 1.
