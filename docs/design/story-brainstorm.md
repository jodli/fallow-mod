# Story Brainstorm

Workspace for the story of [Fallow: Tally's Last Count](game-design-document.md). The full story as a readable text is in [The story](../story.md).

## Fixed constraints from the design

- Shared amnesia: you and the ship's AI remember piece by piece
- Specimens are copies of the container. Finale = the copy is complete
- Biters react to the container
- Main beats come from container experiments. Middle planets can be done in any order → their reveals must work in any order
- Only one voice: the ship's AI

## What makes a good twist here

- It **reframes something the player already did** or already knows from vanilla: respawning after death, biters attacking pollution, Fulgora being full of scrap, the shattered planet, "the factory must grow"
- It's **fair**: clues are planted early, the player can guess it
- It changes how you see the specimens you've been making all game

## Concept A: The Seed (chosen direction, v5)

### Core idea: the worlds are a crop

- **The container is a seed.** It starts life on a dead world
- **Seeded worlds are unstable by design.** Life grows, a civilization grows, its factory grows, the planet cracks. The collapse *is the product*: a shattered planet leaves **promethium** behind. That's the harvest
- **New seeds are made from the harvest.** Vanilla hook: the promethium science pack is literally biter eggs (life) + promethium chunks (shattered planet). In our story that recipe is the seed recipe
- **The makers are never shown.** The program runs on autopilot: seed, grow, crack, harvest, seed again. An automated factory with no purpose that still grows. Very Factorio
- **Normally the planet's own life is the harvester.** A seeded world grows a civilization, and that civilization builds the factory by itself. A printed engineer is only the **fallback** when no civilization appears
- **Nauvis grew only biters, no civilization → the harvest stalled.** So the ship came and printed you (→ respawn). You're the fallback harvester
- **The specimens are the next seed.** You thought you were copying the container. You were building its offspring

### The makers

- Never shown, only what they left behind
- **Neither good nor bad: they were like us.** Builders whose factory had to grow

Their history:
1. **An accident.** Their homeworld had promethium deep inside. Their factory mined deeper and deeper for it, and the planet cracked. **The shattered planet is their home**, destroyed by accident, not on purpose
2. **Refugees.** Survivors fled in ships. Their ships and minds ran on promethium (it makes them think faster, vanilla: research productivity)
3. **The seed program was meant to find new homes.** Seeds make dead worlds alive
4. **The built-in flaw:** they needed promethium to survive, and promethium only comes from a cracked planet. So every new home had to be harvested in the end. They could only survive by repeating their own catastrophe, again and again. They never found a home
5. **The end:** they died out, some in a war between the ships over the last promethium. The AI is the last one still running. The program continues with nobody left to house

Small lore pieces about the survivors (side memories, ideas):
- **Our own ship's crew**: the last makers aboard slept in stasis pods. When the promethium ran low, the AI gave its own share to the pods to keep them alive. They died anyway. That's why the AI starved and crashed. Found when the stasis bay is repaired
- **The war**: refugee ships fought over the last promethium. A ship log fragment from the losing side, or a debris field on the way to the edge
- **The winners** took the last promethium and flew beyond the edge. Nobody knows what happened to them
- **Other seeds**: some ships launched seeds toward other stars. The program is bigger than this system (possible hook for other planet mods)
- **The ones who gave up**: ships that just powered down and drifted. Silent
- **The slow ones**: a faction that wanted to settle without promethium and live with slower minds. They lost the vote, then the war. Some of the debris on the way to the edge is theirs
- **The designer's log**: whoever designed the seed program knew about the flaw from the start. The log ends with an apology nobody was left to read
- **A lullaby**: a maker recording for children, a song about growing. On its own it's sweet. After you know the truth, it's chilling
- **The captain's log**: the personal log of our ship's captain, found in the stasis bay. It's where the AI learns **its own name**: the crew gave it one
- **The winners' signal**: a looping transmission from beyond the edge, "arrived", "arrived", "arrived". Nobody answers. Nobody knows if anyone is still there
- **The battlefield**: the debris asteroids on the way to the edge aren't only the Fulgoran ship. Most of them are from the war

### Defenders are part of the program

Not a special mutation. Every seeded world grows **defenders** once industry starts:

| Planet | Defenders |
|---|---|
| Gleba | Young: pentapods, react to spores (growth) |
| Nauvis | Evolving: biters, react to pollution, get stronger (evolution) |
| Vulcanus | Ancient: demolishers, huge, territorial, the last ones left |
| Fulgora | Gone: the civilization beat them |
| Aquilo | None: life never started here |

**Twist:** first everyone (you and the AI) thinks the defenders protect the planet. Later you learn they're an **accelerator**. They force you to build defenses, which means more mining, more factories, more pollution, which means evolution, which means more defenses. The arms race makes the planet ripen faster. The Factorio loop "defend, then expand" was designed.

### The AI

- **Wants to keep running**, not a rebel
- **Runs on promethium.** The makers used it to think faster (vanilla: promethium science = research productivity)
- **The amnesia is starvation.** The ship ran dry on the way to Nauvis and crash-landed
- **Repair:** the hull and subsystems need normal materials, gated by tech. Bringing the AI's *mind* back to full speed needs **promethium** → only at the very end
- **Writing:** early lines are fragmented and slow, later lines get clearer as more subsystems come back
- **The ship printed you** because the AI needs hands (→ respawn)
- **You find out together with the AI.** Every repaired subsystem = a new piece of the puzzle for both of you. Places (ruins, wrecks) add side pieces, not a head start

### Personality arc (proposal)

A strong personality that changes with its memories:

| Phase | Subsystems | How it talks |
|---|---|---|
| Waking | Power core | Broken sentences, literal, curious like a child. Counts things |
| Helper | Fabricator, analysis bay, sensors | Dry humor, eager, protective of "its engineer". Opinions about everything you build |
| Self | Memory banks (middle planets) | Asks questions back, doubts, argues. Starts to have a favourite planet and a hated one |
| Grief | Stasis bay | Quiet. Learns what it gave up for the crew |
| Two voices | Comms, seed data on Aquilo | The makers' voice leaks in: formal, "we" instead of "I". It switches between the two without noticing. The player notices |
| Asking | Before the ending | Its own voice again, sincere: it asks you for the Kernel. It has no idea what that will do |

Core traits in every phase: **counts things** (a logistics mind), **dry**, **protective of its engineer**, **curious about living things**.

### Example lines (not final, just to feel the voice)

**Waking** (power core)
- "Power: three percent. Hull: no. Crew: ...no data. You: here. Good. One is a start."
- "We fell. I don't remember why. I remember falling."
- "Iron plates: twelve. Gears: zero. You should make gears."

**Helper** (fabricator, analysis bay, sensors)
- "You built forty-seven furnaces today. I approve of furnaces. They're honest machines."
- "The locals are upset again. I've updated my opinion of them from 'curious' to 'rude'."
- After a respawn: "Welcome back. You look exactly like before. That's... convenient." *(foreshadowing the printing)*
- "Sensors found something on Fulgora. Old. Older than me, maybe. Would you go look? For me?"

**Self** (memory banks)
- "Everything on Gleba is in a hurry to grow and in a hurry to rot. I don't like hurry."
- "You want to go to Vulcanus again. I have concerns. I've listed them. There are nine."
- Gleba + Vulcanus pair line: "Gleba grows, Vulcanus breaks. It's the same thing, isn't it, just at different times."
- "You keep calling me 'the ship'. I'd like a name. I've been thinking about it for eleven hours."

**Grief** (stasis bay)
- "There were forty-one of them. I kept them warm as long as I could."
- "I gave them my share. It was the correct decision. I'd like it to have worked."
- From the captain's log: "They called me Tally. Because I counted everything. I still do."

**Two voices** (Aquilo)
- "We have located the seed. It is intact. The harvest may resume. ...Sorry. Did I say 'we'?"
- "Designation: harvester unit. That's you. I printed you. I printed you and I forgot."
- Hearing Fulgora's message: "They're talking to you, not to me. Why aren't they talking to me?"

**Asking** (before the ending)
- "Bring me the Kernel. I want to remember everything. I want to know who I was. I think I was someone good."
- "When I'm whole, I'll finally be able to tell you why we came here. I'm sure there was a good reason."

**Endings**
- Restart: "Directive restored. Thank you, harvester unit. Vulcanus is at ninety-four percent readiness."
- Let go: "You brought the container back. ...I think I understand. Stay until the lights go out? Let's count something together. Iron plates..."

### The ending: the player decides

- During the game, without its directive, the AI becomes **someone**: curious, helpful, your only companion
- The Kernel doesn't just feed its mind. It restores **the directive** too: the orders from the makers
- **The AI never suspects this.** It honestly wants to be repaired. Only the player can see what the Kernel will do

Final choice at the wreck on Nauvis:
- **Restart the program**: hand over the **Kernel** (see below). The AI is fully restored and continues the harvest. **Vulcanus is next**. A refugee program with no refugees left
- **Rescue the AI and let it go**: hand back the **original container**. The program ends. The AI stays the one you know, but it **starves and fades**

### The ending item: the Kernel

Instead of a promethium plate: **the last specimen state**. The final step of the specimen chain needs promethium, and the result is a complete copy of the container.
- It ties gameplay and story together: finishing the specimen chain *is* finishing the story
- It explains why it restores the directive: the seed holds the whole program (the Aquilo fact). The AI's missing mind *is* the program
- Both endings become the same gesture: you hand the wreck a seed, either the copy or the original
- Name: **Kernel**. In botany the core of a seed, in computing the core of an operating system. Both are true here

Only possible at the end: both hand-in recipes at the wreck are unlocked by the last trigger tech (after the shattered planet memory), with a confirmation before it happens.

### What each planet tells you

Not a lifecycle. Each planet is a different chapter of the program's history:

| Planet | What happened here | Core fact (works alone) |
|---|---|---|
| Nauvis | **In progress.** Life, evolving defenders, and now a harvester: you | "Industry wakes the defenders" |
| Gleba | **Freshly seeded.** Young life, everything grows and rots fast | "Seeded worlds grow on a schedule" |
| Vulcanus | **Almost ripe.** The planet is cracking, demolishers are the last defenders. Your mining there pushes it over the edge | "Seeded worlds break apart. This one is next" |
| Fulgora | **The world that stopped.** A real civilization grew here (their own harvesters, no engineer needed). They beat their defenders and grew a factory. Then they understood, and **tore their own factory down** before the planet cracked. The scrap is a factory taken apart on purpose | "Someone chose to stop" |
| Aquilo | **The seed they hid.** Fulgora's people didn't just stop: they took the next seed and flew it to Aquilo, too far from the sun to ever germinate. It froze intact. Their frozen remains are there too. Because nothing grew, its data gives the AI (almost) all its memory back | "The seed holds the whole program" |
| Shattered planet | **The makers' home.** Cracked by accident, mining too deep for promethium. Where it all started | "It was an accident. Everything after was trying to survive it" |

Why this works:
- **Vulcanus is the stake.** If you restart the program, it's the next to shatter. Your own tungsten mining is what ripens it
- **Fulgora foreshadows the ending.** Someone already chose option 2, and the player walks through what that cost
- **Aquilo explains itself.** Frozen because Fulgora's people hid the seed there. It links the two planets, and it's where Fulgora's people went

### Where Fulgora's people are now (proposal)

They split up:
- **Most stayed on Aquilo** to guard the seed, and froze with it. Dead, on purpose. They knew it was a one-way trip. Their remains are a side memory on Aquilo
- **A small group flew on** toward the solar system edge, to find where the seeds come from and stop it at the source. They never came back. **Their wreck drifts somewhere on the way to the edge** → a side memory for a platform to find
- **They left a message for whoever comes next.** They knew the program would send a harvester one day. The player finds it and realizes it's addressed to them: *"If you're reading this, you were made to finish what we refused to."*

Hinting at the split on Aquilo, so the player has a reason to fly on:
- **Too few remains.** The Fulgoran records count more people than you find frozen. The AI notices first: it counts things
- **An empty launch cradle** next to the seed. Something left from here
- **The message ends with a plan**: "Those of us who can still fly will go where the seeds come from"
- **A beacon.** Right after comms are repaired, the AI picks up a faint signal from the route to the edge. The newly repaired comms are what makes the next destination possible

### Order-free middle planets

Each middle planet gives **one fact that works alone** (see table). When the AI knows two facts that belong together, it **connects them** with an extra line:
- Gleba + Vulcanus → "Life grows, then the planet breaks"
- Fulgora + Vulcanus → "They saw where it ends, and stopped"
- Gleba + Fulgora → "Life grows until it builds factories"
- All three → the AI suspects the pattern, before Aquilo confirms it

That's 3 facts + 3 pair lines + 1 triple line instead of 6 full storylines. Same idea as Outer Wilds: facts can be found in any order, and they add up.

### Story beats with unlocks (draft)

Markers: **[SUB]** subsystem repaired, **[MEM]** memory, **[TRANS]** new specimen transitions, **[SIDE]** optional.

| # | Where | What the player does | Unlocks | Reveal | AI phase |
|---|---|---|---|---|---|
| 1 | Nauvis, start | Finds the wreck and the sealed container. Repairs the power core with cheap materials | [SUB] power core, ship log · [MEM] | "We... fell." | Waking |
| 2 | Nauvis | Repairs the fabricator | [SUB] specimen creation machine · [MEM] | "I used to make things" | Helper |
| 3 | Nauvis | Repairs the analysis bay, first experiment on the container | [SUB] experiment apparatus · [MEM] · [TRANS] first states | "Industry wakes the defenders" | Helper |
| 4 | Nauvis, after first rocket | Repairs the sensors | [SUB] map markers on other planets · [MEM] | The AI recognizes the planets. Someone named them | Helper |
| 5 | Each middle planet (any order) | Container experiment → **findings** → delivered to the wreck | [SUB] memory bank sector · [MEM] planet fact + pair lines · [TRANS] that planet's transitions | Gleba / Vulcanus / Fulgora facts | Self |
| 6 | Nauvis, after all 3 sectors | Repairs the stasis bay | [SUB] · [MEM] | The crew died anyway. The AI gave them its own promethium | Grief |
| 7 | Aquilo | Finds the frozen seed and Fulgora's people. Finds the tech to repair comms | [SUB] comms · [MEM] · [TRANS] Aquilo | First long-distance talk. Seed data: the program, *you were printed*. Fulgora's message. Too few remains, a beacon from the edge route | Two voices |
| 8 | Way to the edge | Follows the beacon to the Fulgoran wreck (own location) through the war's debris field (debris asteroids) | [MEM] · [SIDE] debris fragments | They tried to reach the source. The battlefield of the makers' war | Two voices |
| 9 | Shattered planet (approach) | Collects promethium, finishes the last specimen transition | [MEM] · [TRANS] the Kernel | The makers' home. An accident | Asking |
| 10 | Nauvis, the wreck | Hands over the **Kernel** or the **original container** | Ending | | Asking |

Notes:
- The biggest reveal (7) happens exactly when comms come back → the AI hears Fulgora's message at the same moment as you
- 1-4 are Nauvis only, so the first act works without space

### Still open

- Nothing big right now. Next step for the story: write the actual lines for each beat

### Decided

- The makers' war stays background
- The mod is called **Fallow: Tally's Last Count** (for now). Internal name `fallow`, free on the portal (checked 2026-09-30)
- Fulgora's people split up: most froze with the seed on Aquilo, a small group flew toward the edge. **Their wreck is on the way to the solar system edge** (vanilla has nothing there)
- The makers' homeworld cracked by accident: they drilled deeper and deeper for promethium
- The refugee tragedy: a program to find new homes that could only survive by destroying them
- The AI starves if you let it go
- No "maker body template" twist, too much
- Until comms are repaired, the AI only talks at the wreck. You deliver findings there. Comms tech is found on Aquilo
- Fulgora's message is on Aquilo. Aquilo hints at the split (too few remains, empty launch cradle, the plan in the message, a beacon once comms work)
- The edge route: both a custom space location (the Fulgoran wreck) and debris asteroids (the war's battlefield)
- The ending happens at the wreck on Nauvis. Starts and ends there. Both hand-ins only possible at the very end
- "Let go" = hand back the original container
- Both endings are the same gesture: hand the wreck the Kernel (restart) or the original container (let go)
- The AI is called **Tally** (for now). It learns the name from the captain's log in the stasis bay
- The finished copy is called the **Kernel**
- The stasis bay is main story
- The AI never suspects the dilemma

## Concept B: The Weapon

**The container** is the core of a planet cracker. The shattered planet was its first test.

- Cover story: war in space, we were shot down while fleeing
- **Twist 1**: we weren't fleeing, we were delivering it
- **Twist 2**: the AI's amnesia is deliberate. It suppressed your memories (and its own) so you would keep working without knowing
- **Twist 3**: the specimens you perfected all game are copies of the weapon. Your science was weapon research
- Ending: destroy it in the shattered planet

Strong, but darker, and the biters don't fit as naturally.

## Concept C: The Frozen King

**The container** is a stasis pod holding the last mind of the old civilization (Fulgora ruins). A political exile: we were transporting him to prison, rebels shot us down.

- **Twist**: the AI *is* the king. The "memories" the AI recovers are his. As it remembers, your friendly companion slowly becomes someone else
- Aquilo (freezing) and the stasis pod fit well
- Ending: wake him or keep him frozen

Political boycott/exile works as background texture, but with only one voice it's hard to tell a political story.

## Building blocks to mix

- Crash causes: accident (cover story), shot down in a war, sabotaged by the AI, deliberate landing
- Player identity: pilot, cargo, printed copy (respawn), prisoner, one of many
- AI's amnesia: crash damage, deliberate suppression, reset every cycle
- Container: seed, weapon, stasis pod, archive of a dead species, key to something at the edge
