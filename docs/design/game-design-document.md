# Fallow: Tally's Last Count - Game Design Document

Internal mod name `fallow`. A standalone Factorio: Space Age story and production mod with two parts:

- **Specimens** (gameplay): copies of the sealed container, grown under pollution on Nauvis and processed across the other planets to replace the ship's four crushed ovens (`growing`, `heat`, `current`, `cold`), then finished in deep space with promethium into **the Kernel**
- **The story**: the crashed ship's AI (**Tally**) that you repair stage by stage at the wreck on Nauvis. You both start without memories and piece together what the worlds, the container, and you are for

Full narrative: [The story](../story.md). Earlier notes: [Story brainstorm](story-brainstorm.md), [Mod portal README](mod-portal-readme.md), [Prior art research](prior-art-research.md).

## Core Decisions

- **Story-driven, vanilla-first**: every mechanic exists to serve [The story](../story.md) using native Space Age systems (spoilage, `surface_conditions`, trigger technologies, space locations) and low UPS overhead
- **Two things, two jobs**: specimens = cross-planet factory puzzle; the wreck, the container, and the Analysis Bay = story progression
- **11 specimen states (the $2^3$ relay cube)**: middle-planet science needs 1 hop from Nauvis; Aquilo science requires a single specimen to tour all 3 middle planets in sequence (in any visit order) before freezing on Aquilo
- **Self-healing spoilage**: all 7 unstable treated states (`1-planet`, `2-planet`, `3-planet`) spoil back into `Awakened`, so every planet and hub only filters one fallback item
- **Creation on Nauvis requires pollution**: the Fabricator only runs when local chunk pollution is high → continuous biter pressure on Nauvis
- **Order-free middle planets & relay routes**: because all subsets of `{Gleba, Vulcanus, Fulgora}` exist, any planet visit order and any 3-planet platform courier route works
- **Silence before Aquilo**: until the Fulgoran Relay is built on Aquilo, Tally can only speak at the Nauvis wreck. Planet experiments produce physical **Record** items that must be shipped home
- **No worldgen ruins or camera cutscenes**: experiments run anywhere on the target planet via `surface_conditions`. Story beats land in the **Ship Log GUI** and console/speaker messages (force-wide, multiplayer-safe)
- **One edge location ("The Field")**: a custom `SpaceLocationPrototype` between Aquilo and the Solar System Edge with ship-debris asteroids and the Fulgoran crew log
- **Two endings at the Nauvis wreck**: insert **the Kernel** (restore the directive) or **the Container** (let Tally destroy the master seed and fade). The game continues after either ending

## Specimens ("Four Crushed Ovens" Relay Cube)

The ship's fabricator has one working oven left on Nauvis; its ovens for growing (Gleba), heat (Vulcanus), electric current (Fulgora), and deep cold (Aquilo) were crushed in the crash.

- **Middle-planet science** requires a **1-treatment specimen** (`Nauvis → Planet X`)
- **Aquilo / endgame science** requires a **single specimen to tour all three middle planets** (`Nauvis → Planet 1 → Planet 2 → Planet 3 → Aquilo`, in any order you route your platforms) before its decay timer expires, then get cold-locked on Aquilo

### Flow ($2^3$ Treatment Lattice)

```
Nauvis (Fabricator + pollution):
  [Inert] ──► [Awakened]  (0 treatments)
                  │
                  ├──► [Grown] (G)          ──► used in Agricultural science
                  ├──► [Tempered] (V)       ──► used in Metallurgic science
                  └──► [Charged] (F)        ──► used in Electromagnetic science
                         │
                         ▼  (2nd planet hop, any order)
                  ├──► [Grown + Tempered] (G+V)
                  ├──► [Grown + Charged] (G+F)
                  └──► [Tempered + Charged] (V+F)
                         │
                         ▼  (3rd planet hop, remaining middle planet)
                       [Primed Specimen] (G+V+F)
                         │
                         ▼  (Aquilo Cryogenic Plant)
                       [Frozen Specimen] (never spoils ──► used in Cryogenic science)
                         │
                         ▼  (Deep Space + fresh Promethium)
                       [The Kernel] (used in Promethium science + Ch. 10 Ending)

  * All 7 unstable states (G, V, F, G+V, G+F, V+F, G+V+F) spoil back into [Awakened].
```

