# Fallow: Tally's Last Count - Game Design Document

Working name (earlier "Planet Chem"), internal mod name `fallow`. A standalone Space Age mod with two parts:

- **Specimens** (gameplay): created on Nauvis, then transformed step by step by the mechanics of other planets until they reach the state a science tier needs
- **The story**: a sealed container from your crashed ship, and the ship's AI that you repair piece by piece. You both have amnesia and find out together what's going on

Story details: [Story brainstorm](story-brainstorm.md), full story: [The story](../story.md), portal text draft: [Mod portal README](mod-portal-readme.md). Research and references: [Prior art research](prior-art-research.md).

## Decisions

- Two things, two jobs: specimens = gameplay, container + ship AI = story
- Specimens are copies of the container. Finale = the copy is complete
- Specimens are a **state machine**: each specimen item is one named state, planet recipes are transitions, spoiling is a transition back
- Specimens can only be **created on Nauvis**. Creation needs pollution → an ongoing defense problem on Nauvis
- **No extra catalyst.** Too tedious
- **Lore unlocks transitions.** The specimen chain grows as you learn more
- **Middle planets only need Nauvis states.** A middle planet's transitions never require a state from another middle planet → free visit order
- Container experiments are **storytelling, not challenge**: easy, no risk, no babysitting. The container can't be destroyed or lost
- **Shared amnesia.** You and the ship's AI recover your memories piece by piece
- **The ship's AI is repaired in stages** and is the only voice of the story
- **Until comms are repaired, the AI only talks at the wreck on Nauvis.** You bring your findings back to it. The comms tech is found on Aquilo
- **The story starts and ends at the wreck on Nauvis.** The ending is handing something to the wreck: the Kernel (restart) or the original container (let go). Both only possible at the very end
- Names: the mod is **Fallow: Tally's Last Count** (for now), the AI is **Tally** (for now), the finished copy is the **Kernel**
- The AI has a **strong personality that changes** as its memories come back
- **Cutscenes are a bonus, never the only channel.** Every story beat also lands in shared channels (ship log, speech bubbles, force-wide messages, trigger techs). Story progress is per force → multiplayer works
- No capsule-style (procession) cutscenes
- **A real location on the way to the solar system edge**: the wreck of the Fulgoran ship
- **Vanilla mechanics first**: closer to the original game and UPS friendly
- **Standalone mod**, no score metric

## Specimens

### Creation on Nauvis

- Needs high pollution where it runs. Pollution also draws biter attacks and raises evolution → you defend your specimen production for as long as you make science
- The creation machine comes from the repaired **fabricator** subsystem of the ship

### State machine

Each specimen is in exactly one state. Planet recipes move it to the next state, spoiling moves it back. Placeholder example:

```
Nauvis:   [Inert] --creation--> [Awakened]
Vulcanus: [Awakened] --heat--> [Tempered] --cools--> [Awakened]
Fulgora:  [Awakened] --charge--> [Charged]
Aquilo:   [Tempered] --freeze--> [...]   (after all middle planets)
```

- Order matters automatically: a transition only exists from certain states
- Each science tier needs a specific state
- Every state gets a lore name (a stage of copying the container)
- Around 10-20 states. Exact number → prototype

### Planet treatments

| Planet | Treatment |
|---|---|
| Nauvis | Creation (pollution) |
| Vulcanus | Heat. Cools down over time |
| Fulgora | Charge. Leaks over time |
| Gleba | Culture. Grows over time, overgrows if you're too slow |
| Aquilo | Freeze. Stops decay |
| Space | Transit |

## Ship AI

The crashed ship on Nauvis has an AI. Inspired by the book "Starship of the Ancients". It's the only voice of the story.

- Hull and subsystems are repaired with **normal materials**, gated by tech
- The AI's **mind** needs **promethium** to run at full speed → the ending
- Every repair = new abilities + new memories + the personality shifts a bit
- Difference to Eneas' Unit-05: our AI is broken, recovers with you, and is bound to the ship and the container

### Subsystems (proposal)

| # | Subsystem | When | What it unlocks in the game | Story |
|---|---|---|---|---|
| 1 | **Power core** | Nauvis, very early | AI wakes up, ship log | Fragmented speech, barely remembers the crash |
| 2 | **Fabricator** | Nauvis, mid | Specimen creation machine | "I used to make things." Later: it also made *you* |
| 3 | **Analysis bay** | Nauvis, mid | The container experiment apparatus | First experiment on the container |
| 4 | **Sensors** | After first rocket | Map markers for places on other planets (`force.add_chart_tag`) | The AI recognizes the planets |
| 5 | **Memory banks** (3 sectors) | One per middle planet | Findings from a planet are delivered here → memory + that planet's transitions | The three planet facts, plus connecting lines |
| 6 | **Stasis bay** | After the memory banks | Main story | The pods: the last makers aboard died on the way. The captain's log gives Tally its name |
| 7 | **Comms** | Tech found on Aquilo | AI talks on any planet | First long-distance talk, right at the frozen seed |
| 8 | **Mind core** | Endgame | The ending | The Kernel (or the container) |

