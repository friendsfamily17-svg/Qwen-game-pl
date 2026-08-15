# Crafting & Professions System

## 1. Overview

### 1.1 Purpose
The crafting system delivers a deep, physical crafting experience where players master trades through hands-on practice rather than menu interactions. Every crafted item bears the mark of its creator, and true mastery unlocks legendary techniques passed down through generations.

### 1.2 Design Pillars Alignment
- **Knowledge > Gold**: Crafting recipes are discovered and earned, not bought; master craftsmen guard their secrets
- **World Remembers**: Crafted items carry creator signatures; reputation spreads through quality work
- **Discovery Drives Design**: Players uncover advanced techniques through experimentation and mentorship
- **Permanent Consequences**: Failed crafts waste materials; poor quality damages reputation

### 1.3 Scope
This document covers:
- Physical crafting mechanics (hammer-and-anvil style)
- Profession categories and specializations
- Quality tiers and mastery progression
- Resource gathering and processing
- Tool systems and durability
- Recipe discovery and learning
- Economic integration

---

## 2. Core Crafting Mechanics

### 2.1 Physical Crafting System

#### 2.1.1 Active Crafting Process
Crafting is a real-time mini-game, not a menu selection:

**Forging Example:**
1. Heat metal in forge to correct temperature
2. Place on anvil, select hammer strike type
3. Time strikes to rhythm (timing affects grain structure)
4. Rotate piece, repeat for each section
5. Quench at optimal moment
6. Polish and finish

**Success Factors:**
- **Temperature control**: Too hot = brittle, too cold = cracks
- **Strike timing**: Rhythm affects material integrity
- **Strike force**: Light taps vs heavy blows for different effects
- **Sequence order**: Wrong order causes structural weakness

#### 2.1.2 Crafting Actions by Profession

| Profession | Primary Actions | Skill Checks | Tools Required |
|------------|----------------|--------------|----------------|
| Blacksmith | Hammer, Heat, Quench, Grind | Temperature, Timing, Force | Forge, Anvil, Hammers |
| Carpenter | Cut, Shape, Join, Sand | Angle precision, Pressure | Saw, Chisel, Plane |
| Tailor | Cut, Stitch, Hem, Embroider | Thread tension, Pattern alignment | Scissors, Needle, Loom |
| Alchemist | Mix, Heat, Cool, Distill | Proportions, Timing, Temperature | Cauldron, Alembic, Scales |
| Cook | Chop, Mix, Heat, Season | Timing, Temperature, Balance | Knife, Pot, Spices |
| Mason | Cut, Shape, Fit, Polish | Angle, Pressure, Alignment | Chisel, Hammer, Square |
| Leatherworker | Cut, Punch, Stitch, Dye | Precision, Tension, Pattern | Knife, Awl, Needle |
| Jeweler | Cut, Set, Polish, Engrave | Precision, Angle, Pressure | Loupe, Files, Setting tools |

### 2.2 Quality System

#### 2.2.1 Quality Tiers
| Tier | Name | Multiplier | Requirements |
|------|------|------------|--------------|
| 1 | Broken | 0.3x | Critical failure |
| 2 | Poor | 0.5x | Multiple mistakes |
| 3 | Common | 0.8x | Basic competence |
| 4 | Fine | 1.0x | Good execution |
| 5 | Excellent | 1.3x | Skilled craftsmanship |
| 6 | Masterwork | 1.7x | Master-level skill |
| 7 | Legendary | 2.5x | Legendary technique + perfect execution |
| 8 | Artifact | 5.0x+ | Unique creation, world-first |

#### 2.2.2 Quality Determinants
```
Final Quality = Base Quality + Skill Bonus + Tool Bonus + Material Bonus - Mistake Penalty
```

- **Base Quality**: Random factor (0.6-1.0)
- **Skill Bonus**: +0.02 per profession level (max +2.0)
- **Tool Bonus**: Quality tools add +0.1 to +0.5
- **Material Bonus**: Premium materials add +0.1 to +0.3
- **Mistake Penalty**: -0.1 to -0.5 per error

#### 2.2.3 Quality Inspection
- Buyers can inspect crafted items before purchase
- Quality visible through visual inspection (not numerical UI)
- Master craftsmen can identify maker by style marks
- Poor quality items damage crafter reputation

### 2.3 Failure System