### The 11 Specimen Items

| # | State | Treatments | Where made | Spoils into | Role |
|---|---|---|---|---|---|
| 1 | **Inert Specimen** | — | Nauvis (Fabricator + high pollution) | — | Raw copy grown from stressed local tissue |
| 2 | **Awakened Specimen** | `{}` | Nauvis (unlocked in Ch. 3) | — | Base export to middle planets; universal spoilage fallback |
| 3 | **Grown Specimen** | `{G}` | Gleba (Biochamber) | `Awakened` | 1-hop state; Agricultural science + relay step |
| 4 | **Tempered Specimen** | `{V}` | Vulcanus (Foundry) | `Awakened` | 1-hop state; Metallurgic science + relay step |
| 5 | **Charged Specimen** | `{F}` | Fulgora (EM Plant) | `Awakened` | 1-hop state; Electromagnetic science + relay step |
| 6 | **Cultured-Tempered Specimen** | `{G, V}` | Vulcanus (from `{G}`) or Gleba (from `{V}`) | `Awakened` | 2-hop relay state |
| 7 | **Cultured-Charged Specimen** | `{G, F}` | Fulgora (from `{G}`) or Gleba (from `{F}`) | `Awakened` | 2-hop relay state |
| 8 | **Tempered-Charged Specimen** | `{V, F}` | Fulgora (from `{V}`) or Vulcanus (from `{F}`) | `Awakened` | 2-hop relay state |
| 9 | **Primed Specimen** | `{G, V, F}` | 3rd middle planet (from any 2-hop state) | `Awakened` | Unstable 3-treatment copy racing to Aquilo |
| 10 | **Frozen Specimen** | `{G, V, F, Cold}` | Aquilo (Cryogenic Plant) | — (`spoil_ticks = nil`) | Cold-locked copy; Cryogenic science + Edge export |
| 11 | **The Kernel** | Complete | Space platform (`Frozen` + promethium) | — | Finished seed; Promethium science + Mind Core ending |

### Why the 11-state cube works cleanly

- **Any route order works**: all 6 permutations of `Gleba → Vulcanus → Fulgora` use the same 11 items
- **One fallback item everywhere**: because all 7 unstable states spoil back to `Awakened` (rather than stepping backward along permutation history), landing pads, silos, and platform hubs only ever filter **one** spoiled item (`Awakened`), which can immediately re-enter the local planet's treatment machine as a fresh 1-hop specimen
- **Tunable leg timers**: `RecipePrototype.result_is_always_fresh = true` lets each planet treatment reset the spoil timer for the next interplanetary hop

## Story & Wreck Progression (10 Chapters)

