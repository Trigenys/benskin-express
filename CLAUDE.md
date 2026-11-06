# Benskin Express

Jeu moto-taxi 2D Android (boucle courte type Hill Climb Racing / Crazy Taxi). Trigenys, 3 devs, pas d'artiste.

## Stack
- Godot 4.x (GDScript), Android API 24+, APK < 60 Mo.
- MVP 8 semaines : Douala seule, 3 motos, 6 passagers, pubs récompensées + achat sans pub.

## Références
- Cahier des charges : `Benskin-Express-Cahier-des-charges.pdf` (source : Claude Docs, lien dans PASSATION-benskin.md).
- Passation : `PASSATION-benskin.md` (ajout seulement).
- Skills gamedev : `.claude/skills/` (router + Godot + disciplines), copie épinglée, voir `docs/engineering/skills-pin.md`.

## Conventions
- RAIDER : pas de nombres magiques, physique et économie dans des `Resource` (.tres) éditables.
- Tests GDScript headless (`godot --headless`) dès le prototype ; CI change-scoped.
- Commits : description technique uniquement.