#### 2.3.1 Failure Types
| Failure | Cause | Consequence | Recovery |
|---------|-------|-------------|----------|
| Critical Fail | Major mistake | Item destroyed, materials lost | Start over |
| Poor Quality | Multiple errors | Item usable but low value | Sell cheap, recycle |
| Flawed | Single error | Minor stat reduction | Use personally |
| Near Perfect | Tiny mistake | Almost maximum quality | Accept or recycle |

#### 2.3.2 Learning from Failure
- Each failure provides hidden progress toward mastery
- Repeated failures with same recipe unlock "lesson learned" bonus
- Masters can analyze failed items to understand mistakes

---

## 3. Profession System

### 3.1 Profession Categories

#### 3.1.1 Gathering Professions
| Profession | Resources | Tools | Notes |
|------------|-----------|-------|-------|
| Miner | Ores, gems, stone | Pickaxe, shovel | Underground work |
| Lumberjack | Wood, bark, sap | Axe, saw | Forest work |
| Farmer | Crops, fibers | Hoe, sickle | Seasonal cycles |
| Hunter | Meat, hides, bones | Bow, knife | Tracking skill |
| Fisher | Fish, pearls, shells | Net, rod | Water knowledge |
| Herbalist | Plants, flowers, roots | Knife, basket | Plant identification |

#### 3.1.2 Crafting Professions
| Profession | Products | Specializations | Entry Barrier |
|------------|----------|-----------------|---------------|
| Blacksmith | Weapons, armor, tools | Bladesmith, Armorsmith, Toolsmith | High (forge required) |
| Carpenter | Furniture, bows, buildings | Furniture, Bowyer, Architect | Medium (tools required) |
| Tailor | Clothing, bags, sails | Clothier, Bagmaker, Sailmaker | Low (needle/thread) |
| Alchemist | Potions, poisons, explosives | Pharmacist, Toxicologist, Bomber | High (lab required) |
| Cook | Food, preserves, feasts | Baker, Chef, Preserver | Low (fire+pot) |
| Mason | Buildings, statues, roads | Builder, Sculptor, Paver | Medium (tools required) |
| Leatherworker | Armor, bags, boots | Armorer, Bagmaker, Cobbler | Medium (materials) |
| Jeweler | Jewelry, enchanted items | Gemcutter, Goldsmith, Enchanter | Very High (tools+materials) |

#### 3.1.3 Service Professions
| Profession | Services | Skills Required |
|------------|----------|-----------------|
| Merchant | Trading, appraisal | Negotiation, Market knowledge |
| Healer | Medical treatment | Anatomy, Herbology |
| Teacher | Skill training | Mastery in subject, Patience |
| Entertainer | Performances | Music, Acting, Juggling |
| Guard | Protection services | Combat skills, Vigilance |

### 3.2 Multi-Profession Rules

- **Max active professions**: 3 gathering + 3 crafting + 2 service
- **Mastery focus**: Only one profession can reach Legendary tier
- **Cross-profession bonuses**: Related professions grant synergy bonuses
  - Miner + Blacksmith: +10% ore yield, +5% metal quality
  - Lumberjack + Carpenter: +10% wood quality, +5% crafting speed
  - Hunter + Leatherworker: +15% hide quality

---

## 4. Mastery Progression

### 4.1 Skill Tiers

| Tier | Range | Title | Capabilities |
|------|-------|-------|--------------|
| 1 | 0-20 | Novice | Basic recipes, simple items |
| 2 | 21-40 | Apprentice | Intermediate recipes, better quality |
| 3 | 41-60 | Journeyman | Advanced recipes, consistent quality |
| 4 | 61-80 | Expert | Complex items, teaching ability |
| 5 | 81-95 | Master | Rare recipes, legendary techniques |
| 6 | 96-100 | Grandmaster | Unique creations, world-renowned |

### 4.2 Invisible Progression

- Players don't see exact skill numbers
- Progress tracked through:
  - Items crafted (quantity and quality)
  - Recipes mastered
  - Techniques discovered
  - Reputation earned
  - Students taught

### 4.3 Breakthrough Moments

At certain thresholds, players experience epiphanies:

**Journeyman Breakthrough (60 skill):**
- Unlock "Craftsman's Eye": Can visually assess quality before completion
- Gain ability to teach apprentices

**Master Breakthrough (85 skill):**
- Unlock "Muscle Memory": -20% time on familiar recipes
- Can develop custom variations

**Grandmaster Breakthrough (98 skill):**
- Unlock "Legendary Technique": Unique method known only to them
- Can create one-of-a-kind artifacts
- Reputation spreads across continents

### 4.4 Technique Discovery

