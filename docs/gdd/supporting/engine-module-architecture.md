# Engine Module Architecture

## Overview

This document defines the modular architecture of the Living World RPG engine, specifying module boundaries, ownership rules, access patterns, and inter-module communication protocols. It ensures clean separation of concerns, testability, and maintainability as the codebase scales.

---

## Architecture Principles

### 1. Layered Architecture
```
┌─────────────────────────────────────────┐
│           Presentation Layer            │
│    (UI, Audio, Input, Rendering)        │
├─────────────────────────────────────────┤
│            Game Logic Layer             │
│   (Systems, Rules, Mechanics, AI)       │
├─────────────────────────────────────────┤
│           Core Engine Layer             │
│  (Simulation, Physics, Time, World)     │
├─────────────────────────────────────────┤
│        Infrastructure Layer             │
│ (Persistence, Network, Logging, Config) │
└─────────────────────────────────────────┘
```

### 2. Dependency Rules
- **Upper layers depend on lower layers** (never vice versa)
- **Same-layer modules communicate via interfaces/events**
- **No circular dependencies** between modules
- **Dependencies point toward stability** (stable modules depended upon by volatile ones)

### 3. Module Encapsulation
- Each module exposes a **public API** (interface/abstract classes)
- Internal implementation is **private** to the module
- Cross-module access only through **defined interfaces**
- No direct field access across module boundaries

---

## Module Catalog

### Infrastructure Layer Modules

#### M01: Persistence Module
**Purpose:** Data storage, retrieval, serialization, migration  
**Public API:** `IPersistenceService`  
**Dependencies:** None (leaf module)  
**Dependents:** All game logic modules  

```
Interfaces:
  - IPersistenceService
    - Save<T>(string key, T data) → Task<bool>
    - Load<T>(string key) → Task<T?>
    - Delete(string key) → Task<bool>
    - BeginTransaction() → ITransaction
    - Migrate(int targetVersion) → Task<MigrationResult>

  - ISerializable
    - Serialize() → ByteString
    - Deserialize(ByteString) → void

  - ITransaction
    - Commit() → Task<bool>
    - Rollback() → Task
```

**Access Rules:**
- ✅ Any module can read/write its own data
- ❌ No module can access another module's data directly
- ✅ Only Persistence module accesses database drivers

---

#### M02: Network Module
**Purpose:** Multiplayer communication, replication, synchronization  
**Public API:** `INetworkService`  
**Dependencies:** M01 (Persistence for session data)  
**Dependents:** All multiplayer-aware modules  

```
Interfaces:
  - INetworkService
    - Connect(string endpoint) → Task<ConnectionResult>
    - Disconnect() → Task
    - Send<T>(string channel, T message) → Task
    - Subscribe<T>(string channel, Action<T> handler) → Subscription
    - GetLatency() → TimeSpan
    - IsConnected() → bool

  - IMessage : ISerializable
    - GetChannel() → string
    - GetPriority() → MessagePriority
    - GetReliability() → ReliabilityMode

  - INetworkRenderer
    - Interpolate<T>(T from, T to, float t) → T
    - Predict<T>(T current, Vector3 velocity) → T
    - Reconcile<T>(T predicted, T authoritative) → T
```

**Access Rules:**
- ✅ Game logic modules send messages through network service
- ❌ No module bypasses network abstraction layer
- ✅ Network module handles all socket/protocol details

---

#### M03: Configuration Module
**Purpose:** Game settings, balance parameters, feature flags  
**Public API:** `IConfigurationService`  
**Dependencies:** M01 (Persistence for saved settings)  
**Dependents:** All modules requiring runtime configuration  

```
Interfaces:
  - IConfigurationService
    - Get<T>(string key) → T
    - Set<T>(string key, T value) → void
    - Reload() → Task
    - Watch<T>(string key, Action<T> callback) → IDisposable

  - IBalanceTable
    - GetMultiplier(string stat, int tier) → float
    - GetThreshold(string mechanic, string condition) → float
    - GetCurve(string curveName, float input) → float
```

---

#### M04: Logging & Diagnostics Module
**Purpose:** Debug logging, performance profiling, error tracking  
**Public API:** `IDiagnosticsService`  
**Dependencies:** None  
**Dependents:** All modules (optional dependency)  

