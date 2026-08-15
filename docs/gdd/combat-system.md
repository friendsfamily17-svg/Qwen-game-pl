# Combat System

## 1. Overview

### 1.1 Purpose
The combat system delivers intense, skill-based real-time action where player mastery—not character levels—determines success. Every swing, dodge, and block requires physical input and timing. Death has permanent consequences, reinforcing the Living World's core pillar: **actions matter**.

### 1.2 Design Pillars Alignment
- **Knowledge > Gold**: Combat techniques are discovered, not bought; mastery comes from practice and observation
- **World Remembers**: Combat reputation spreads; witnesses report your fighting style and deeds
- **Discovery Drives Design**: Players uncover advanced techniques through experimentation and mentorship
- **Permanent Consequences**: Injury, equipment loss, and death create meaningful stakes

### 1.3 Scope
This document covers:
- Real-time hit detection and body targeting
- Skill-based progression (no traditional XP)
- Weapon handling and combat styles
- Defensive mechanics (blocking, dodging, parrying)
- Injury and fatigue systems
- Group combat dynamics
- AI opponent behavior

---

## 2. Core Mechanics

### 2.1 Hit Detection System

#### 2.1.1 Body Targeting Zones
Players aim at specific body parts with mouse/controller direction:

| Zone | Hit Difficulty | Damage Multiplier | Critical Chance | Notes |
|------|---------------|-------------------|-----------------|-------|
| Head | Very High | 2.5x | 40% | Instant kill on critical; hardest to hit |
| Neck | Very High | 2.0x | 35% | Bleed effect; high lethality |
| Torso | Medium | 1.0x | 10% | Largest target; protects vital organs |
| Arms | High | 0.7x | 5% | Can disable weapon arm; reduces enemy effectiveness |
| Legs | High | 0.7x | 5% | Slows movement; can cause fall |
| Hands | Very High | 0.5x | 15% | Can disarm; forces weapon drop |

**Hit Calculation:**
```
Hit Chance = Base Accuracy + Skill Bonus - Target Movement - Distance Penalty - Fatigue Penalty
```

- **Base Accuracy**: 70% for all players
- **Skill Bonus**: +0.5% per combat skill level (max +50% at Grandmaster)
- **Target Movement**: Up to -40% for sprinting/dodging targets
- **Distance Penalty**: -5% per meter beyond optimal weapon range
- **Fatigue Penalty**: Up to -30% when exhausted

#### 2.1.2 Collision Detection
- **Server-authoritative**: All hit calculations run on server to prevent cheating
- **Hitbox precision**: Individual body part hitboxes (not single character collider)
- **Tick rate**: 60Hz simulation for smooth hit registration
- **Lag compensation**: 100ms rewind window for client-side prediction

### 2.2 Attack System

#### 2.2.1 Attack Types
| Type | Speed | Damage | Stamina Cost | Recovery | Use Case |
|------|-------|--------|--------------|----------|----------|
| Light Attack | 0.4s | 0.6x | 10 | 0.3s | Quick pressure, combo starter |
| Heavy Attack | 0.8s | 1.5x | 25 | 0.6s | High damage, guard break |
| Thrust | 0.5s | 1.0x | 15 | 0.4s | Armor penetration, reach |
| Slash | 0.6s | 1.1x | 18 | 0.5s | Wide arc, multiple targets |
| Overhead | 0.9s | 1.8x | 30 | 0.7s | Shield break, stun |
| Low Sweep | 0.7s | 0.8x | 20 | 0.5s | Leg targeting, knockdown |

#### 2.2.2 Combo System
- **No forced combos**: Players chain attacks freely based on timing and positioning
- **Flow bonuses**: Successful consecutive hits grant +5% damage per stack (max 3 stacks = +15%)
- **Combo breaking**: Blocked or dodged attacks reset flow bonus
- **Discovered techniques**: Advanced combo patterns learned through practice/mentorship

**Example Discovered Techniques:**
- *Windmill Strike*: Light → Light → Heavy (unlocks after 50 successful light-heavy transitions)
- *Punisher*: Block → Parry → Thrust (learned from veteran NPCs)
- *Executioner Flow*: Heavy → Overhead → Thrust (requires 80+ combat skill)

### 2.3 Defensive Mechanics

#### 2.3.1 Blocking
- **Active blocking**: Hold block button; stamina drains continuously
- **Block strength**: Reduces incoming damage by 60-90% based on shield quality
- **Stamina drain**: 5 stamina/sec while blocking; 15 stamina on heavy hit
- **Guard break**: When stamina reaches 0, player is stunned for 2 seconds
- **Directional blocking**: Must face attack direction; back/side attacks bypass block