Players discover techniques through:
1. **Repetition**: Crafting same item 50+ times reveals optimizations
2. **Experimentation**: Trying unusual combinations
3. **Observation**: Watching masters work
4. **Mentorship**: Being taught by higher-skill crafters
5. **Ancient texts**: Finding forgotten manuals
6. **Divine inspiration**: Random epiphany after extensive practice

**Example Discovered Techniques:**
- *Damascus Folding*: Blacksmith technique creating pattern-welded steel (requires 80+ skill, discovered through repetition)
- *Ghost Stitch*: Tailor technique for nearly invisible seams (taught by master tailor NPCs)
- *Dragon's Breath*: Alchemist technique for ultra-potent fire potions (found in ancient laboratory notes)

---

## 5. Tool System

### 5.1 Tool Categories

| Category | Examples | Impact | Durability |
|----------|----------|--------|------------|
| Basic | Iron hammer, wooden saw | No bonus | 100 uses |
| Fine | Steel hammer, iron saw | +5% quality | 500 uses |
| Masterwork | Damascus hammer, tempered saw | +15% quality | 2000 uses |
| Legendary | Named artisan tools | +30% quality, unique effects | Unlimited |

### 5.2 Tool Maintenance

- **Degradation**: Tools lose effectiveness with use
- **Sharpening**: Cutting tools require regular sharpening
- **Repair**: Damaged tools can be fixed by appropriate profession
- **Replacement**: Broken tools must be replaced

### 5.3 Tool Specialization

- Tools can be attuned to specific tasks
- **Example**: A sword-making hammer grants +10% to swords but 0% to armor
- Specialized tools encourage crafters to focus on niches

---

## 6. Resource System

### 6.1 Resource Quality Tiers

| Tier | Name | Examples | Quality Bonus |
|------|------|----------|---------------|
| 1 | Scrap | Rusty iron, rotten wood | -30% |
| 2 | Common | Standard iron, oak | 0% |
| 3 | Fine | Refined steel, maple | +10% |
| 4 | Premium | Damascus steel, ebony | +25% |
| 5 | Rare | Mithril, dragonbone | +50% |
| 6 | Legendary | Adamantite, phoenix feather | +100% |

### 6.2 Resource Processing

Raw resources often require processing before use:

**Ore Processing:**
1. Mine raw ore
2. Smelt into ingots (blacksmithing)
3. Refine for purity (optional, improves quality)
4. Alloy creation (mixing metals for special properties)

**Wood Processing:**
1. Fell tree (lumberjack)
2. Cut into planks (carpentry)
3. Season/dry (time requirement)
4. Treat/finish (optional protection)

### 6.3 Resource Scarcity

- High-quality resources are geographically limited
- Some resources only available in dangerous areas
- Over-harvesting depletes local nodes (regenerates slowly)
- Sustainable harvesting yields long-term benefits

---

## 7. Recipe System

### 7.1 Recipe Acquisition

| Method | Description | Rarity |
|--------|-------------|--------|
| Basic Training | Starting recipes | Common |
| Experimentation | Discover through trial/error | Variable |
| Mentor Teaching | Learned from masters | Uncommon |
| Recipe Books | Found or purchased | Rare |
| Ancient Texts | Forgotten knowledge | Very Rare |
| Divine Inspiration | Unique discovery | Legendary |

### 7.2 Recipe Complexity

Recipes have hidden complexity ratings:

| Complexity | Skill Required | Steps | Time | Failure Rate |
|------------|---------------|-------|------|--------------|
| Simple | 0-20 | 2-3 | 1-2 min | 10% |
| Moderate | 21-40 | 4-6 | 3-5 min | 25% |
| Complex | 41-60 | 7-10 | 6-10 min | 40% |
| Expert | 61-80 | 11-15 | 11-20 min | 55% |
| Master | 81-95 | 16-20 | 21-40 min | 70% |
| Legendary | 96-100 | 20+ | 40+ min | 85% |

### 7.3 Recipe Variations

- Masters can modify existing recipes
- **Ingredient substitution**: Replace with equivalent materials
- **Process alteration**: Change steps for different outcomes
- **Custom creations**: Combine knowledge for entirely new items

---

## 8. Economic Integration

### 8.1 Pricing Mechanics

```
Base Price = Material Cost + (Time × Hourly Rate) + Quality Multiplier + Reputation Premium
```

- **Material Cost**: Sum of resource values
- **Hourly Rate**: Based on profession skill level
- **Quality Multiplier**: 0.5x (poor) to 5.0x (artifact)
- **Reputation Premium**: Famous crafters charge more