```
Interfaces:
  - IDiagnosticsService
    - Log(LogLevel level, string message, params object[] args) → void
    - BeginScope(string operationName) → IDisposable
    - Measure(string metricName, Action action) → T
    - ReportError(Exception ex, context) → void
    - GetPerformanceReport() → PerformanceSnapshot
```

---

### Core Engine Layer Modules

#### M05: Time Module
**Purpose:** Game time, tick management, scheduling  
**Public API:** `ITimeService`  
**Dependencies:** None  
**Dependents:** M06, M07-M20  

```
Interfaces:
  - ITimeService
    - CurrentTime → WorldTime
    - DeltaTime → float
    - TickNumber → long
    - Schedule(Action action, float delaySeconds) → ScheduledTask
    - Repeat(Action action, float intervalSeconds) → RepeatingTask
    - Pause() → void
    - Resume() → void
    - SetTimeScale(float scale) → void
```

---

#### M06: World State Module
**Purpose:** Global world state, region management, coordinate system  
**Public API:** `IWorldState`  
**Dependencies:** M05 (Time), M01 (Persistence)  
**Dependents:** M07-M20  

```
Interfaces:
  - IWorldState
    - GetRegion(RegionId id) → IRegion
    - GetAllRegions() → IEnumerable<IRegion>
    - GetEntitiesInRegion(RegionId id) → IEnumerable<IEntity>
    - GetWeather(RegionId id) → WeatherState
    - GetTimeOfDay() → TimeOfDay
    - SubscribeToRegionChanges(Action<RegionChange> callback) → Subscription

  - IRegion
    - Id → RegionId
    - BiomeType → Biome
    - EcologyState → EcologySnapshot
    - ActiveEntities → IReadOnlyList<IEntity>
    - Modifiers → IReadOnlyList<RegionModifier>
```

---

#### M07: Entity Component System (ECS) Module
**Purpose:** Entity management, component storage, system execution  
**Public API:** `IEcsWorld`  
**Dependencies:** M05 (Time), M06 (World State)  
**Dependents:** All game logic systems  

```
Interfaces:
  - IEcsWorld
    - CreateEntity() → EntityId
    - DestroyEntity(EntityId id) → void
    - AddComponent<T>(EntityId id, T component) → void
    - GetComponent<T>(EntityId id) → T?
    - RemoveComponent<T>(EntityId id) → void
    - Query<T1, T2>() → EntityQuery<T1, T2>
    - RegisterSystem<T>(T system) where T : ISystem → void

  - ISystem
    - Initialize() → void
    - Update(float deltaTime) → void
    - OnEntityAdded(EntityId id) → void
    - OnEntityRemoved(EntityId id) → void

  - IEntityQuery
    - Execute(Action<EntityId> action) → void
    - ToArray() → EntityId[]
    - Count() → int
```

---

### Game Logic Layer Modules

#### M08: Simulation Module
**Purpose:** Weather, ecology, physics, environmental systems  
**Public API:** `ISimulationService`  
**Dependencies:** M05, M06, M07  
**Dependents:** M09-M20  

```
Interfaces:
  - ISimulationService
    - UpdateWeather(RegionId id, WeatherState newState) → void
    - StepEcology(float deltaTime) → void
    - ApplyPhysics(EntityId id, PhysicsState state) → void
    - GetSimulationStats() → SimulationSnapshot
```

---

#### M09: NPC Module
**Purpose:** NPC entities, behavior trees, relationship tracking  
**Public API:** `INPCService`  
**Dependencies:** M05-M08, M19 (AI)  
**Dependents:** M10-M20  

```
Interfaces:
  - INPCService
    - CreateNPC(NPCDefinition def) → EntityId
    - GetNPC(EntityId id) → INPC
    - UpdateRelationship(EntityId npcId, EntityId targetId, float delta) → void
    - GetRelationship(EntityId npcId, EntityId targetId) → RelationshipState
    - GetAllNPCsInRegion(RegionId id) → IEnumerable<INPC>

  - INPC
    - Id → EntityId
    - Memory → INPCMemory
    - Personality → PersonalityProfile
    - CurrentGoal → Goal?
    - Relationships → IReadOnlyDictionary<EntityId, RelationshipState>
```