#### 2.3.2 Dodging
- **Roll dodge**: 0.5s animation; i-frames during middle 0.2s
- **Stamina cost**: 20 stamina per dodge
- **Distance**: 2.5 meters in movement direction
- **Recovery**: 0.3s before next action
- **Mastery unlock**: At 60+ skill, gain "Quick Step" (0.3s dodge, 15 stamina)

#### 2.3.3 Parrying
- **Timing window**: 0.15s before impact (expands to 0.25s at Grandmaster)
- **Perfect parry**: Exact timing creates opening for guaranteed critical hit
- **Failed parry**: Partial block (30% damage reduction) but no counter opportunity
- **Weapon requirements**: Only certain weapons can parry (swords, daggers; not axes)

### 2.4 Stamina & Fatigue

#### 2.4.1 Stamina Pool
- **Base stamina**: 100 points
- **Regeneration**: 10 stamina/sec (out of combat); 5 stamina/sec (in combat)
- **Exhaustion**: Below 20 stamina causes -30% accuracy, -20% movement speed

#### 2.4.2 Action Costs
| Action | Stamina Cost |
|--------|--------------|
| Light Attack | 10 |
| Heavy Attack | 25 |
| Block (per sec) | 5 |
| Dodge | 20 |
| Parry Attempt | 15 |
| Sprint | 8/sec |
| Jump | 5 |

#### 2.4.3 Fatigue Accumulation
- Prolonged combat without rest builds fatigue
- **Fatigue stages**:
  - Fresh (0-20%): No penalty
  - Winded (21-50%): -10% stamina regen
  - Tired (51-75%): -20% accuracy, -15% stamina regen
  - Exhausted (76-100%): -30% accuracy, -30% movement, -50% stamina regen

---

## 3. Weapon System

### 3.1 Weapon Categories

| Category | Speed | Damage | Range | Weight | Special Properties |
|----------|-------|--------|-------|--------|-------------------|
| Dagger | Very Fast | Low | Short | Light | Backstab bonus, fast draw |
| Sword | Fast | Medium | Medium | Medium | Balanced, can parry |
| Longsword | Medium | High | Long | Heavy | Reach, guard break |
| Axe | Slow | Very High | Short | Heavy | Armor pierce, shield damage |
| Mace | Slow | High | Short | Heavy | Stun chance, armor pierce |
| Spear | Medium | Medium | Very Long | Medium | Reach, thrust bonus |
| Bow | Variable | Medium-High | Very Long | Light | Ranged, ammo dependent |
| Crossbow | Slow | Very High | Very Long | Heavy | Armor pierce, slow reload |
| Staff | Fast | Low-Medium | Long | Light | Blunt damage, spell channel |
| Unarmed | Very Fast | Very Low | Short | None | Grapple, disarm |

### 3.2 Weapon Handling

#### 3.2.1 Two-Handed vs One-Handed
- **One-handed**: Can use shield off-hand; faster attack speed (+10%)
- **Two-handed**: +30% damage, +20% range, cannot use shield
- **Dual-wielding**: Two light weapons; -15% accuracy per hand, +40% DPS potential

#### 3.2.2 Weapon Condition
- **Durability**: Weapons degrade with use (0.1% per hit)
- **Dull weapon**: Below 20% durability causes -20% damage
- **Broken weapon**: At 0% durability, weapon shatters (must repair/replace)
- **Repair**: Blacksmiths can restore durability; cost depends on damage

### 3.3 Weapon Mastery

Each weapon type has independent mastery tracking:
- **Novice** (0-20): Basic attacks only
- **Apprentice** (21-40): Unlock combo potential
- **Journeyman** (41-60): Reduced stamina costs (-15%)
- **Expert** (61-80): Advanced techniques unlocked
- **Master** (81-95): Signature moves available
- **Grandmaster** (96-100): Legendary techniques, +50% crit chance with weapon

**Mastery progression**: Invisible counter; increases through successful hits, kills, and training

---

## 4. Injury & Death System

### 4.1 Injury Mechanics

#### 4.1.1 Injury Types
| Injury | Cause | Effect | Healing Time |
|--------|-------|--------|--------------|
| Minor Cut | Light attacks | -5% accuracy (affected limb) | 2-5 days |
| Deep Wound | Heavy attacks | -20% limb function, bleed | 1-2 weeks |
| Broken Bone | Critical hits, falls | Limb unusable, severe pain | 3-6 weeks |
| Concussion | Head trauma | Blurred vision, confusion | 1-4 weeks |
| Internal Bleeding | Critical torso hits | Stamina drain, weakness | Requires surgery |
| Burn | Fire attacks | DoT, scarring | 1-3 weeks |