### 8.2 Commission System

- Players can accept commissioned work
- Contracts specify: item, quality tier, deadline, payment
- Failure to deliver damages reputation
- Successful commissions build client relationships

### 8.3 Shop Ownership

- Master crafters can open permanent shops
- Hire NPC assistants or player apprentices
- Build customer base through consistent quality
- Shop reputation persists even when owner offline

---

## 9. Social Aspects

### 9.1 Apprenticeship System

- Masters can take on apprentices (players or NPCs)
- **Teaching process**: Demonstrate → Guide → Observe → Evaluate
- **Apprentice benefits**: Faster learning, access to master's recipes
- **Master benefits**: Assistance with large projects, legacy building
- **Contract terms**: Fixed duration or project-based

### 9.2 Guilds

- Crafters can form or join guilds
- **Guild benefits**: Shared resources, bulk buying, knowledge library
- **Guild halls**: Central locations for collaboration
- **Guild reputation**: Collective standing affects all members

### 9.3 Competitions

- Crafting contests held at festivals
- **Categories**: Best weapon, finest clothing, most creative design
- **Judging**: By panel of masters or public vote
- **Prizes**: Rare materials, reputation, exclusive recipes

---

## 10. UI & Feedback

### 10.1 Minimal HUD

- **No crafting bars**: Players judge progress by sight/sound
- **Temperature indicators**: Visual (glow color) not numerical
- **Quality sense**: Developed through experience, not displayed

### 10.2 Sensory Feedback

**Visual:**
- Metal color changes with temperature
- Wood grain reveals cut quality
- Stitch evenness visible on close inspection

**Audio:**
- Hammer ring indicates strike quality
- Saw sound reveals blade sharpness
- Sizzle tells quench timing

**Tactile (controller rumble):**
- Resistance when cutting
- Impact feedback on strikes
- Vibration on mistakes

### 10.3 Journal System

- Players maintain crafting journals
- Records recipes discovered
- Notes on techniques learned
- Personal observations and tips

---

## 11. Technical Requirements

### 11.1 Physics Simulation

- Real-time collision for hammer strikes
- Material deformation visualization
- Particle effects for sparks, dust, shavings

### 11.2 Persistence

- Crafted items persist indefinitely
- Creator signature embedded in item data
- Quality calculations server-authoritative

### 11.3 Performance

- Crafting instances support multiple viewers
- Complex animations stream efficiently
- Large-scale production (guild workshops) optimized

---

## 12. Dependencies

### 12.1 Required Systems

- **Skills Progression**: Profession skill tracking
- **Inventory**: Resource and item management
- **Economy**: Pricing, trading, commissions
- **Reputation**: Crafter fame system
- **Physics**: Collision and deformation

### 12.2 Related Systems

- **Gathering**: Resource acquisition
- **Combat**: Weapon/armor crafting integration
- **Magic**: Enchanting and magical crafting
- **Housing**: Workshop placement and upgrades

---

## 13. Open Questions

1. Should crafting fail states be more punishing in hardcore mode?
2. How to handle mass production vs artisanal crafting balance?
3. Should there be crafting-specific attributes (strength, dexterity)?
4. What limits should exist on recipe sharing between players?
5. How to prevent crafting inflation in long-term economies?

---

## 14. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-XX | AI Architect | Initial draft using design-system methodology |

---

## Appendix A: Crafting Scenario Examples

### A.1 Master Swordsmith Scenario
*Veteran blacksmith creates legendary blade:*
- Spends days preparing materials (smelting rare ore)
- Maintains precise forge temperature for 6 hours
- Delivers 200+ perfectly-timed hammer strikes
- Quenches in special oil at exact moment
- Result: Legendary sword with unique pattern, signed by maker
- Reputation spreads, buyers travel from distant lands

### A.2 Apprentice Learning Scenario
*New player learns tailoring:*
- Starts with basic stitches on scrap cloth
- Makes many mistakes (uneven seams, broken needles)
- Gradually improves through repetition
- After 50 garments, experiences breakthrough
- Can now see stitch quality before finishing
- Takes on first commission (simple tunic)

### A.3 Guild Collaboration Scenario
*Cathedral construction project:*
- Master architect designs structure
- Masons cut and fit stone blocks
- Carvers create decorative elements
- Carpenters build scaffolding and roof
- Stained glass made by specialist glaziers
- Project takes months, involves 20+ crafters
- Completed cathedral becomes world landmark
