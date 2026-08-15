# Failure Consequences & Recovery System

## 1. Overview

### 1.1 Purpose
The failure system transforms setbacks from frustrating obstacles into meaningful narrative moments that deepen player investment. Failure is not punishment—it's a catalyst for growth, storytelling, and world interaction. Every mistake leaves a mark, and recovery defines character.

### 1.2 Design Pillars Alignment
- **Knowledge > Gold**: Players learn more from failures than successes; wisdom comes through hardship
- **World Remembers**: Failures are recorded alongside successes; scars tell stories
- **Discovery Drives Design**: New recovery methods discovered through experimentation
- **Permanent Consequences**: Some failures leave lasting marks, but resilience builds strength

### 1.3 Scope
This document covers:
- Failure taxonomy and categorization
- Immediate consequences (combat, crafting, exploration)
- Long-term impacts (reputation, psychological, physical)
- Recovery mechanics (healing, redemption, restoration)
- Resilience building and growth systems
- Narrative integration of failure

---

## 2. Failure Taxonomy

### 2.1 Failure Categories

| Category | Examples | Severity | Reversibility |
|----------|----------|----------|---------------|
| **Minor** | Dropped item, failed craft attempt, lost argument | Low | Fully reversible |
| **Moderate** | Combat defeat, broken equipment, injured ally | Medium | Recoverable with effort |
| **Major** | Death of companion, destroyed reputation, lost quest | High | Partially reversible |
| **Catastrophic** | Character death (hardcore), kingdom fall, world event | Extreme | Permanent/legacy only |

### 2.2 Failure Domains

#### 2.2.1 Combat Failures
| Failure Type | Trigger | Immediate Consequence |
|--------------|---------|----------------------|
| Wounded | Health < 50% | Injury debuff, reduced effectiveness |
| Defeated | Health = 0 | Equipment drop, respawn delay |
| Captured | Surrender or overwhelmed | Imprisonment, ransom demand |
| Companion Lost | Ally dies in battle | Grief debuff, relationship changes |
| Reputation Damage | Fleeing battle, cowardice | Fame loss, title change |

#### 2.2.2 Crafting Failures
| Failure Type | Trigger | Immediate Consequence |
|--------------|---------|----------------------|
| Botched Craft | Skill check fail | Item destroyed, materials lost |
| Poor Quality | Multiple mistakes | Low-value item, reputation hit |
| Tool Break | Critical failure | Tool damaged, crafting interrupted |
| Workshop Accident | Rare critical fail | Injury, property damage |
| Recipe Corruption | Wrong ingredients | Unusable result, potential hazard |

#### 2.2.3 Social Failures
| Failure Type | Trigger | Immediate Consequence |
|--------------|---------|----------------------|
| Insult Given | Failed diplomacy | Relationship -10 to -50 |
| Promise Broken | Failed to deliver | Trust severely damaged |
| Secret Revealed | Failed stealth/discretion | Information spreads |
| Alliance Rejected | Failed negotiation | Diplomatic relations sour |
| Public Humiliation | Failed performance | Reputation damage, mockery |

#### 2.2.4 Exploration Failures
| Failure Type | Trigger | Immediate Consequence |
|--------------|---------|----------------------|
| Lost | Navigation fail | Time wasted, resources consumed |
| Trapped | Triggered trap | Injury, equipment damage |
| Environmental Hazard | Weather, terrain | Status effects, delays |
| Discovery Denied | Failed perception | Miss opportunity, no reward |
| Path Blocked | Obstacle insurmountable | Must find alternate route |

---

## 3. Consequence Systems

### 3.1 Physical Consequences

#### 3.1.1 Injury System
Injuries persist beyond the immediate failure:

| Injury Type | Cause | Duration | Effects | Treatment Required |
|-------------|-------|----------|---------|-------------------|
| Minor Cut | Light combat failure | 2-5 days | -5% accuracy | Basic first aid |
| Deep Wound | Heavy combat failure | 1-2 weeks | -20% limb function, bleed | Healer attention |
| Broken Bone | Critical hit, fall | 3-6 weeks | Limb unusable | Surgery, immobilization |
| Concussion | Head trauma | 1-4 weeks | Blurred vision, confusion | Rest, monitoring |
| Burn | Fire failure | 1-3 weeks | DoT, scarring | Cooling, bandaging |
| Poison | Toxic exposure | Variable | Depends on toxin | Antidote, purging |
| Disease | Contagion | Days to permanent | Various debuffs | Medical treatment |

#### 3.1.2 Scarring System
Some injuries leave permanent marks:

**Physical Scars:**
- Visible cosmetic changes
- Some scars grant minor bonuses (battle-hardened)
- Others impose penalties (limited mobility)
- Scars become part of character identity

**Psychological Scars (Trauma):**
- PTSD from catastrophic events
- Phobias develop (fear of fire, heights, etc.)
- Trust issues from betrayal
- Can be addressed through therapy, time, or significant events

### 3.2 Material Consequences

#### 3.2.1 Equipment Loss
On defeat or failure:

**Death Penalty:**
- Drop 3-5 random inventory items at location
- Equipped items have 20% chance to break
- Currency loss: 10-30% of carried gold

**Non-Death Defeat:**
- Looters may take valuable items
- Ransom demands for return of equipment
- Black market circulation of lost gear

#### 3.2.2 Property Damage
- Homes can be damaged in disasters
- Workshops destroyed in accidents
- Crops ruined by weather/events
- Repair costs scale with property value

### 3.3 Social Consequences

#### 3.3.1 Reputation Impact

**Reputation Tiers:**
| Tier | Name | Effect | Recovery Difficulty |
|------|------|--------|---------------------|
| 5 | Revered | +50% social success | N/A (highest) |
| 4 | Respected | +25% social success | Moderate |
| 3 | Neutral | No modifier | Easy |
| 2 | Distrusted | -25% social success | Hard |
| 1 | Hated | -50% social success, hostility | Very Hard |
| 0 | Outcast | Attacked on sight, no services | Extreme |

**Reputation Changes:**
- Single major failure: -1 to -2 tiers
- Repeated minor failures: Gradual decline
- Recovery requires consistent positive actions
- Some reputations permanently stained (notorious villains)

#### 3.3.2 Relationship Damage

**Individual Relationships:**
| Relationship | Failure Impact | Recovery Method |
|--------------|---------------|-----------------|
| Friend | Trust -20 to -50 | Apology, gifts, shared experiences |
| Family | Trust -30 to -70 | Extended reconciliation, proving change |
| Romantic | May end relationship | Extremely difficult, often permanent |
| Business Partner | Contract voided | Financial restitution, legal process |
| Liege/Lord | Title revoked, exile | Proving loyalty, great service |

**Faction Relationships:**
- Failed missions reduce faction standing
- Betrayal may result in permanent exile
- Redemption quests available for serious offenses
- Some factions never forgive certain actions

### 3.4 Progression Consequences

#### 3.4.1 Skill Regression
On significant failure:

- **-5 to -15 points** in most-used skills (temporary)
- Represents loss of confidence, not actual ability
- Recoverable through practice
- Hardcore mode: Permanent regression possible

#### 3.4.2 Opportunity Loss
- Failed quests may not be repeatable
- Missed timing locks out content
- Alternative paths open (failure creates new stories)
- Some opportunities unique to failure states

---

## 4. Recovery Mechanics

### 4.1 Physical Recovery

#### 4.1.1 Healing System

**Natural Healing:**
```
Healing Rate = Base Rate × Rest Bonus × Nutrition Bonus × Medical Care Bonus
```

- **Base Rate**: 1-5 HP/day depending on injury severity
- **Rest Bonus**: 2x when resting in safe location
- **Nutrition Bonus**: 1.5x with quality food
- **Medical Care Bonus**: 1.5-3x with professional treatment

