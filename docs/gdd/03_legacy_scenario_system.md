# Legacy Scenario System

## Overview
Legacy Scenarios are the heart of the living world experience. Unlike traditional quests with markers and explicit objectives, Legacy Scenarios are hidden, conditional events triggered by invisible world memory tracking player actions over time.

## Core Philosophy
- **No Quest Markers**: Players discover these through exploration, rumors, and experimentation
- **Invisible Triggers**: The game tracks actions without displaying progress bars
- **Emergent Storytelling**: Each player's journey creates unique narrative moments
- **World Memory**: The world remembers and responds to player behavior patterns

## System Architecture

### Invisible Counters
The system tracks hundreds of hidden metrics including:
- Creatures killed vs. spared
- NPCs helped or harmed
- Secrets discovered
- Languages learned
- Locations explored
- Items crafted or fused
- Weather events experienced
- Time spent in different activities
- Choices made in moral dilemmas
- Patterns of behavior (violent, peaceful, curious, greedy)

### Condition Checking
Scenarios trigger based on complex combinations:
```
IF (corrupted_rabbits_defeated > 70 AND corrupted_rabbits_defeated < 120)
AND (innocent_rabbits_killed == 0)
AND (rabbit_dens_saved >= 3)
AND (current_season == "spring")
AND (has_spoken_to NPC:old_herbalist)
AND (carries_item:ancient_relic)
THEN trigger_scenario: white_rabbit_encounter
```

### Trigger Types
1. **Behavioral Triggers**: Based on accumulated player actions
2. **Temporal Triggers**: Specific times, seasons, or celestial events
3. **Location Triggers**: Being in specific places under certain conditions
4. **Relationship Triggers**: NPC relationship thresholds reached
5. **Knowledge Triggers**: Learning specific information or languages
6. **Item Triggers**: Possessing or using particular objects
7. **World State Triggers**: Global events or conditions met

## Scenario Categories

### Tier 1: Personal Legacy
Affects only the individual player's experience:
- Unique NPC relationships
- Personal skill unlocks
- Hidden area access
- Custom dialogue options
- Individual story branches

### Tier 2: Local Impact
Changes affect a region or settlement:
- Trade route openings/closures
- NPC population changes
- Building construction/destruction
- Local faction reputation shifts
- Regional event availability

### Tier 3: World-Changing
Rare scenarios that alter the shared world:
- Ancient Entity awakenings
- Civilization discoveries
- Permanent geography changes
- New faction formations
- Historical event recordings

## Example Scenarios

### The Wandering Blacksmith
**Triggers:**
- Crafted 50+ items
- Discovered 10+ rare materials
- Helped 3+ villages with resource shortages
- Current reputation with crafters > 75

**Outcome:**
Legendary blacksmith appears for one in-game day, offering:
- Unique crafting techniques
- Legendary weapon blueprints
- Equipment repair services
- Rare material sources

### Blood Moon Event
**Triggers:**
- Nightborn players active in region
- Moon phase: Full
- Time: Midnight
- Recent vampire activity in area

**Outcome:**
- Nightborn gain significant power boost
- New monster spawns appear
- Hidden caves open
- Special boss awakens
- Rare resources spawn

### The Lost Expedition
**Triggers:**
- Explored 5+ ancient ruins
- Translated 3+ ancient texts
- Has survival skill > 50
- Random chance (10%) when entering deep wilderness

**Outcomes (based on player choice):**
- **Rescue**: Unlock new trade route, gain expedition members as allies
- **Ignore**: Expedition lost forever, trade route never opens
- **Follow**: Discover ancient city, gain unique knowledge

### The Rabbit Sanctuary
**Triggers:**
- Defeated 70-120 corrupted rabbits
- Never killed innocent rabbits
- Saved 3+ rabbit dens
- Spring season
- Spoken to old herbalist NPC
- Carrying ancient relic

**Outcome:**
White rabbit appears, leads player to underground sanctuary where:
- Ancient rabbits share forgotten history
- Player learns rabbit language
- Gain ability to calm corrupted rabbits
- Access to hidden tunnel network
- Optional rabbit companion
- Unique title: "Friend of the Warren"

## Reward Philosophy

Legacy Scenarios prioritize meaningful rewards over raw power:

### Knowledge Rewards
- Maps to forgotten locations
- Ancient language translations
- Boss strategy insights
- Crafting technique discoveries
- Historical revelations

### Access Rewards
- Entry to hidden cities
- Secret dungeon entrances
- Restricted faction areas
- Ancient library permissions
- Underground passage networks

### Skill Rewards
- Unique abilities unavailable elsewhere
- Advanced technique unlocks
- Hidden profession skills
- Magical affinities
- Combat maneuvers

### Relationship Rewards
- NPC allies and companions
- Faction reputation boosts
- Marriage/family opportunities
- Mentor relationships
- Servant or follower recruitment

### Cosmetic Rewards
- Unique titles recorded in world history
- Distinctive clothing or armor appearances
- Special mounts or pets
- Architectural customization options
- Statue or monument placements

### Historical Rewards
- Names recorded in world libraries
- Statues built in player's honor
- Songs or stories created about player
- Chronicle entries written
- Legacy effects for future player generations

### Equipment Rewards
- Occasionally, legendary weapons or artifacts
- Items with unique histories
- Gear with special properties
- Heirloom items passed through generations

## Implementation Guidelines

### Design Principles
1. **Never Obvious**: Triggers should not be easily deducible
2. **Multiple Paths**: Same scenario accessible through different action combinations
3. **Meaningful Choices**: Player decisions genuinely affect outcomes
4. **Delayed Gratification**: Rewards may come weeks after triggering actions
5. **Community Mystery**: Encourage player discussion and theory-crafting

### Technical Considerations
- Store counter data efficiently (incremental updates)
- Use event-driven architecture for trigger checking
- Implement server-side validation to prevent exploitation
- Design for scalability (thousands of simultaneous players)
- Create tools for designers to configure scenarios without code changes

### Balance Concerns
- Avoid making triggers too obscure (players should feel rewarded for natural play)
- Ensure solo and group players can both access scenarios
- Prevent griefing or exploitation of trigger conditions
- Maintain fairness across time zones and play schedules
- Consider new player catch-up mechanisms

## Community Integration

### Discovery Sharing
- Players naturally share theories on forums/Discord
- Content creators document unusual encounters
- Community wikis compile known triggers
- Social media spreads stories of rare events

### Developer Support
- Release subtle hints through official channels
- Host community events around major discoveries
- Acknowledge player theories and findings
- Update scenarios based on community feedback

## Future Expansion

### Scenario Types to Add
- Seasonal festivals with unique triggers
- Inter-player legacy scenarios (group achievements)
- Generational scenarios (affecting player's descendants)
- Cross-continent epic storylines
- Player-initiated world events

### Advanced Features
- AI-driven scenario generation based on player patterns
- Dynamic difficulty adjustment within scenarios
- Multi-stage legacy chains (one scenario leads to another)
- Player-created scenario suggestions
- Community-voted scenario implementations

## Success Metrics

A Legacy Scenario system is successful when:
- Players regularly share "You won't believe what happened" stories
- Community forums buzz with theories about hidden triggers
- Content creators make videos analyzing scenario patterns
- Players feel their unique playstyle is recognized and rewarded
- The world feels responsive and alive rather than scripted
- New players feel wonder discovering what veterans take for granted
