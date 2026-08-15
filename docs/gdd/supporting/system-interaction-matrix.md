# System Interaction Matrix

## Overview

This document maps the interactions, dependencies, and data flows between all major systems in the Living World RPG. It serves as the authoritative reference for understanding system coupling, identifying potential bottlenecks, and ensuring architectural coherence.

---

## System Legend

| ID | System Name | Category | Owner Module |
|----|-------------|----------|--------------|
| S01 | Core Game Loop | Core | Engine.Core |
| S02 | World Simulation Engine | Core | Engine.Simulation |
| S03 | Player Journey | Core | Engine.Progression |
| S04 | Legacy Scenario System | Core | Engine.Scenarios |
| S05 | Roles & Character Perspectives | Core | Engine.Roles |
| S06 | NPC System & Relationships | Core | Engine.NPC |
| S07 | Knowledge Economy | Core | Engine.Economy |
| S08 | Ancient Entities | Core | Engine.Entities |
| S09 | Skills Progression | Core | Engine.Progression |
| S10 | Economy & Trade | Core | Engine.Economy |
| S11 | Information Propagation | Core | Engine.Communication |
| S12 | Combat System | Core | Engine.Combat |
| S13 | Crafting & Professions | Core | Engine.Crafting |
| S14 | Failure Consequences | Supporting | Engine.Consequences |
| S15 | World Geography & Rules | Supporting | Engine.World |
| S16 | UI/UX System | Supporting | Client.UI |
| S17 | Audio Atmosphere | Supporting | Client.Audio |
| S18 | Magic System | Supporting | Engine.Magic |
| S19 | Items & Equipment | Supporting | Engine.Items |
| S20 | Persistence Layer | Technical | Engine.Persistence |
| S21 | Network Layer | Technical | Engine.Network |
| S22 | AI Decision Framework | Technical | Engine.AI |

---

## Interaction Matrix

### Legend for Interaction Types
- **R** = Reads data from
- **W** = Writes/updates data to
- **T** = Triggers events in
- **D** = Depends on (requires system to be initialized)
- **C** = Calls functions/methods in
- **E** = Emits events consumed by

| From \ To | S01 | S02 | S03 | S04 | S05 | S06 | S07 | S08 | S09 | S10 | S11 | S12 | S13 | S14 | S15 | S16 | S17 | S18 | S19 | S20 | S21 | S22 |
|-----------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| **S01** Core Loop | — | C | C | T | R | R | R | R | R | R | R | C | C | T | R | R | T | C | R | C | C | C |
| **S02** World Sim | — | — | T | T | R | T | T | T | T | T | T | T | T | T | R | — | T | T | T | W | — | C |
| **S03** Player Journey | R | R | — | C | R | R | R | R | C | R | R | C | C | C | R | C | — | R | R | W | — | — |
| **S04** Legacy Scenarios | R | R | C | — | R | R | R | C | R | R | R | C | R | C | R | — | — | R | R | W | — | C |
| **S05** Roles | R | R | R | R | — | R | R | R | R | R | R | R | R | R | R | C | — | R | R | R | — | — |
| **S06** NPCs | R | C | R | R | R | — | C | R | C | C | C | C | R | C | R | R | — | C | R | W | — | C |
| **S07** Knowledge Econ | R | R | R | R | R | R | — | R | R | C | C | R | R | R | R | R | — | R | R | W | — | — |
| **S08** Ancient Entities | R | C | R | R | R | R | R | — | R | R | R | R | R | R | C | — | — | C | R | R | — | C |
| **S09** Skills | R | R | C | R | R | R | R | R | — | R | R | C | C | R | R | R | — | C | R | W | — | — |
| **S10** Economy | R | R | R | R | R | C | C | R | R | — | C | R | C | R | R | R | — | R | C | W | — | — |
| **S11** Info Prop | R | C | R | R | R | C | C | R | R | C | — | R | R | R | R | C | C | R | R | W | C | — |
| **S12** Combat | R | C | C | C | R | C | R | R | C | R | R | — | R | C | C | C | T | C | C | W | — | C |
| **S13** Crafting | R | C | C | R | R | R | R | R | C | C | R | R | — | C | R | C | — | C | C | W | — | — |
| **S14** Failure | R | C | C | C | R | C | R | R | R | R | R | C | C | — | C | C | — | R | C | W | — | C |
| **S15** Geography | R | R | R | R | R | R | R | C | R | R | R | R | R | R | — | R | T | R | R | R | — | — |
| **S16** UI/UX | R | R | C | R | C | C | C | R | C | C | C | C | C | C | R | — | C | C | C | R | R | — |
| **S17** Audio | R | C | R | R | R | R | R | R | R | R | R | E | R | R | E | R | — | E | R | R | — | — |
| **S18** Magic | R | C | C | R | R | R | R | C | C | R | R | C | R | R | R | C | — | — | R | W | — | C |
| **S19** Items | R | R | R | R | R | R | R | R | R | C | R | C | C | C | R | C | — | R | — | W | — | — |
| **S20** Persistence | C | C | C | C | C | C | C | C | C | C | C | C | C | C | C | C | C | C | C | — | C | C |
| **S21** Network | C | — | C | C | C | C | C | C | C | C | C | C | C | C | C | C | — | C | C | C | — | C |
| **S22** AI Decision | R | C | R | C | R | C | R | C | R | R | R | C | R | C | R | R | — | C | R | R | — | — |