The crashed ship on Nauvis is an indestructible, unminable entity (`destructible = false`, `minable = false`; spawned by script if freeplay's crash site is disabled). Opening the wreck (`on_gui_opened`) shows **Tally's console**, **subsystem repair / hand-in slots**, and the **Ship Log**.

| Ch. | Title | Player Action | Unlocks | Story Beat |
|---|---|---|---|---|
| **1** | **One is a start** | Deliver basic parts + power to the Nauvis wreck | **Power core**, **Ship Log GUI**, **Container** in hold | Tally wakes up at 3% power, counts 12 iron plates, remembers falling |
| **2** | **Forty-seven furnaces** | Repair the **Fabricator** at the wreck | **Fabricator** machine + `Inert` specimen recipe | The four crushed ovens; pollution ("your smoke") wakes biters; first hint about respawn printing |
| **3** | **Something underneath** | Repair the **Analysis Bay**; run first scan on Nauvis | Craftable **Analysis Bay** + `Awakened` specimen recipe | The container answers something deep under Nauvis; industry wakes the defenders |
| **4** | **Names** | Launch the **Sensors** package in a rocket | Planet survey recipes in the Analysis Bay | Tally sees the system from orbit and realizes someone put the planet names inside it |
| **5** | **Three worlds** | Build an **Analysis Bay** on Gleba, Vulcanus, and Fulgora (any order) → craft each world's **Record** → deliver Records to the Nauvis wreck | **Memory banks** (3 sectors) + each planet's specimen transition | Gleba is newly planted; Vulcanus is about to break; Fulgora tore its own factory down and carried its heart to Aquilo. Pair + triple connection lines |
| **6** | **Forty-one** | Repair the **Stasis Bay** at the wreck (after all 3 Records) | Aquilo relay & cryo-specimen tech | 41 frosted pods; Tally gave its reserve to keep the crew warm; captain's log gives Tally its name and mentions "the planting" |
| **7** | **Too few** | Build & heat-pipe the **Fulgoran Relay** + run Analysis Bay on Aquilo | **Long-range comms** (Tally speaks on all surfaces), `Frozen` specimen recipe, route to **The Field** | The seed program revealed; Tally printed you; "we" slips into Tally's voice; Fulgora's message in the ice; 171 of 206 bodies; beacon from the edge route |
| **8** | **The field** | Fly a platform to **The Field** (`SpaceLocationPrototype` beyond Aquilo) and collect the **Fulgoran Black Box** | Deep-space archive prep | Ship-debris asteroids from the makers' war; Fulgoran crew log about the dying ship mind (*"the ship is inside the seed"*) |
| **9** | **Home** | Deliver **1 Promethium chunk** to the Nauvis wreck | **The Archive** + **The Kernel** recipe | The shattered planet was the makers' homeworld, cracked by accident; designer's apology; the slow ones; the lullaby; Tally asks for the Kernel |
| **10** | **The last count** | At the Nauvis wreck **Mind Core**, confirm handing over **the Kernel** or **the Container** | Ending log entry + achievement / post-game state | **Kernel:** directive restored, cold voice, Vulcanus at 94%. **Container:** Tally destroys the master seed with its last power and counts iron plates with you until the lights go out |

## Key Technical Implementation Notes

- **Wreck & Container safety**:
  - The Container stays stored in the wreck's GUI (or, if taken into the player's inventory, has a 1-click **Recall to Wreck** button in the wreck GUI and `auto_recycle = false` with self-recycling stripped in `data-final-fixes.lua`)
  - All wreck repairs, Record deliveries, and the Chapter 10 ending choice use the wreck's custom `on_gui_opened` GUI + `"scripted"` trigger technologies (`force.script_trigger_research`), giving a clean confirmation dialog before the final hand-in
- **Pollution check on the Fabricator**:
  - Bucketed `on_nth_tick` checks `surface.get_pollution(entity.position)` for registered Fabricators, toggling `entity.active` and setting `entity.custom_status` (`"Requires high pollution"`) when below threshold
- **The Field (Edge route)**:
  - Custom `SpaceLocationPrototype` (`fallow-the-field`) positioned between `aquilo` and `solar-system-edge` with custom ship-wreck `starmap_icon`
  - Custom `AsteroidPrototype`s for hull debris along the connection, dropping a **Fulgoran Black Box** chunk collected by standard asteroid collectors
- **Lore & Multiplayer**:
  - All story progress is stored per-force in `storage`
  - Every chapter and log entry lives permanently in the **Ship Log GUI** (accessible via shortcut button or opening the wreck), with toast/console notifications when new entries arrive

## Next Steps

- [ ] Create mod scaffold (`info.json`, `data.lua`, `data-final-fixes.lua`, `control.lua`, `locale/en/fallow.cfg`)
- [ ] Prototype and tune the 11-state specimen relay cube (spoil timers, `result_is_always_fresh`, rocket stack sizes)
- [ ] Implement the Nauvis wreck entity, pollution-checked Fabricator, and Analysis Bay
- [ ] Build the Wreck + Ship Log GUI and wire up Chapters 1–10 from [The story](../story.md)
- [ ] Add `fallow-the-field` space location and debris asteroid definitions