### Talking to the AI before comms

- The AI is only reachable at the wreck on Nauvis
- A container experiment on a middle planet produces a **findings** item
- The findings have to get back to the wreck (carry it or ship it) and go into the **memory banks** → memory + trigger tech that unlocks that planet's transitions
- Multiplayer: anyone can deliver findings, everyone sees the result in the ship log

### Technical

- The freeplay crash site can be disabled (freeplay remote interface) → spawn our own wreck if it's missing
- The wreck must be protected (not minable, not destroyable by biters). Check how the vanilla crash-site entities behave

## Memories

| Source | Role | Trigger (vanilla tech triggers) |
|---|---|---|
| **Findings delivered to the wreck** | Main story | `craft-item`: the memory bank recipe consumes the findings |
| **Ship repair stages** | New abilities + a memory each | `craft-item` / `build-entity` for the repair parts |
| **Places** (ruins, wrecks) | Side memories, exploration | `mine-entity` on a special ruin, or `scripted` when a player gets close |

- The main story never depends on finding a place. Places are optional extras
- The sensors point you to the places

## The Fulgoran wreck (edge location)

A real location on the way to the solar system edge, where vanilla has nothing.

- **Own space location**: `SpaceLocationPrototype` supports its own `starmap_icon(s)` → a broken ship instead of a round planet. Platforms can travel there and park
- **Debris on the way**: space connections and locations have `asteroid_spawn_definitions`, and asteroids are moddable (Metal and Stars adds its own) → asteroids that look like ship debris. Their chunks could be wreck fragments → side memories
- Check: what a parked platform shows as background at a custom location

## Ending

- Starts and ends at the wreck on Nauvis
- **Restart the program**: hand the wreck the **Kernel**, the finished copy and last specimen state. Its final transition needs promethium (see [Story brainstorm](story-brainstorm.md))
- **Let the AI go**: hand the wreck the **original container**. You found it in the wreck, you return it, and it goes down with the ship
- Both hand-in recipes are unlocked only by the last trigger tech (after the shattered planet memory), with a confirmation dialog before anything happens

## Cutscenes

Camera cutscenes for key moments, the AI talks. Always skippable, always also in the ship log.

Toolkit (Lua API 2.1):
- **Camera**: `player.set_controller{type = defines.controllers.cutscene, waypoints = {...}}`. Waypoints target a position, an entity or a unit group. The vanilla crash-site intro works the same way
- **Events**: `on_cutscene_started`, `on_cutscene_waypoint_reached`, `on_cutscene_finished`, `on_cutscene_cancelled`
- **Speech**: `speech-bubble` entity prototype (vanilla `compi-speech-bubble` precedent), `rendering` text, or a GUI panel with a portrait
- **Effects**: `surface.execute_lightning`, `surface.play_sound`, `surface.play_music`, spawned entities / explosions
- **Multiplayer**: plays for the player who triggered it, everyone else gets a notification and a **replay** button in the ship log

## Lore delivery

- Trigger technologies
- Ship log GUI with collected memories
- Item, entity and technology descriptions, Factoriopedia
- Tips-and-tricks entries on triggers
- Places on each planet

## Tech notes

- Each specimen state = one item prototype, generated in the data stage
- Decay = `spoil_ticks` + `spoil_result`
- Planet lock = `surface_conditions`
- Recipes are fixed at load time. Techs unlock recipes (`unlock-recipe`), script can toggle `force.recipes[name].enabled`

## Open questions

- [ ] Story: remaining details in [Story brainstorm](story-brainstorm.md)
- [ ] Subsystems: confirm the list above and its order
- [ ] Prototype: pollution in specimen creation (vanilla recipes can't check pollution → script)
- [ ] Prototype: number of states
- [ ] Prototype: do we need spoiling in rockets / cargo pods? Decide after the prototype
- [ ] Prototype: custom space location for the Fulgoran wreck (broken-ship `starmap_icon`, what a parked platform shows)
- [ ] Prototype: debris asteroids on the edge route (custom `AsteroidPrototype` + `asteroid_spawn_definitions`, chunks as wreck fragments)
