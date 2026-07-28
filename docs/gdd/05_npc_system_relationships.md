# NPC System & Relationships

## Overview
NPCs (Non-Player Characters) are autonomous individuals with complex lives, memories, and relationships. They are not static quest givers but living beings who remember player actions, evolve over time, and contribute to the world's dynamic nature.

## Core Philosophy
- **Autonomous Existence**: NPCs live independent lives regardless of player presence
- **Permanent Memory**: Every interaction is remembered and influences future behavior
- **Generational Continuity**: NPCs age, die, and pass legacies to successors
- **Nuanced Relationships**: No binary good/evil, only complex individual responses

## NPC Architecture

### Basic Attributes
Every NPC possesses:
- **Name**: Unique identifier, often culturally significant
- **Age**: Affects capabilities, knowledge, and lifespan
- **Personality**: Trait combinations influencing behavior
- **Profession**: Primary occupation and skill set
- **Home**: Personal residence with daily routines
- **Relationships**: Network of connections to other NPCs
- **Memories**: Database of all player interactions
- **Schedule**: Daily/weekly activity patterns
- **Ambitions**: Long-term goals and desires
- **Fears**: Phobias and avoidance behaviors
- **Loyalties**: Faction allegiances and personal bonds
- **Reputation**: How others perceive this NPC

### Personality Traits
Personality is composed of multiple spectrums:

**Trust vs. Skepticism**
- High trust: Quickly believes players, shares information freely
- High skepticism: Questions motives, verifies claims independently

**Generosity vs. Greed**
- Generous: Gives freely, offers discounts, helps without payment
- Greedy: Demands payment, hoards resources, suspicious of gifts

**Bravery vs. Cowardice**
- Brave: Stands ground in danger, defends others
- Cowardly: Flees threats, hides during conflicts

**Kindness vs. Cruelty**
- Kind: Helps strangers, comforts distressed individuals
- Cruel: Takes pleasure in others' misfortune, harsh treatment

**Curiosity vs. Conservatism**
- Curious: Asks questions, explores new ideas, welcomes change
- Conservative: Prefers tradition, suspicious of innovation

**Honor vs. Pragmatism**
- Honorable: Keeps promises, follows moral code
- Pragmatic: Does what works, flexible with principles

### Memory System

#### Memory Categories
NPCs remember different types of interactions:

**Direct Interactions**
- Conversations held with player
- Transactions completed
- Quests given or received
- Gifts exchanged
- Combat encounters (ally or enemy)
- Physical proximity over time

**Observed Actions**
- Crimes witnessed
- Heroic deeds seen
- Reputation-defining moments
- Public speeches or performances
- Battle outcomes observed

**Heard Rumors**
- Stories told by other NPCs
- Player reputation spreading
- Exaggerated tales growing over time
- Misinformation believed as truth

#### Memory Persistence
- **Short-term**: Recent interactions (hours/days)
- **Long-term**: Significant events (months/years)
- **Permanent**: Life-changing moments (never forgotten)
- **Inherited**: Memories passed to family members after death

#### Memory Effects
Memories influence:
- Dialogue options available
- Prices offered in trade
- Quest availability and rewards
- Willingness to help or hinder
- Emotional reactions during encounters
- Recommendations to other NPCs
- Romantic interest potential
- Trust levels for sensitive information

## Daily Schedules

### Routine Structure
NPCs follow realistic daily patterns:

**Morning (6:00 - 12:00)**
- Wake up and morning routines
- Breakfast at home or tavern
- Travel to workplace
- Begin daily labor

**Afternoon (12:00 - 18:00)**
- Continue work activities
- Lunch break (varies by profession)
- Social interactions with colleagues
- Errands and shopping

**Evening (18:00 - 22:00)**
- Return home or visit tavern
- Dinner with family or friends
- Leisure activities
- Community gatherings

**Night (22:00 - 6:00)**
- Sleep (most NPCs)
- Night shift workers active
- Criminals operate in shadows
- Emergency situations disrupt routine

### Schedule Variations
- **Weekdays vs. Weekends**: Different routines on rest days
- **Seasonal Changes**: Work varies by season (farming, fishing)
- **Weather Impact**: Rain/snow alters outdoor activities
- **Festival Days**: Special schedules during celebrations
- **Emergency States**: War, disaster, or crisis changes everything
- **Life Events**: Marriage, birth, death, illness disrupt routines

### Finding NPCs
Players must learn schedules to meet specific NPCs:
- No permanent stationary positions
- May need to wait for right time/place
- Can follow NPCs to discover locations
- Asking locals reveals schedule information
- Some NPCs only available at specific times

## Relationship System

### Relationship Types
NPCs can develop various relationships with players:

**Stranger** → **Acquaintance** → **Friend** → **Close Friend** → **Best Friend**
- Progression through positive interactions
- Unlocks deeper dialogue and quests
- Increases trust and assistance willingness