#### 4.1.2 Injury Effects
- Injuries persist after combat ends
- Severe injuries require medical attention (healers, hospitals)
- Untreated injuries can become infected (worsen over time)
- Scarring: Permanent cosmetic marks; some scars grant minor bonuses/penalties

### 4.2 Death & Consequences

#### 4.2.1 Death Triggers
- Health reaches 0
- Critical head/neck hit (instant kill regardless of health)
- Severe blood loss (bleedout timer: 60 seconds)
- Drowning, falling, environmental hazards

#### 4.2.2 Death Penalties
**On death:**
1. **Equipment loss**: Drop 3-5 random inventory items at death location
2. **Legacy mark**: Death recorded in world history; visible to others who investigate
3. **Reputation impact**: Witnesses spread news of your demise
4. **Respawn delay**: 10-30 minutes based on location and circumstances
5. **Skill regression**: -5 to -15 points in most-used combat skills (temporary; recoverable)

#### 4.2.3 Respawn Options
- **Nearest sanctuary**: Free respawn at closest safe zone (loses all carried items)
- **Body recovery**: Return to death location within 24 hours to reclaim items (risk of ambush)
- **Ransom**: Other players/NPCs can loot your body; items enter circulation

#### 4.2.4 Permanent Death (Optional Hardcore Mode)
- Servers may enable permadeath
- Character deleted on death
- Legacy continues through descendants (Legacy System)

---

## 5. Group Combat

### 5.1 Party Dynamics
- **Max party size**: 8 players
- **Friendly fire**: Optional (server setting); default ON for realism
- **Formation bonuses**: Coordinated positioning grants +10% defense

### 5.2 Group Tactics
- **Flanking**: Attacks from behind ignore 50% of armor
- **Surrounding**: 3+ attackers gain +20% hit chance
- **Shield wall**: Adjacent blockers share 30% of damage
- **Focus fire**: Call-target system for coordinated takedowns

### 5.3 Large-Scale Battles
- **Battleground zones**: Designated areas for 20v20+ conflicts
- **Morale system**: Units flee when morale breaks (based on casualties, leadership)
- **Commander role**: Designated leader provides buffs and tactical options

---

## 6. AI Opponent Behavior

### 6.1 AI Personalities
Each NPC has combat personality traits:

| Trait | Behavior Pattern |
|-------|------------------|
| Aggressive | Constant pressure, heavy attacks, risky plays |
| Defensive | Waits for openings, strong blocking, counter-focused |
| Tactical | Uses environment, targets weak points, retreats when wounded |
| Reckless | Ignores defense, wild swings, unpredictable |
| Cowardly | Flees when disadvantaged, calls for help |

### 6.2 AI Decision Tree
```
IF health < 20% THEN
  IF cowardly THEN flee
  ELSE desperate_mode (wild attacks)
ELSE IF stamina < 30% THEN
  defensive_stance (block, wait for regen)
ELSE IF opponent_opening THEN
  execute_attack(best_available)
ELSE IF opponent_attacking THEN
  IF can_parry THEN parry
  ELSE IF can_dodge THEN dodge
  ELSE block
ELSE
  circle_opponent(look_for_opening)
```

### 6.3 AI Learning (Advanced)
- AI adapts to player patterns over multiple encounters
- Veterans remember player tactics and adjust
- Defeating same NPC repeatedly makes them smarter against your style

---

## 7. Environmental Combat

### 7.1 Terrain Advantages
- **High ground**: +15% range, +10% damage on downhill attacks
- **Cover**: Behind objects grants 40% damage reduction from ranged
- **Chokepoints**: Narrow passages negate numerical advantage
- **Obstacles**: Can kite enemies around terrain features

### 7.2 Environmental Hazards
| Hazard | Effect | Counterplay |
|--------|--------|-------------|
| Fire | DoT, panic | Water, distance |
| Water | Slowed movement, electrical vulnerability | Swimming skill |
| Ice | Slip, reduced traction | Careful movement |
| Darkness | Reduced accuracy | Light source |
| Smoke | Obscured vision | Wind, masks |

### 7.3 Interactive Elements
- **Breakable objects**: Smash pots, barrels for improvised weapons
- **Traps**: Trigger environmental traps (falling rocks, spike pits)
- **Climbing**: Vertical escape routes and ambush positions

---

## 8. Progression & Discovery

### 8.1 Skill-Based Advancement
- **No XP grinding**: Improvement comes from actual combat experience
- **Invisible progression**: Players don't see exact skill numbers
- **Breakthrough moments**: Sudden unlocks after repeated practice
- **Mentorship**: Learning from skilled players/NPCs accelerates discovery