---

## Critical Dependency Chains

### Chain 1: Player Action → World State Update
```
S01 (Core Loop) 
  → S12/S13/S18 (Action System: Combat/Crafting/Magic)
    → S02 (World Simulation)
      → S06/S08 (NPC/Entity Reaction via S22 AI)
        → S11 (Information Propagation)
          → S20 (Persistence)
```

### Chain 2: Knowledge Discovery → Economy Impact
```
S03 (Player Journey - Discovery)
  → S07 (Knowledge Economy - Value Assignment)
    → S11 (Information Propagation - Spread)
      → S10 (Economy & Trade - Price Adjustment)
        → S06 (NPC Behavior Change)
          → S20 (Persistence)
```

### Chain 3: Legacy Scenario Trigger → Multi-System Cascade
```
S04 (Legacy Scenario - Trigger Condition)
  → S02 (World Simulation - State Change)
    → S15 (Geography - Regional Effects)
      → S06/S08 (NPC/Entity Behavior)
        → S12/S14 (Combat/Failure Systems)
          → S03 (Player Journey - Legacy Recording)
            → S20 (Persistence)
```

### Chain 4: Skill Progression → Capability Unlock
```
S09 (Skills Progression - Mastery Threshold)
  → S03 (Player Journey - New Abilities)
    → S12/S13/S18 (Enhanced Combat/Crafting/Magic)
      → S02 (World Simulation - New Interactions)
        → S07 (Knowledge Economy - New Discoveries)
          → S20 (Persistence)
```

---

## High-Coupling Systems (Refactoring Candidates)

### ⚠️ World Simulation Engine (S02)
**Coupling Score:** 21/21 systems interact with it  
**Risk:** Central bottleneck, single point of failure  
**Mitigation:** 
- Implement event-driven architecture
- Use message queues for non-critical updates
- Consider microservices split: Weather, Ecology, Physics

### ⚠️ Core Game Loop (S01)
**Coupling Score:** 21/21 systems called by it  
**Risk:** Tight coupling makes testing difficult  
**Mitigation:**
- Introduce facade pattern for system groups
- Use dependency injection for mock testing
- Implement command pattern for action queuing

### ⚠️ Persistence Layer (S20)
**Coupling Score:** 21/21 systems write to it  
**Risk:** Database contention, save/load bottlenecks  
**Mitigation:**
- Implement write-back caching
- Use event sourcing for critical systems
- Partition database by system domain

---

## Data Flow Patterns

### Pattern 1: Request-Response (Synchronous)
**Used by:** S01→S12 (Combat), S16→S19 (UI→Items), S03→S09 (Journey→Skills)  
**Latency Requirement:** <16ms (1 frame)  
**Implementation:** Direct method calls, in-memory state

### Pattern 2: Event-Driven (Asynchronous)
**Used by:** S02→S11 (World→Info Prop), S12→S17 (Combat→Audio), S04→S06 (Scenario→NPC)  
**Latency Requirement:** <100ms acceptable  
**Implementation:** Event bus, pub-sub pattern