---

#### M10: Knowledge Economy Module
**Purpose:** Knowledge tracking, valuation, scarcity  
**Public API:** `IKnowledgeService`  
**Dependencies:** M05-M09  
**Dependents:** M11, M12  

```
Interfaces:
  - IKnowledgeService
    - RegisterKnowledge(KnowledgeDef def) → KnowledgeId
    - GetKnowledge(KnowledgeId id) → KnowledgeState
    - GetValue(KnowledgeId id, RegionId region) → Decimal
    - OnDiscovery(KnowledgeId id, EntityId discoverer) → void
    - Propagate(KnowledgeId id, RegionId from, RegionId to) → void
    - GetScarcityIndex(KnowledgeId id) → float
```

---

#### M11: Information Propagation Module
**Purpose:** News spread, rumor system, communication networks  
**Public API:** `IInformationService`  
**Dependencies:** M05-M10  
**Dependents:** M12-M20  

```
Interfaces:
  - IInformationService
    - Publish(Information info) → InformationId
    - Subscribe(InformationFilter filter, Action<Information> handler) → Subscription
    - GetPropagationGraph(InformationId id) → PropagationGraph
    - SimulateSpread(InformationId id, float timeHorizon) → SpreadPrediction
```

---

#### M12: Economy & Trade Module
**Purpose:** Markets, prices, trading, resource flow  
**Public API:** `IEconomyService`  
**Dependencies:** M05-M11  
**Dependents:** M13-M20  

```
Interfaces:
  - IEconomyService
    - GetMarket(RegionId id) → IMarket
    - ExecuteTrade(TradeOffer offer) → TradeResult
    - UpdatePrices(RegionId id, PriceUpdate update) → void
    - GetPriceHistory(ItemId id, RegionId region, TimeSpan range) → PriceSeries
    - CalculateValue(ResourceBundle bundle) → Decimal
```

---

#### M13: Skills Module
**Purpose:** Skill tracking, progression, mastery unlocks  
**Public API:** `ISkillsService`  
**Dependencies:** M05-M12  
**Dependents:** M14-M20  

```
Interfaces:
  - ISkillsService
    - GetSkill(EntityId entityId, SkillId skillId) → SkillState
    - ProgressSkill(EntityId entityId, SkillId skillId, float xp) → void
    - CheckBreakthrough(EntityId entityId, SkillId skillId) → BreakthroughResult?
    - UnlockTechnique(EntityId entityId, TechniqueId techniqueId) → void
    - GetAllSkills(EntityId entityId) → IEnumerable<SkillState>
```

---

#### M14: Combat Module
**Purpose:** Real-time combat, targeting, damage calculation  
**Public API:** `ICombatService`  
**Dependencies:** M05-M13  
**Dependents:** M15-M20  

```
Interfaces:
  - ICombatService
    - InitiateCombat(Combatant attacker, Combatant defender) → CombatSession
    - ProcessAttack(AttackCommand cmd) → AttackResult
    - CalculateDamage(Attack attack, Defense defense) → DamageValue
    - ApplyStatusEffect(EntityId target, StatusEffect effect) → void
    - EndCombat(CombatSession session) → void
```

---

#### M15: Crafting Module
**Purpose:** Recipe system, material processing, quality calculation  
**Public API:** `ICraftingService`  
**Dependencies:** M05-M14  
**Dependents:** M16-M20  

```
Interfaces:
  - ICraftingService
    - GetRecipe(RecipeId id) → Recipe
    - CanCraft(EntityId crafter, RecipeId recipe) → CraftabilityCheck
    - ExecuteCraft(CraftCommand cmd) → CraftResult
    - CalculateQuality(CraftContext ctx) → QualityGrade
    - TrackMastery(EntityId crafter, ItemClass itemClass) → MasteryProgress
```

---

#### M16: Magic Module
**Purpose:** Spell system, mana, magical effects  
**Public API:** `IMagicService`  
**Dependencies:** M05-M15  
**Dependents:** M17-M20  