**Neutral** → **Suspicious** → **Hostile** → **Enemy** → **Archenemy**
- Degradation through negative actions
- Leads to refusal of service or attacks
- May trigger revenge scenarios

**Professional**: Business partnerships, mentor/apprentice
**Romantic**: Dating, engagement, marriage, family
**Familial**: Adoption into NPC families, inheritance rights
**Political**: Alliance members, rivals, subordinates, superiors

### Building Relationships

#### Positive Actions
- Regular friendly conversations
- Completing quests for them
- Giving meaningful gifts
- Defending them from threats
- Helping achieve their ambitions
- Remembering important dates (birthdays, anniversaries)
- Keeping their secrets
- Introducing them to useful contacts
- Supporting their business/profession

#### Negative Actions
- Insulting or threatening
- Stealing from them or their associates
- Harming their friends/family
- Breaking promises
- Spreading rumors about them
- Competing for same objectives
- Disrespecting their values/beliefs
- Ignoring their requests for help

### Relationship Milestones
Significant relationship stages trigger events:

**Friendship Milestones**
- Invited to their home
- Introduced to family members
- Trusted with valuable items
- Asked for personal favors
- Included in private gatherings

**Romance Milestones**
- First date invitation
- Gift of romantic significance
- Confession of feelings
- Engagement proposal
- Wedding ceremony
- Starting a family together

**Professional Milestones**
- Offered apprenticeship
- Made business partner
- Given access to restricted areas
- Taught secret techniques
- Named as successor

## Succession System

### Natural Lifecycle
NPCs age and eventually die:

**Life Stages**
- **Child** (0-12): Learning, playing, minor tasks
- **Teenager** (13-17): Apprenticeships, coming of age
- **Young Adult** (18-35): Peak productivity, starting families
- **Adult** (36-55): Established careers, community leaders
- **Elder** (56-75): Retirement, advising, grandparenting
- **Ancient** (76+): Rare, revered, passing on wisdom

### Death Conditions
NPCs can die from:
- **Old Age**: Natural death after full lifespan
- **Player Actions**: Killed directly or indirectly
- **Monster Attacks**: During raids or wandering encounters
- **Disease**: Plagues and illnesses spread through populations
- **Accidents**: Falls, fires, drowning, etc.
- **War**: Combat casualties during conflicts
- **Execution**: Punishment for crimes
- **Mysterious Disappearance**: Plot-related vanishings

### Succession Mechanics
When important NPCs die:

**Family Succession**
- Children inherit professions
- Spouses take over businesses
- Extended family fills gaps
- Family dynamics shift after loss

**Apprentice Succession**
- Trained replacements take roles
- Quality may differ from predecessor
- New perspectives brought to profession
- Apprentice's personality affects business

**Community Selection**
- Town chooses new leader
- Guild elects new master
- Customers adopt new merchant
- Gradual acceptance period

### Inheritance Systems
Successors inherit:
- **Physical Assets**: Buildings, inventory, equipment
- **Knowledge**: Recipes, techniques, secrets (partial)
- **Relationships**: Modified versions of parent's connections
- **Reputation**: Family name carries weight (positive/negative)
- **Unfinished Business**: Quests, debts, promises
- **Memories**: Stories told about predecessor

### Grief and Mourning
Communities react to deaths:
- Funeral ceremonies held
- Period of mourning observed
- Memorials constructed (statues, plaques)
- Stories shared about deceased
- Temporary business closures
- Emotional dialogue changes
- Possible revenge quests if murdered

## Mark System

### Overview
Major player actions leave permanent Marks that define how the world perceives them. Marks are narrative tags, not numerical penalties.

### Mark Types

#### Mark of the Protector
**Earned By**:
- Saving villages from threats
- Defending weak NPCs
- Preventing disasters
- Protecting endangered species

**Effects**:
- NPCs trust player more readily
- Children recognize and greet warmly
- Guards offer assistance
- Reduced prices from grateful merchants
- Priority access to emergency requests

#### Mark of the Betrayer
**Earned By**:
- Killing friendly NPCs
- Stealing from those who trusted you
- Breaking sacred oaths
- Selling out allies for profit

**Effects**:
- Some villages refuse entry
- Bounty hunters may appear
- Certain factions avoid contact
- Higher prices from suspicious merchants
- Locked out of trust-based quests

#### Mark of the Scholar
**Earned By**:
- Discovering forgotten knowledge
- Translating ancient texts
- Solving historical mysteries
- Teaching others

**Effects**:
- Libraries grant special access
- Scholars seek collaboration
- Unlock research opportunities
- Discounts on books and scrolls
- Invited to academic gatherings

#### Mark of the Beastfriend
**Earned By**:
- sparing creatures repeatedly
- Healing injured animals
- Protecting natural habitats
- Communicating with wildlife