### 8.2 Technique Discovery
Players discover techniques through:
1. **Experimentation**: Trying different attack combinations
2. **Observation**: Watching skilled fighters
3. **Training**: Practicing with veterans
4. **Ancient texts**: Finding forgotten combat manuals
5. **Epiphanies**: Sudden understanding after extensive practice

### 8.3 Legendary Combat Styles
Rare techniques mastered by few:
- *Shadow Step*: Teleport behind enemy (requires 95+ skill, discovered in darkness)
- *Perfect Parry*: 0.3s parry window (learned from mythical swordmaster)
- *Thousand Cuts*: Rapid light attack flurry (found in ancient assassin guild)
- *Unbreakable Will*: Immune to fear/morale breaks (earned through surviving impossible odds)

---

## 9. UI & Feedback

### 9.1 Minimal HUD
- **Health bar**: Only visible when damaged or in combat
- **Stamina ring**: Subtle indicator around character
- **No crosshair**: Aiming is manual (mouse/controller direction)
- **No damage numbers**: Visual/audio feedback only

### 9.2 Visual Feedback
- **Hit effects**: Blood splatter, sparks on armor, weapon impacts
- **Screen shake**: On heavy hits
- **Blur/distortion**: When injured or exhausted
- **Weapon trails**: Show attack arcs

### 9.3 Audio Feedback
- **Weapon sounds**: Distinct clangs for metal, thuds for flesh
- **Character vocalizations**: Grunts, screams, breathing
- **Environmental audio**: Footsteps vary by terrain

---

## 10. Balance Considerations

### 10.1 Rock-Paper-Scissors Dynamics
- **Heavy weapons** beat shields but lose to fast weapons
- **Fast weapons** beat heavy weapons but lose to reach
- **Long weapons** beat fast weapons but lose in close quarters
- **Shields** beat arrows/thrusts but vulnerable to blunt/heavy

### 10.2 Anti-Turtling Measures
- Prevent excessive defensive play:
  - Block stamina drain increases over time
  - Surrounding bonuses punish static defense
  - Stamina regeneration penalizes passive play

### 10.3 New Player Protection
- **Sanctuary zones**: No PvP in starter areas
- **Skill-matched matchmaking**: Optional arena pairing
- **Veteran mentors**: Experienced players can guide newcomers

---

## 11. Technical Requirements

### 11.1 Network Architecture
- **Server tick rate**: 60Hz minimum
- **Client prediction**: For smooth local combat feel
- **Lag compensation**: 100ms rewind for hit registration
- **Bandwidth**: ~15 KB/sec per player in combat

### 11.2 Performance Targets
- **Frame rate**: 60 FPS minimum (144 FPS ideal)
- **Hit registration latency**: <50ms server response
- **Animation canceling**: Frame-perfect input recognition

### 11.3 Anti-Cheat Measures
- Server-authoritative hit calculation
- Speed hack detection (impossible attack rates)
- Aimbot detection (unnatural accuracy patterns)
- Memory integrity checks

---

## 12. Dependencies

### 12.1 Required Systems
- **Skills Progression System**: Combat skill tracking and mastery
- **Inventory System**: Weapon equipment and durability
- **Injury System**: Wound management and healing
- **NPC System**: AI opponent behavior
- **Network System**: Multiplayer synchronization
- **Physics System**: Collision detection and ragdoll

### 12.2 Related Systems
- **Economy System**: Weapon trading and repair costs
- **Reputation System**: Combat fame and infamy
- **Legacy System**: Death recording and inheritance
- **Crafting System**: Weapon creation and modification

---

## 13. Open Questions

1. Should there be weapon class restrictions based on strength/attributes?
2. How to handle mounted combat (horseback fighting)?
3. Should poisons and enchantments be part of base combat or separate system?
4. What is the maximum recommended group size for balanced PvP?
5. Should there be ranked/unranked combat modes?

---

## 14. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-XX | AI Architect | Initial draft using design-system methodology |

---

## Appendix A: Combat Scenario Examples

### A.1 Duel Scenario
*Two players meet in an arena:*
- Player A (longsword, shield) vs Player B (dual daggers)
- Player A uses reach advantage, keeps distance
- Player B dodges inside, targets arms to disable shield
- Stamina management decides winner as fight extends past 2 minutes

### A.2 Ambush Scenario
*Player traveling forest road:*
- 3 bandit NPCs attack from concealment
- Player must quickly assess threat, choose fight or flight
- Killing bandits yields loot but attracts attention
- Fleeing preserves health but loses supplies

### A.3 Group Battle Scenario
*8v8 faction conflict:*
- Coordinated shield wall advances
- Archers provide covering fire
- Flanking team attempts rear assault
- Commander coordinates focus-fire targets
- Morale breaks when 50% casualties reached