**Medical Treatment Tiers:**
| Care Level | Provider | Multiplier | Cost |
|------------|----------|------------|------|
| Self-Care | Player | 1.0x | Free |
| First Aid | Any trained person | 1.3x | Low |
| Professional | Healer NPC/player | 2.0x | Medium |
| Expert | Master healer | 2.5x | High |
| Legendary | Renowned physician | 3.0x | Very High |

#### 4.1.2 Rehabilitation
For severe injuries:

- **Physical Therapy**: Restore function to damaged limbs
- **Time Requirement**: Weeks to months of game time
- **Mini-game**: Exercises must be performed correctly
- **Success Rate**: Improves with consistency

### 4.2 Material Recovery

#### 4.2.1 Item Retrieval
After death or loss:

**Body Recovery:**
- Return to death location within 24 hours
- Risk of ambush by looters/enemies
- Items may be scattered or taken
- Success restores 80-100% of lost items

**Ransom Payment:**
- Negotiate with captors
- Pay 20-50% of item value
- Guaranteed return but expensive
- May encourage future captures

**Insurance System (Late-game):**
- Premium crafters/guilds offer insurance
- Pay upfront fee (5-10% of value)
- Claim replacement on loss
- Limited to non-legendary items

#### 4.2.2 Repair Services
Damaged equipment can be restored:

| Damage Level | Repair Method | Cost | Quality Impact |
|--------------|---------------|------|----------------|
| Minor | Self-repair kit | Low | None |
| Moderate | Professional repair | Medium | -5% max quality |
| Severe | Master craftsman | High | -15% max quality |
| Broken | Full restoration | Very High | -25% max quality |
| Shattered | Cannot repair | N/A | Must replace |

### 4.3 Social Recovery

#### 4.3.1 Reputation Restoration

**Recovery Actions:**
| Action | Reputation Gain | Requirements |
|--------|-----------------|--------------|
| Good Deeds | +1 to +5 per act | Consistent behavior |
| Public Service | +5 to +15 | Significant contribution |
| Heroic Act | +20 to +50 | Extraordinary achievement |
| Donation | +1 per gold amount | Wealth requirement |
| Quest Completion | +5 to +20 | Faction-specific |

**Redemption Quests:**
- Available for serious reputation damage
- Challenging multi-stage objectives
- Success restores significant reputation
- Failure worsens standing permanently

#### 4.3.2 Relationship Repair

**Apology System:**
1. **Acknowledge Wrong**: Admit fault publicly or privately
2. **Express Remorse**: Sincere apology (mini-game)
3. **Make Amends**: Compensation or service
4. **Prove Change**: Consistent good behavior over time

**Forgiveness Factors:**
- Severity of offense
- History of relationship
- Sincerity of apology
- Adequacy of amends
- Time since offense

### 4.4 Psychological Recovery

#### 4.4.1 Trauma Healing

**Therapy Options:**
| Method | Effectiveness | Time | Availability |
|--------|---------------|------|--------------|
| Rest/Time | Slow | Months | Always |
| Talking to Friends | Moderate | Weeks | Requires relationships |
| Professional Counselor | High | Weeks | Limited availability |
| Meditation/Spiritual | Variable | Months | Requires belief system |
| Cathartic Action | High | Days/Weeks | Dangerous method |

**Phobia Overcoming:**
- Gradual exposure therapy
- Facing fear in controlled environment
- Success grants "Courage" buff
- Failure reinforces phobia

#### 4.4.2 Resilience Building

Players develop resilience through:
- Surviving previous failures
- Supporting others through hardship
- Learning philosophical/spiritual practices
- Achieving difficult recoveries

**Resilience Benefits:**
- Reduced impact of future failures
- Faster psychological recovery
- Access to "Veteran" dialogue options
- Mentorship opportunities

---

## 5. Growth Through Failure

### 5.1 Learning Mechanics

#### 5.1.1 Lesson System
Each failure teaches something:

**Failure Analysis:**
- Post-failure reflection period
- Identify what went wrong
- Unlock hidden knowledge
- Apply lessons to future attempts

**Lesson Types:**
| Lesson | Source | Benefit |
|--------|--------|---------|
| Tactical | Combat defeat | +5% vs same enemy type |
| Technical | Crafting failure | -10% failure rate on recipe |
| Social | Failed interaction | +10% success with similar NPCs |
| Survival | Near-death experience | +15% hazard awareness |

#### 5.1.2 Wisdom Accumulation

**Wisdom Points:**
- Earned through significant failures
- Invisible counter (part of character depth)
- Spent on:
  - Insight abilities (see weaknesses)
  - Teaching skills (mentor others)
  - Philosophical unlocks (new dialogue)
  - Epiphany triggers (breakthrough moments)

### 5.2 Character Development

#### 5.2.1 Personality Evolution

Failures shape character personality:

**Possible Traits from Failure:**
| Trait | Source | Effect |
|-------|--------|--------|
| Cautious | Multiple defeats | +Defense, -Initiative |
| Vengeful | Betrayal | +Damage vs betrayer type, -Diplomacy |
| Compassionate | Witnessed suffering | +Healing, +Relationship building |
| Stoic | Endured hardship | +Pain tolerance, -Emotional expression |
| Reckless | Survived impossible odds | +Bold actions, -Safety |

#### 5.2.2 Story Integration

**Personal Narrative:**
- Failures become part of character backstory
- NPCs reference past failures
- Dialogue options reflect experiences
- Some content only accessible through failure paths

**Legacy Recording:**
- Major failures recorded in world history
- Bards sing of tragic defeats
- Future generations learn from your mistakes
- Failure can inspire others

---

## 6. Failure Mitigation

### 6.1 Prevention Systems

#### 6.1.1 Warning Indicators

Subtle cues before failure:

**Combat:**
- Enemy telegraphing powerful attacks
- Stamina warnings (visual/audio)
- Surrounding danger awareness

**Crafting:**
- Temperature color changes
- Material stress sounds
- Tool wear indicators

**Social:**
- NPC body language shifts
- Tone changes in dialogue
- Relationship status hints

#### 6.1.2 Safety Nets

**Beginner Protection:**
- Sanctuary zones (no permadeath)
- Training failures have reduced consequences
- Mentor intervention available
- Second chance quests

**Insurance Mechanics:**
- Backup equipment storage
- Emergency teleport scrolls
- Guardian NPCs (limited uses)
- Guild support systems

### 6.2 Risk Management

#### 6.2.1 Preparation Systems

**Pre-Adventure Checklist:**
- Equipment inspection
- Supply stockpiling
- Intelligence gathering
- Contingency planning

**Risk Assessment:**
- Evaluate threat levels
- Calculate success probability
- Plan escape routes
- Set rally points

#### 6.2.2 Team Support

**Group Failure Mitigation:**
- Shared burden (equipment pool)
- Multiple revival options
- Combined resources for recovery
- Emotional support network

---

## 7. Special Failure States

### 7.1 Death Variants

#### 7.1.1 Standard Death
- Respawn at sanctuary
- Equipment loss (partial)
- Skill regression (temporary)
- Legacy recorded

#### 7.1.2 Heroic Death
- Died completing important objective
- Reduced penalties
- Reputation bonus
- Memorial erected

#### 7.1.3 Dishonorable Death
- Died fleeing or in disgrace
- Increased penalties
- Reputation damage
- Mockery from others

#### 7.1.4 Sacrificial Death
- Chose to die for others
- No skill regression
- Major reputation gain
- Legend status possible

### 7.2 Permanent Consequences (Hardcore)

#### 7.2.1 Permadeath
- Character deleted on death
- Legacy continues through descendants
- World remembers deeds
- Items enter circulation

#### 7.2.2 Irreversible Damage
- Some injuries never fully heal
- Lost relationships cannot be repaired
- Destroyed reputations stay destroyed
- Creates unique character story

