# World Simulation Engine: Foundational Rules

## Overview
This document defines the **Layer 0** and **Layer 1** systems that govern the living world. These are the immutable laws of physics, time, and causality that all other systems (economy, combat, NPCs) must obey. 

The goal is to create a deterministic yet emergent simulation where complex behaviors arise from simple, consistent rules.

---

## Layer 0: The Simulation Core

### 1. Time System
Time is continuous, persistent, and affects every system.

- **Scale**: `1 real-minute = 10 game-minutes` (2.4-hour day cycle).
- **Persistence**: Time flows even when players are offline. Server calculates elapsed time based on real-world duration.
- **Impact**:
  - **NPC Schedules**: NPCs wake, work, eat, socialize, sleep based on time.
  - **Resource Spawning**: Plants grow, ores regenerate, animals migrate based on seasons/time.
  - **Event Triggers**: Certain events only occur at specific times (e.g., "Blood Moon," "Eclipse").
  - **Decay**: Food spoils, structures degrade, fires burn out over time.

### 2. Space & Physics
The world obeys consistent physical laws.

- **Gravity**: Standard gravity applies, except in specific "Anomaly Zones" (e.g., Floating Islands).
- **Collision**: Objects have physical presence. Players cannot clip through walls; projectiles interact with terrain.
- **Destructibility**: 
  - **Soft Destruction**: Grass flattens, snow shows footprints, water ripples.
  - **Hard Destruction**: Walls can be breached, trees felled, bridges destroyed (requires tools/explosives).
  - **Permanence**: Destruction persists until repaired by players or NPC crews.
- **Fluid Dynamics**: Water flows downhill, fills basins, floods during rain. Fire spreads based on wind and fuel.

### 3. Causality Engine
Every action has a reaction. The system tracks cause-and-effect chains.

- **Direct Causality**: Player kills wolf → Wolf corpse appears → Scavengers arrive.
- **Indirect Causality**: Player kills wolf → Wolf population drops → Deer population rises → Overgrazing occurs → Vegetation degrades → Soil erosion.
- **Delayed Causality**: Player saves merchant → Merchant survives to trade → New goods appear in village 2 weeks later → Economy shifts.
- **Rule**: No action is truly isolated. The system logs significant events for future ripple effects.

---

## Layer 1: Environmental Systems

### 4. Weather System
Weather is dynamic, regional, and gameplay-altering.

- **Generation**: Procedural based on biome, season, and global climate patterns. Not random; follows meteorological logic.
- **Types**: Rain, Snow, Fog, Storm, Heatwave, Blizzard, Acid Rain (magical zones).
- **Gameplay Impacts**:
  - **Visibility**: Fog/Storms reduce sight range.
  - **Movement**: Rain makes slopes slippery; snow slows movement; mud traps heavy armor.
  - **Combat**: Lightning can strike metal armor; fire spells weaken in rain; ice spells strengthen in snow.
  - **Ecology**: Rain triggers plant growth; drought causes animal migration.
- **Prediction**: Players can learn to predict weather via sky observation, barometers, or NPC meteorologists.

### 5. Ecology & Ecosystem
Creatures and plants exist as part of a food web, not as static spawns.

- **Food Chain**: Predators hunt prey; herbivores graze; scavengers clean corpses.
- **Migration**: Herds move seasonally between grazing grounds. Predators follow.
- **Population Dynamics**: 
  - Overhunting → Species scarcity → Higher prices for related resources.
  - Predator removal → Prey overpopulation → Resource depletion.
- **Behavior States**: Creatures have states: `Idle`, `Hunting`, `Fleeing`, `Mating`, `Sleeping`, `Aggressive`.
- **Extinction**: Local extinction is possible. Reintroduction requires player/NPC effort (breeding programs).

### 6. Geography & Biomes
The world is divided into distinct regions with unique rules.

- **Biome Types**: Forest, Desert, Swamp, Tundra, Mountain, Ocean, Volcanic, Magical Anomaly.
- **Regional Rules**:
  - **Desert**: Heat stress, water scarcity, sandstorms.
  - **Swamp**: Disease risk, movement penalty, poison flora.
  - **Tundra**: Freezing damage, limited resources, aurora phenomena.
  - **Volcanic**: Lava flows, ash clouds, fire resistance required.
- **Boundaries**: Biomes transition gradually. No invisible walls.

---

## Layer 2: Information & Knowledge Systems