```
Interfaces:
  - IMagicService
    - CastSpell(SpellCommand cmd) → SpellResult
    - GetManaPool(EntityId caster) → ManaState
    - ValidateSpell(SpellDef spell, EntityId caster) → ValidationErrors
    - ApplyMagicalEffect(MagicalEffect effect) → void
```

---

#### M17: Items Module
**Purpose:** Item definitions, inventory, durability, object memory  
**Public API:** `IItemService`  
**Dependencies:** M05-M16  
**Dependents:** M18-M20  

```
Interfaces:
  - IItemService
    - CreateItem(ItemDef def) → ItemId
    - GetItem(ItemId id) → IItem
    - TransferItem(ItemId id, EntityId from, EntityId to) → void
    - ApplyDurabilityDamage(ItemId id, float damage) → void
    - RecordMemory(ItemId id, MemoryFragment fragment) → void
    - GetObjectMemory(ItemId id) → IEnumerable<MemoryFragment>
```

---

#### M18: Failure & Consequences Module
**Purpose:** Failure handling, recovery mechanics, permanent consequences  
**Public API:** `IFailureService`  
**Dependencies:** M05-M17  
**Dependents:** M19-M20  

```
Interfaces:
  - IFailureService
    - EvaluateFailureRisk(ActionContext ctx) → FailureProbability
    - OnFailure(FailureEvent evt) → ConsequenceSet
    - OfferRecovery(RecoveryOption option) → RecoveryResult
    - ApplyPermanentConsequence(EntityId entityId, Consequence consequence) → void
```

---

#### M19: AI Decision Framework Module
**Purpose:** Behavior trees, utility AI, goal selection  
**Public API:** `IAIService`  
**Dependencies:** M05-M18  
**Dependents:** M20  

```
Interfaces:
  - IAIService
    - CreateBehaviorTree(BehaviorTreeDef def) → BehaviorTree
    - SelectAction(AIContext ctx) → ActionSelection
    - UpdateGoal(AIContext ctx, Goal currentGoal) → Goal?
    - EvaluateUtility(ActionDef action, AIContext ctx) → UtilityScore
```

---

#### M20: Scenario & Legacy Module
**Purpose:** Legacy scenarios, trigger conditions, event chains  
**Public API:** `IScenarioService`  
**Dependencies:** M05-M19  
**Dependents:** None (top-level orchestrator)  

```
Interfaces:
  - IScenarioService
    - RegisterScenario(ScenarioDef def) → ScenarioId
    - CheckTriggers(ScenarioId id) → TriggerEvaluation
    - ActivateScenario(ScenarioId id) → ScenarioInstance
    - RecordLegacyEvent(LegacyEvent evt) → void
    - GetActiveScenarios() → IEnumerable<ScenarioInstance>
```

---

### Presentation Layer Modules

#### M21: UI Module
**Purpose:** User interface, HUD, menus, journal  
**Public API:** `IUIService`  
**Dependencies:** M01-M20 (read-only via interfaces)  
**Dependents:** None  

```
Interfaces:
  - IUIService
    - ShowScreen(ScreenType type, ScreenData data) → void
    - HideScreen(ScreenType type) → void
    - UpdateHUD(HUDUpdate update) → void
    - OpenJournal(JournalEntry entry) → void
    - Notify(Notification notification) → void
```

---

#### M22: Audio Module
**Purpose:** Sound effects, music, ambient audio, spatial audio  
**Public API:** `IAudioService`  
**Dependencies:** M05-M08 (for world state)  
**Dependents:** None  

```
Interfaces:
  - IAudioService
    - PlaySound(SoundDef def, Vector3? position) → AudioHandle
    - StopSound(AudioHandle handle) → void
    - SetAmbientTrack(AmbientTrack track) → void
    - UpdateSpatialAudio(AudioHandle handle, Vector3 newPosition) → void
    - SetVolume(AudioChannel channel, float volume) → void
```

---

## Module Communication Patterns

### Pattern 1: Direct Interface Call (Synchronous)
**Use Case:** Immediate response required  
**Example:** Combat damage calculation

```csharp
// CombatModule calls DamageCalculator interface
var damage = _damageCalculator.Calculate(attack, defense);
combatSession.ApplyDamage(damage);
```