### Pattern 3: Batch Processing (Deferred)
**Used by:** S10 (Economy price updates), S11 (Information spread), S02 (Ecology simulation)  
**Latency Requirement:** Seconds to minutes acceptable  
**Implementation:** Job queues, scheduled tasks, tick-based updates

### Pattern 4: Stream Processing (Real-time)
**Used by:** S21 (Network replication), S17 (Audio positioning), S16 (UI updates)  
**Latency Requirement:** <50ms critical  
**Implementation:** WebSockets, delta compression, interpolation

---

## System Boundaries & Interfaces

### Core Engine Boundary
**Systems:** S01-S15  
**Access Pattern:** Internal engine modules, direct memory access  
**External Interface:** S20 (Persistence), S21 (Network)

### Client Boundary  
**Systems:** S16 (UI/UX), S17 (Audio)  
**Access Pattern:** Read-only from engine, write to input layer  
**External Interface:** S21 (Network), platform APIs

### Technical Services Boundary
**Systems:** S20 (Persistence), S21 (Network), S22 (AI)  
**Access Pattern:** Service calls from all systems  
**External Interface:** Database, network sockets, ML models

---

## Integration Points & API Contracts

### S02 World Simulation → External Systems
```
Interface: IWorldStateProvider
Methods:
  - GetWeather(region_id) → WeatherState
  - GetTime() → WorldTime
  - GetEcologyState(region_id) → EcologySnapshot
  - SubscribeToChanges(callback) → SubscriptionHandle
```

### S06 NPC System → AI Decision Framework
```
Interface: INPCDecisionMaker
Methods:
  - DecideAction(npc_id, context) → ActionPlan
  - UpdateRelationship(npc_id, target_id, delta) → void
  - GetMemory(npc_id, query) → MemoryFragment
```

### S07 Knowledge Economy → S10 Economy & Trade
```
Interface: IKnowledgeValueProvider
Methods:
  - GetKnowledgeValue(knowledge_id, region_id) → Decimal
  - GetScarcityIndex(knowledge_id) → Float (0.0-1.0)
  - OnKnowledgeDiscovered(knowledge_id, discoverer_id) → void
```

### S20 Persistence → All Systems
```
Interface: IPersistable
Methods:
  - Serialize() → ByteString
  - Deserialize(ByteString) → void
  - GetVersion() → Int
  - GetChecksum() → Hash
```

---

## Race Conditions & Concurrency Hazards

### Hazard 1: Simultaneous World State Updates
**Scenario:** Multiple players trigger world changes in same region  
**Affected Systems:** S02, S12, S13, S15  
**Mitigation:** Region-based locking, optimistic concurrency with retry

### Hazard 2: Knowledge Value Oscillation
**Scenario:** Rapid discovery/spread causes price instability  
**Affected Systems:** S07, S10, S11  
**Mitigation:** Damping functions, update rate limiting, circuit breakers

### Hazard 3: NPC Decision Conflicts
**Scenario:** Multiple NPCs react to same event with conflicting actions  
**Affected Systems:** S06, S22  
**Mitigation:** Priority queues, action arbitration, cooldown periods

### Hazard 4: Save/Load Inconsistency
**Scenario:** System state changes during persistence operation  
**Affected Systems:** S20, all systems  
**Mitigation:** Snapshot isolation, transaction logs, rollback capability

---

## Performance Bottlenecks & Optimization Strategies

### Bottleneck 1: World Simulation Tick
**Current Cost:** O(n²) for entity interactions  
**Optimization:** Spatial partitioning, interest management, LOD simulation

### Bottleneck 2: Information Propagation Graph
**Current Cost:** O(n*m) for n nodes, m edges  
**Optimization:** Graph pruning, cluster-based propagation, approximate algorithms

### Bottleneck 3: Economy Recalculation
**Current Cost:** O(k) for k knowledge items, every tick  
**Optimization:** Incremental updates, lazy evaluation, cache invalidation

### Bottleneck 4: AI Decision Trees
**Current Cost:** O(d*b^d) for depth d, branching factor b  
**Optimization:** Behavior trees with memoization, utility AI precomputation