**Effects**:
- Rare animals don't flee immediately
- Druids treat with respect
- Animal companions more likely
- Nature spirits acknowledge presence
- Access to hidden groves

#### Mark of the Merchant
**Earned By**:
- Extensive trading activity
- Establishing trade routes
- Economic investments
- Market manipulation (positive/negative)

**Effects**:
- Better prices automatically
- Exclusive merchant contacts
- Early access to rare goods
- Investment opportunities
- Economic intelligence

#### Mark of the Warrior
**Earned By**:
- Defeating powerful enemies
- Winning battles
- Mastering combat arts
- Military service

**Effects**:
- Soldiers show respect
- Training opportunities available
- Weapon smiths eager to serve
- War veterans share stories
- Combat challenges issued

#### Mark of the Shadow
**Earned By**:
- Stealth operations
- Assassination contracts
- Thief guild association
- Operating outside law

**Effects**:
- Criminal underworld access
- Information from shady sources
- Suspicion from authorities
- Secret passage revelations
- Black market opportunities

### Multiple Marks
Players can carry multiple marks simultaneously:
- Marks can conflict (Protector + Shadow creates complexity)
- Different groups emphasize different marks
- Marks evolve based on continued behavior
- Some marks can be "cleansed" through redemption arcs

## Dynamic NPC Lives

### Autonomous Behaviors
NPCs act independently:

**Career Development**
- Apprentices become masters
- Successful merchants expand businesses
- Failed entrepreneurs lose shops
- Career changes based on circumstances

**Relationship Evolution**
- Friendships form between NPCs
- Romances develop naturally
- Rivalries emerge from conflicts
- Families grow with children/grandchildren

**Personal Growth**
- Learning new skills over time
- Overcoming fears through experiences
- Changing opinions based on events
- Developing hobbies and interests

**Crisis Responses**
- Flee dangerous areas
- Band together against threats
- Seek player help when desperate
- Make sacrifices for loved ones

### NPC Initiatives
NPCs create their own storylines:

**Quest Giving Without Players**
- NPCs hire other NPCs for jobs
- Caravans form without player involvement
- Expeditions launch independently
- Wars start between factions

**Consequences Without Players**
- Villages thrive or fail based on NPC actions
- Businesses succeed or bankrupt naturally
- Political shifts occur off-screen
- Relationships evolve without player input

## Special NPC Categories

### Legendary NPCs
Rare individuals with unique importance:

**Characteristics**:
- Extended lifespans or immortality
- Vast knowledge or power
- Influence over major events
- Multiple dialogue trees based on world state
- Personal questlines spanning years

**Examples**:
- Ancient wizard studying forbidden magic
- Retired hero living in seclusion
- Mysterious merchant with impossible wares
- Oracle who sees possible futures

### Quest-Giver Evolution
Traditional quest givers transformed:

**Before**: Static position, identical dialogue, infinite quest supply
**After**: 
- Moves around world on schedule
- Dialogue reflects relationship history
- Quests limited by their current situation
- May stop giving quests if ignored too long
- Can die and be replaced

### Companion NPCs
NPCs who can travel with players:

**Recruitment**:
- Earned through relationship building
- Specific conditions must be met
- Some require completing personal quests
- Others demand payment or favors

**Companion Features**:
- Unique combat abilities
- Special perception filters (like player roles)
- Personal commentary on discoveries
- Relationship development during travel
- Can leave if treated poorly
- May have their own ambitions to pursue

## Implementation Considerations

### Technical Challenges
- **Memory Storage**: Efficient database for millions of NPC memories
- **Schedule Calculation**: Real-time pathfinding for thousands of NPCs
- **Relationship Tracking**: Complex graph of interconnected NPCs
- **Succession Logic**: Automated inheritance and replacement systems
- **Performance Optimization**: LOD (Level of Detail) for distant NPC AI

### Balance Concerns
- **Important NPC Protection**: Critical story NPCs may need plot armor
- **Grief Prevention**: Limits on killing essential NPCs in multiplayer
- **New Player Integration**: Catch-up mechanics for late-joining players
- **Content Availability**: Ensuring quests remain accessible despite NPC deaths

### Authoring Tools
- **NPC Editor**: Visual tool for creating NPCs with traits/schedules
- **Dialogue Tree System**: Branching conversations based on memory/state
- **Event Trigger System**: Linking player actions to NPC responses
- **Succession Planner**: Defining inheritance chains and conditions

## Success Metrics

The NPC system succeeds when:
- Players form genuine emotional attachments to NPCs
- Communities discuss NPC stories and relationships
- Player actions toward NPCs have visible long-term consequences
- NPCs feel like real individuals rather than game mechanics
- Unexpected NPC behaviors create emergent storytelling
- Players report feeling guilty about harming NPCs
- NPC deaths genuinely impact players emotionally