### Pattern 2: Event Bus (Asynchronous)
**Use Case:** Decoupled notifications, multiple listeners  
**Example:** World state changes triggering NPC reactions

```csharp
// SimulationModule publishes event
_eventBus.Publish(new WeatherChangedEvent(regionId, newWeather));

// NPCModule subscribes and reacts
_eventBus.Subscribe<WeatherChangedEvent>(evt => {
    _npcService.UpdateNPCBehaviorsForWeather(evt.RegionId, evt.NewWeather);
});
```

### Pattern 3: Command Queue (Deferred Execution)
**Use Case:** Batched operations, rate limiting  
**Example:** Economy price updates

```csharp
// Multiple modules queue price updates
_commandQueue.Enqueue(new UpdatePriceCommand(itemId, newPrice));

// Economy module processes batch per tick
foreach (var cmd in _commandQueue.DequeueBatch()) {
    _economyService.ApplyPriceUpdate(cmd);
}
```

### Pattern 4: Query Object (Complex Filtering)
**Use Case:** Multi-criteria entity selection  
**Example:** Finding NPCs for information propagation

```csharp
var query = _ecsWorld.Query<NPCComponent, KnowledgeComponent>()
    .Where(npc => npc.RegionId == sourceRegion)
    .Where(npc => npc.RelationshipWith(source) > threshold)
    .OrderByDescending(npc => npc.InfluenceScore);

var targets = query.ToArray();
_informationService.Propagate(knowledgeId, targets);
```

---

## Module Initialization Lifecycle

### Phase 1: Infrastructure Boot
```
1. M04 Logging & Diagnostics (first, for error tracking)
2. M03 Configuration (needed by all modules)
3. M01 Persistence (required for data access)
4. M02 Network (if multiplayer enabled)
```

### Phase 2: Core Engine Boot
```
5. M05 Time (fundamental for all simulation)
6. M06 World State (global state container)
7. M07 ECS (entity management foundation)
```

### Phase 3: Game Logic Boot (Order Matters!)
```
8. M08 Simulation (weather, ecology, physics)
9. M09 NPC (needs simulation for environment awareness)
10. M10 Knowledge Economy (needs NPCs for knowledge holders)
11. M11 Information Propagation (needs knowledge system)
12. M12 Economy & Trade (needs knowledge and information)
13. M13 Skills (needs economy for skill valuation)
14. M14 Combat (needs skills for combat calculations)
15. M15 Crafting (needs combat for material acquisition)
16. M16 Magic (needs crafting for reagents)
17. M17 Items (needs all previous for item creation)
18. M18 Failure & Consequences (needs all action systems)
19. M19 AI Decision Framework (needs all behavioral context)
20. M20 Scenario & Legacy (orchestrates all systems)
```

### Phase 4: Presentation Boot
```
21. M22 Audio (can start early for loading sounds)
22. M21 UI (last, depends on all game state being ready)
```

---

## Module Testing Strategy

### Unit Testing (Per Module)
```csharp
// Example: Skills module unit test
[Test]
public void ProgressSkill_WhenXpReached_BreakthroughTriggered() {
    // Arrange
    var skillService = new SkillsService(mockConfig, mockEventBus);
    var player = CreateTestPlayer();
    skillService.InitializeSkill(player.Id, SkillId.Blacksmithing);
    
    // Act
    skillService.ProgressSkill(player.Id, SkillId.Blacksmithing, 1000); // Exactly at threshold
    
    // Assert
    var breakthrough = mockEventBus.ReceivedBreakthrough(player.Id);
    Assert.IsNotNull(breakthrough);
    Assert.AreEqual(BreakthroughTier.Journeyman, breakthrough.Tier);
}
```