### 7. Information Propagation
News travels physically, not instantly.

- **Speed**: Determined by distance and travel speed of messengers.
  - **Local**: Minutes to hours (village gossip).
  - **Regional**: Days (traveling merchants).
  - **Continental**: Weeks (ships, royal decrees).
- **Distortion**: Rumors change as they spread. Facts become exaggerated or lost ("Telephone Game" mechanic).
- **Channels**: 
  - **Oral**: Bards, travelers, tavern gossip.
  - **Written**: Books, newspapers, wanted posters.
  - **Magical**: Scrying orbs, telepathy (rare/expensive).
- **Player Impact**: Players can accelerate/slow information by carrying messages personally or intercepting messengers.

### 8. Knowledge State
Knowledge is an object with properties: `Discovered`, `Public`, `Lost`, `False`.

- **Discovery**: Player finds info via exploration, reading, or conversation.
- **Verification**: Info can be `Verified` (proven true), `Debunked` (proven false), or `Unverified` (rumor).
- **Persistence**: 
  - If all carriers of a knowledge piece die/books burn → Knowledge becomes `Lost`.
  - If rediscovered later → Marked as `Rediscovered`.
- **Value**: Unverified rumors are cheap; Verified secrets are expensive; Lost knowledge is priceless.

---

## Layer 3: Life & Death Systems

### 9. NPC Lifecycle
NPCs are born, live, and die autonomously.

- **Aging**: NPCs age in real-time. Children grow to adults; adults become elderly.
- **Professions**: NPCs train, work, retire. Skills improve with practice.
- **Relationships**: NPCs form friendships, rivalries, marriages, families dynamically.
- **Death**:
  - **Natural**: Old age, disease, accidents.
  - **Violent**: Combat, murder, disasters.
  - **Succession**: Upon death, heirs inherit property/titles. If no heir, assets go to state/guild.
- **Memory**: NPCs remember interactions permanently. Legacy passes to descendants.

### 10. Creature Lifecycle
Monsters/animals follow biological rules.

- **Breeding**: Seasonal cycles. Nests/lairs contain young (vulnerable).
- **Growth**: Juveniles → Adults → Elders (stronger/wiser).
- **Death**: Corpses decay, attract scavengers, fertilize soil.
- **Evolution**: Rare chance for mutated variants in high-magic zones.

---

## Failure & Consequence Design

### 11. Failure States
Failure is not "Game Over"; it is a narrative branch.

- **Combat Failure**: 
  - **Captured**: Wake up imprisoned, lose equipment, must escape.
  - **Rescued**: NPC saves you, incur debt/obligation.
  - **Left for Dead**: Lose items, spawn at nearest shrine with injury debuff.
- **Exploration Failure**: 
  - **Lost**: Waste time/resources, encounter random events.
  - **Trapped**: Must solve puzzle/use item to escape.
- **Social Failure**: 
  - **Reputation Loss**: Faction hostility, higher prices, denied services.
  - **Betrayal**: NPC turns enemy, reveals player secrets.
- **Economic Failure**: 
  - **Bankruptcy**: Lose property, forced into labor/debt quests.
  - **Market Crash**: Inventory value plummets.

### 12. Cascading Consequences
Small failures can trigger large events.

- **Example**: Player fails to escort merchant → Merchant dies → Goods never arrive → Village faces famine → Riots occur → King sends troops → Martial law declared.
- **Design Rule**: The system tracks key variables (food supply, morale, security). When thresholds breach, events trigger automatically.

---

## Implementation Priorities (Vertical Slice)

For the initial prototype, focus on these core rules:
1. **Time Cycle**: Day/Night affecting NPC schedules and monster spawns.
2. **Basic Weather**: Rain/Fog affecting visibility and movement.
3. **Simple Ecology**: Wolves hunt deer; deer flee.
4. **Information Delay**: News takes time to reach neighboring NPC.
5. **Permanent Death**: One key NPC can die, triggering successor logic.
6. **Failure Branch**: One quest where failure leads to a different (but playable) outcome.

---

## Metrics for Simulation Health
- **Emergence Frequency**: How often do unplanned events occur? (Target: High)
- **Causality Chain Length**: How many steps from cause to final effect? (Target: 3+)
- **Player Surprise**: % of players encountering unique situations not seen by others.
- **System Stability**: Does the simulation crash or produce impossible states? (Target: Zero)