---

## Testing Strategy by System Cluster

### Cluster 1: Core Loop + World Sim + Persistence
**Test Type:** Integration test with deterministic ticks  
**Mock Strategy:** Fixed seed RNG, controlled time step  
**Validation:** State equivalence after N ticks

### Cluster 2: NPCs + AI + Information Propagation
**Test Type:** Emergent behavior testing  
**Mock Strategy:** Scripted player actions, frozen world state  
**Validation:** Statistical distribution of outcomes

### Cluster 3: Economy + Knowledge + Skills
**Test Type:** Economic equilibrium testing  
**Mock Strategy:** Bot players with defined strategies  
**Validation:** Price stability, resource distribution metrics

### Cluster 4: Combat + Crafting + Magic
**Test Type:** Balance testing  
**Mock Strategy:** Automated combat simulations  
**Validation:** Win rate distribution, resource consumption rates

---

## Versioning & Migration Strategy

### System Version Schema
```
Format: {major}.{minor}.{patch}
- Major: Breaking changes to interfaces or data structures
- Minor: New features, backward compatible
- Patch: Bug fixes, performance improvements
```

### Migration Protocol
1. **Deprecation Phase:** Mark old interface deprecated, support both
2. **Transition Phase:** Default to new interface, fallback to old
3. **Removal Phase:** Remove old interface after N releases

### Data Migration
- Schema versioning in persistence layer
- Migration scripts per system
- Rollback capability for failed migrations

---

## Monitoring & Observability

### Key Metrics per System
| System | Metric | Target | Alert Threshold |
|--------|--------|--------|-----------------|
| S02 World Sim | Tick duration | <10ms | >50ms |
| S06 NPC | Decision latency | <5ms | >20ms |
| S11 Info Prop | Propagation delay | <100ms | >1s |
| S20 Persistence | Save duration | <100ms | >500ms |
| S21 Network | Replication lag | <50ms | >200ms |

### Distributed Tracing
- Trace IDs propagated across system boundaries
- Span collection for performance profiling
- Correlation logs for debugging cascading failures

---

## Appendix A: System Initialization Order

```
Phase 1: Technical Foundation
  1. S20 Persistence Layer
  2. S21 Network Layer
  3. S22 AI Decision Framework

Phase 2: Core Engine
  4. S02 World Simulation Engine
  5. S15 World Geography & Rules
  6. S01 Core Game Loop

Phase 3: Game Systems
  7. S03 Player Journey
  8. S04 Legacy Scenario System
  9. S05 Roles & Character Perspectives
  10. S06 NPC System & Relationships
  11. S07 Knowledge Economy
  12. S08 Ancient Entities
  13. S09 Skills Progression
  14. S10 Economy & Trade
  15. S11 Information Propagation
  16. S12 Combat System
  17. S13 Crafting & Professions
  18. S14 Failure Consequences
  19. S18 Magic System
  20. S19 Items & Equipment

Phase 4: Client Systems
  21. S16 UI/UX System
  22. S17 Audio Atmosphere
```

---

## Appendix B: Change Impact Analysis Template

When modifying any system, use this template:

```markdown
### Change: [Description]
**Modified System:** [System ID & Name]
**Direct Dependencies:** [List systems that directly call this system]
**Indirect Dependencies:** [List systems affected through chains]
**Data Structure Changes:** [Yes/No - describe]
**Interface Changes:** [Yes/No - describe]
**Migration Required:** [Yes/No - describe]
**Testing Scope:** [Unit/Integration/E2E - describe scenarios]
**Rollback Plan:** [Describe if change cannot be deployed]
```

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-12-19 | AI Agent | Initial creation based on ChatGPT reference analysis |

---

## Related Documents

- [[Engine Module Architecture]](./engine-module-architecture.md) - Next: Module ownership and access rules
- [[World Data Schema]](../technical/world-data-schema.md) - Database structure specifications
- [[AI Decision Framework]](../technical/ai-decision-framework.md) - Technical specification for NPC decision-making
- [[Combat System GDD]](./combat-system.md) - Real-time skill-based combat
- [[Crafting & Professions GDD]](./crafting-professions.md) - Physical crafting system