### Integration Testing (Module Clusters)
```csharp
// Example: Combat + Skills + Items integration
[Test]
public void CombatAttack_WithEnchantedWeapon_DamageIncludesMagicBonus() {
    // Arrange - Full system stack
    var world = TestWorldBuilder.Create()
        .WithCombat()
        .WithSkills()
        .WithItems()
        .Build();
    
    var attacker = world.CreatePlayerWithWeapon(WeaponType.Sword, enchantment: FireEnchantment);
    var defender = world.CreateDummy(targetDefense: 50);
    
    // Act
    var result = world.CombatService.ProcessAttack(attacker.AttackCommand(defender));
    
    // Assert - Verify cross-module interaction
    Assert.AreEqual(75, result.BaseDamage); // Combat calculation
    Assert.AreEqual(25, result.MagicBonus); // Item enchantment applied
    Assert.IsTrue(attacker.Skills.GetSkill(SwordSkill).Progressed); // Skill progression triggered
}
```

### End-to-End Testing (Full Stack)
```csharp
[Test]
public void FullPlayerJourney_DiscoveryToLegacyRecording() {
    // Arrange - Complete game session
    using var session = TestGameSession.Start();
    var player = session.CreatePlayer();
    
    // Act - Multi-system journey
    player.ExploreRegion(DungeonRegion);
    player.DiscoverKnowledge(AncientRuneKnowledge);
    session.AdvanceTime(days: 7); // Information spreads
    var marketPrice = session.Economy.GetKnowledgeValue(AncientRuneKnowledge);
    player.TradeKnowledge(AncientRuneKnowledge, merchantNPC);
    session.ScenarioService.CheckTriggers(LegacyScenario_Trader);
    
    // Assert - Verify legacy recording across systems
    var legacyEvent = session.ScenarioService.GetRecordedEvents(player.Id)
        .First(e => e.Type == LegacyEventType.KnowledgeTrade);
    Assert.IsNotNull(legacyEvent);
    Assert.Greater(marketPrice, initialPrice); // Economy responded to discovery
}
```

---

## Module Versioning & Compatibility

### Version Schema
```
Format: {major}.{minor}.{patch}

Major: Breaking interface changes (requires dependent module updates)
Minor: New features, backward compatible (safe upgrade)
Patch: Bug fixes only (always safe upgrade)
```

### Compatibility Matrix
| Module | Min Compatible Version | Max Compatible Version | Notes |
|--------|----------------------|----------------------|-------|
| M01 Persistence | 1.0.0 | 1.x.x | Stable interface |
| M07 ECS | 2.0.0 | 2.x.x | Major refactor in v2 |
| M14 Combat | 1.5.0 | 2.0.0 | Balance changes only |

### Deprecation Policy
```
1. Mark interface [Obsolete("Use NewMethod() instead", error: false)]
2. Support both old and new for 2 minor releases
3. After 2 minors, mark error: true
4. After 1 major release, remove entirely
```

---

## Performance Budgets by Module

| Module | CPU Budget (per tick) | Memory Budget | Allocation Limit |
|--------|---------------------|---------------|------------------|
| M05 Time | <0.01ms | <1KB | 0 allocs |
| M07 ECS | <2ms | <100MB | <50 allocs/tick |
| M08 Simulation | <5ms | <200MB | <100 allocs/tick |
| M09 NPC | <3ms | <50MB | <200 allocs/tick |
| M19 AI | <4ms | <30MB | <150 allocs/tick |
| M21 UI | <5ms | <100MB | <100 allocs/frame |

---

## Security Boundaries

### Trusted vs Untrusted Code
```
Trusted (Server-side):
  - M01 Persistence
  - M08 Simulation
  - M10 Knowledge Economy
  - M12 Economy & Trade
  - M18 Failure & Consequences
  - M20 Scenario & Legacy

Untrusted (Client-side, validated):
  - M21 UI
  - M22 Audio
  - Player input handlers

Validation Required:
  - All network messages
  - All persistence writes
  - All economy transactions
  - All combat damage claims
```

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-12-19 | AI Agent | Initial creation based on ChatGPT reference analysis |

---

## Related Documents

- [[System Interaction Matrix]](./system-interaction-matrix.md) - System dependencies and data flows
- [[World Data Schema]](../technical/world-data-schema.md) - Database structure specifications
- [[AI Decision Framework]](../technical/ai-decision-framework.md) - Technical specification for NPC decision-making
- [[Combat System GDD]](./combat-system.md) - Real-time skill-based combat design
- [[Crafting & Professions GDD]](./crafting-professions.md) - Physical crafting system design