---

## 8. UI & Feedback

### 8.1 Failure Communication

**Minimal HUD Approach:**
- No explicit "FAILURE" messages
- Visual/audio cues convey outcome
- Journal entries record significant events
- NPCs react to visible consequences

### 8.2 Recovery Tracking

**Player Tools:**
- Injury journal (tracks healing progress)
- Reputation ledger (shows relationship changes)
- Goal tracker (recovery milestones)
- Support network list (who can help)

### 8.3 Narrative Presentation

**Story Integration:**
- Cutscenes for major failures
- NPC dialogue references setbacks
- Environmental changes reflect consequences
- Music shifts during recovery arcs

---

## 9. Balance Considerations

### 9.1 Frustration Prevention

**Design Principles:**
- Failures should feel fair, not random
- Recovery should be challenging but achievable
- Some failures create interesting new paths
- Player agency preserved even in failure

**Anti-Frustration Features:**
- No infinite failure loops
- Escape valves for impossible situations
- Catch-up mechanics for severe setbacks
- Opt-in hardcore modes only

### 9.2 Difficulty Scaling

**Contextual Consequences:**
| Context | Consequence Modifier |
|---------|---------------------|
| Tutorial | -80% |
| Early Game | -50% |
| Normal Play | 0% |
| Hardcore | +50% |
| Challenge Mode | +100% |

---

## 10. Dependencies

### 10.1 Required Systems

- **Health/Injury System**: Physical damage tracking
- **Reputation System**: Social standing management
- **Inventory System**: Item loss/recovery
- **Skills System**: Regression and learning
- **NPC System**: Relationship tracking
- **Legacy System**: Death recording

### 10.2 Related Systems

- **Combat System**: Defeat conditions
- **Crafting System**: Failure states
- **Economy System**: Recovery costs
- **Narrative System**: Story integration
- **Save System**: Checkpoint management

---

## 11. Open Questions

1. Should players be able to choose consequence severity?
2. How to handle griefing disguised as legitimate failure?
3. What safety measures prevent cascade failures (one failure causing unstoppable chain)?
4. Should there be failure caps (maximum losses per time period)?
5. How to make failure fun rather than punishing?

---

## 12. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-XX | AI Architect | Initial draft using design-system methodology |

---

## Appendix A: Failure Scenario Examples

### A.1 Combat Defeat Recovery
*Player defeated in duel:*
- Wakes up at nearest sanctuary, missing sword and armor
- Visits blacksmith to purchase replacement gear (expensive)
- Hears rumors his defeated opponent boasts publicly
- Options: Challenge again (prepared better), seek revenge through other means, accept humiliation and grow wiser
- Chooses training path, returns stronger months later
- Defeat becomes origin story for character development

### A.2 Crafting Disaster
*Master smith attempts legendary blade:*
- Critical failure during quenching—blade cracks
- Weeks of work ruined, rare materials lost
- Reputation takes hit (witnesses saw failure)
- Enters depression, considers abandoning craft
- Veteran mentor shares own failure story
- Returns to forge, applies lessons learned
- Next attempt succeeds with deeper understanding

### A.3 Social Redemption Arc
*Player betrays faction trust:*
- Caught selling secrets to enemies
- Exiled from faction, hunted by former allies
- Goes into hiding, takes odd jobs
- Meets contact offering redemption quest
- Completes dangerous multi-stage mission
- Confronts faction leader, begs forgiveness
- Granted probationary status
- Spends years rebuilding trust
- Eventually becomes faction advisor—failure made them wiser

### A.4 Catastrophic Loss (Hardcore)
*Permadeath character:*
- Dies defending village from raid
- Character deleted
- Descendant born with family legacy
- Inherits partial reputation (mixed—heroic death but also failure)
- Finds ancestor's grave, reads their story
- Continues journey with inherited goals
- Village remembers sacrifice, names monument after ancestor
- Failure transformed into legacy
