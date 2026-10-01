# Prior Art - Cross-Planet Production in Factorio

Research for [my mod idea](game-design-document.md): one item that gets transformed step by step by the mechanics of each planet.

## Vanilla Space Age

- Promethium pack = 10 biter eggs (Nauvis) + 25 promethium chunks (space) + 1 quantum processor ([wiki](https://wiki.factorio.com/Promethium_science_pack))
- Quantum processor = processing unit + tungsten carbide + superconductor + carbon fiber + lithium plate + fluoroketone ([wiki](https://wiki.factorio.com/Quantum_processor))
- So vanilla *does* touch every planet, but as a **hub model**: each planet ships a finished local product to Aquilo/space. Nothing passes *through* a planet to get processed by its mechanic.
- Planet packs (metallurgic, EM, agricultural, cryogenic) are 100% local. Probably on purpose, because Vulcanus/Fulgora/Gleba can be done in any order.

## Mods that span planets

| Mod | Pattern | Notes |
|---|---|---|
| [Multi-Surface Promethium Plate Recipe](https://mods.factorio.com/mod/multi_surface_promethium_plate_recipe) | **Relay chain**: one item goes space → Fulgora → Gleba → Nauvis → Vulcanus → Aquilo, each step surface-locked | Closest to my idea. Extensible via `msppr` recipe field. 1.59K downloads, 2.0 only, CC BY-NC-ND |
| [Solar System Science](https://mods.factorio.com/mod/SolarSystemScience) | Cross-pollinated ingredients + hub (universe plate, stellar centrifuge) | Each planet ingredient needs imports from another planet. 586 downloads, active |
| [Krastorio 2 Spaced Out](https://mods.factorio.com/mod/Krastorio2-spaced-out) | Checklist recipe: matter research data needs samples from all planets | [source](https://github.com/Polka37/Krastorio2-spaced-out/blob/main/prototypes/recipes/tech-cards.lua) |
| [Challenging Pack Logistics](https://mods.factorio.com/mod/harder-pack) | Transit as processing step: recharge EM packs on platforms, cool cryo packs | Only existing packs |
| [Nauviax's Science Overhaul](https://mods.factorio.com/mod/nauv-so) | Planets make data, platforms make packs with promethium caught in transit | |
| [Particle Physics](https://mods.factorio.com/mod/particle-physics) | Two planets: Gleba deuterium + Aquilo lithium | |
| Castra, Metal and Stars, Rubia, Apia-Carnova | 2-3 planet links in planet mods | |
| Rainbow Science Pack, Nobelium Science | "One of every pack" | Lazy variant |
| [Space Exploration](https://mods.factorio.com/mod/space-exploration) (1.1) | Deep space science needs all four specialist sciences from different worlds | The big precedent |

Most planet mods stay local: Maraxsis, Cerys, Corrundum, Paracelsin, Secretas & Frozeta, Moshine, Muluna, Pelagos, Lignumis.

## Puzzle / loop references

- **SE Arcospheres** ([wiki](https://spaceexploration.miraheze.org/wiki/Arcospheres)): finite catalysts in 8 polarities. Fold recipes turn 2 spheres into 2 others, inversion flips 4. Recipes use them as catalysts and give back random polarities → balancing puzzle. Loved and hated, mostly because of the randomness.
- **Ultracube** ([mod](https://mods.factorio.com/mod/Ultracube)): one irreplaceable cube is the catalyst for all bulk processing. No copy-paste scaling, the game is about cube uptime, circuits, routing. Victory screen shows cube utilisation. ~30h, finale is reconstructing the cube and you can fail ([review](https://blog.xaviershay.com/articles/factorio-ultracube-review.html)).
- **SpaceChem**: two layers - program a reactor (micro), connect reactors with pipes (macro). Fixed input → target output, scored on cycles/size.

## Story / characters in mods

- **[Eneas](https://mods.factorio.com/mod/moon-eneas)** (2.0-2.1, 8.13K downloads): closest to our story ideas. Crashing debris on Nauvis gives a "weathered artifact". A superintelligence **Unit-05** contacts you early, has "hundreds of written lines of dialogue", comments on progress, gives supplies. Lore entries via Informatron. Timed scripting, some unreproduced multiplayer desync reports. So: a talking AI in a mod **exists**
- **[Story Missions](https://mods.factorio.com/mod/Story-Missions)** (1.1-2.0, 30.7K downloads): 10 scripted missions with a lore-friendly story about the crash-landed engineer. No Space Age support
- **[Dialogue box](https://mods.factorio.com/mod/dialogue-box)** (1.1 only): library for dialogue trees with triggers, conditions and a dialogue log
- **Vanilla Compilatron**: the old tutorial robot talked through speech bubbles. The `compi-speech-bubble` entity (type `speech-bubble`) is still in the base game data
- Not found: a talking **biter**, or dialogue played inside camera cutscenes

## Enemies per planet

From the [wiki](https://wiki.factorio.com/Enemies):

| Planet | Enemies | What drives them |
|---|---|---|
| Nauvis | Biters, spitters, worms | Pollution → attack waves. Expand. Evolve from time, pollution, nest kills |
| Gleba | Pentapods | Spores from agriculture → attacks. Expand on marsh. Own evolution factor |
| Vulcanus | Demolishers | Territory only. No pollution response, no expansion |
| Fulgora, Aquilo | None | Lightning / cold are the hazards |

- Biter eggs spoil into a big biter (quality egg → quality biter). Pentapod eggs hatch too
- The captive biter spawner can only be built on Nauvis
- Pollution does not change eggs in vanilla

## Open design space

- Mid-game cross-planet chains (everything existing is post-Aquilo / promethium)
- Round trips A → B → A instead of one-way relay or hub
- Planet mechanics as actual transformation steps, not just ingredient lists
- Decay/timers during transport as part of the puzzle
- 2.1 platform-to-platform logistics as the "pipe" layer
