# 13. Economy & Trade System

## 1. Core Philosophy: Physical, Player-Driven, Sustainable

The economy is a **living simulation** of supply, demand, production, and consumption—not a static shop interface. It is almost entirely player-driven, with NPCs acting as producers, consumers, and facilitators rather than infinite gold sources.

**Key Principles:**
*   **Physical Resources:** All goods exist as physical items in the world with weight, volume, and degradation.
*   **Finite Supply:** Nodes deplete; over-harvesting causes scarcity.
*   **Dynamic Value:** Prices fluctuate based on real-time local supply/demand, not fixed tables.
*   **No Gold Sinks:** Currency is primarily for player-to-player trade; NPCs use barter/reputation.
*   **Sustainability First:** Built-in mechanics prevent monopolies, bot exploitation, inflation, and excessive grind.

---

## 2. Resource Ecology & Scarcity

Resources are part of the world simulation, subject to depletion, recovery, and discovery.

### 2.1 Resource Types
| Type | Examples | Scarcity | Regeneration |
|------|----------|----------|--------------|
| **Common** | Wood, Stone, Iron, Wheat | Abundant | Fast (days) |
| **Uncommon** | Silver, Herbs, Leather | Regional | Moderate (weeks) |
| **Rare** | Gold, Mithril, Rare Plants | Limited Zones | Slow (months) |
| **Legendary** | Dragonbone, Star Metal, Phoenix Feathers | Unique/Event-Based | Very Slow / One-time |

### 2.2 Depletion & Recovery Mechanics
*   **Yield Decay:** Repeated harvesting reduces node output by 10-20% per cycle until exhaustion.
*   **Exhaustion State:** Over-mined/over-harvested nodes become inactive for weeks/months.
*   **Natural Recovery:** Nodes slowly regenerate over time; speed depends on biome health and season.
*   **Player Intervention:** Specific roles can accelerate recovery:
    *   *Herbalists* replant flora, enrich soil.
    *   *Geologists* stabilize mine shafts, locate new veins.
    *   *Druids* restore ecosystem balance after over-harvesting.
*   **New Discoveries:** Geological shifts, earthquakes, or deep exploration can reveal previously unknown resource deposits, breaking regional monopolies.

### 2.3 Synthetic Alternatives
To prevent permanent lockout from rare resources:
*   **Crafted Substitutes:** High-skill crafters can create "Synthetic [Resource]" using common materials + complex recipes.
    *   Example: Synthetic Mithril (Iron + Crystal Dust + Alchemical Process).
    *   Quality: 70-85% of natural version; functional for most purposes.
*   **Research Requirement:** Recipes for synthetics must be discovered through experimentation or ancient texts.

---

## 3. Production & Crafting Integration

Resources flow from gatherers → processors → crafters → consumers.

### 3.1 Production Chain
```
Raw Node (Miner/Logger/Farmer)
       ↓
Refined Material (Smelter/Miller/Tanner)
       ↓
Component (Blacksmith/Carpenter/Alchemist)
       ↓
Finished Good (Weapon/Armor/Potion/Structure)
       ↓
Consumer (Player/NPC/Guild)
```

### 3.2 Quality Tiers
Item quality affects price, durability, and performance:
*   **Poor:** Rushed crafting, low skill, bad tools.
*   **Standard:** Average materials, competent crafter.
*   **Fine:** Good materials, skilled crafter, proper environment.
*   **Masterwork:** Rare materials, expert crafter, optimal conditions, enchantments.
*   **Legendary:** Unique materials, legendary crafter, special events/rituals.

### 3.3 Crafter Reputation
Crafters build personal reputations affecting demand:
*   **Signature Styles:** Crafters known for specific traits (e.g., "Lightweight Armor," "Fire-Resistant Blades").
*   **Brand Value:** Items signed by renowned crafters command premium prices.
*   **Apprenticeships:** Master crafters can train apprentices, spreading techniques (or keeping secrets).

---

## 4. Trade & Distribution

Goods move through the world via physical transport, creating logistics opportunities and risks.

### 4.1 Trade Methods
| Method | Capacity | Speed | Risk | Cost |
|--------|----------|-------|------|------|
| **Player Carry** | Low | Medium | Medium (creatures/bandits) | Stamina |
| **Pack Animals** | Medium | Slow | Medium | Feed/Maintenance |
| **Carts/Wagons** | High | Very Slow | High (roads only) | Fuel/Repairs |
| **Ships** | Very High | Slow (water only) | High (storms/pirates) | Crew/Supplies |
| **Caravans (Guild)** | Massive | Slow | Low (guards) | Shared Cost |

### 4.2 Trade Routes & Infrastructure
*   **Emergent Routes:** Frequently traveled paths develop into recognized trade routes.
*   **Worn Path Bonus:** Established routes reduce stamina cost, travel time, and random encounters.
*   **Player-Built Infrastructure:** Guilds can construct:
    *   **Roads/Bridges:** Reduce travel time, enable carts.
    *   **Waystations:** Provide rest, repairs, storage along routes.
    *   **Ports/Docks:** Enable efficient ship loading/unloading.
*   **Toll Systems:** Infrastructure owners can charge tolls, creating revenue streams.

### 4.3 Contract System
Players can outsource logistics:
*   **Hauling Contracts:** Post jobs offering payment for transporting goods between points.
*   **Escort Contracts:** Hire guards to protect valuable shipments from bandits/creatures.
*   **Supply Contracts:** Agree to deliver regular quantities of goods to NPCs/guilds at fixed prices.

---

## 5. Pricing & Market Dynamics

Prices are determined by local supply/demand simulations, not static tables.

### 5.1 Dynamic Pricing Factors
*   **Local Supply:** Abundance lowers prices; scarcity raises them.
*   **Local Demand:** NPC populations consume goods; high demand raises prices.
*   **Seasonality:** Food cheap after harvest, expensive in winter; warm clothing vice versa.
*   **Event Impact:** Wars spike weapon prices; plagues increase medicine demand.
*   **Transport Cost:** Remote locations have higher prices due to import difficulty.

### 5.2 Regional Price Variations
```
Example: Iron Ore
- Mining Town: 5 gold (abundant)
- Coastal City: 12 gold (imported)
- Mountain Village: 25 gold (scarce + transport cost)
- War Zone: 40 gold (urgent demand)
```

### 5.3 Market Information Asymmetry
*   **No Global Auction House:** Players must physically visit markets or rely on rumors/travelers.
*   **Price Discovery:** Merchants share price info slowly; players can profit from arbitrage (buy low, sell high across regions).
*   **Rumor System:** Traders gossip about shortages/surpluses, but information may be outdated or false.

---

## 6. Sustainability & Anti-Exploit Mechanics

Built-in systems ensure long-term fairness and viability.

### 6.1 Preventing Monopolies (Resource Regeneration)
**Problem:** First-mover advantage could allow early players/guilds to hoard all rare nodes.

**Solutions:**
*   **Depletion & Recovery:** Over-mining causes temporary exhaustion; nodes naturally recover or require player intervention to rejuvenate.
*   **New Vein Discovery:** Geological shifts or exploration reveal new deposits in unexpected locations.
*   **Synthetic Alternatives:** Crafted substitutes reduce dependency on scarce natural resources.
*   **Antitrust Mechanics:** Guilds controlling >X% of a resource face escalating taxes or NPC merchant strikes (refusal to trade).

### 6.2 Countering Bot Exploitation (Human Verification)
**Problem:** Automated scripts could farm resources 24/7, crashing markets.

**Solutions:**
*   **Diminishing Returns:** Continuous action yields exponentially less profit; efficiency resets after diverse activities or rest.
*   **Stamina/Fatigue System:** Physical actions consume stamina that regenerates slowly; bots hitting cap become inefficient.
*   **Randomized Micro-Events:** Harvesting triggers mini-challenges (tool jam, weather shift, creature disturbance) requiring contextual human reaction.
*   **Reputation Gates:** High-value markets require high reputation earned through complex social interactions difficult to automate.

### 6.3 Controlling Inflation (Barter & Sinks)
**Problem:** Fixed NPC rewards flood market with currency, devaluing player effort.

**Solutions:**
*   **NPC Barter System:** Most NPCs trade goods/services for **Reputation**, **Specific Items**, or **Favors**—not gold. Gold is primarily player-to-player.
*   **Dynamic Money Sinks:**
    *   **Upkeep:** Housing, guild halls, equipment require maintenance fees.
    *   **Taxation:** Territories levy taxes on trade routes; funds used for public works or embezzled.
    *   **Luxury Consumption:** Cosmetics, titles, non-essential services drain excess currency without affecting power.
*   **No "Quest Gold":** Task rewards are gear, knowledge, reputation, or unique items—not raw currency.

### 6.4 Reducing Logistics Grind (Infrastructure & Assistance)
**Problem:** Hauling goods becomes tedious busywork.

**Solutions:**
*   **Player-Built Infrastructure:** Roads, bridges, waystations reduce travel time/fatigue for all users.
*   **Contract System:** Players can accept paid hauling jobs, creating a logistics service layer.
*   **Mounts & Vehicles:** Carts, ships, pack animals increase capacity but require fuel/maintenance.
*   **Trade Route Bonuses:** Established routes gain reduced stamina cost, fewer encounters, faster travel.

---

## 7. Economic Events & Disruptions

The economy reacts dynamically to world events.

| Event | Economic Impact |
|-------|-----------------|
| **War** | Weapon/armor prices spike; food shortages; trade routes blocked |
| **Natural Disaster** | Destroy crops/mines; sudden scarcity; inflation in affected region |
| **Plague** | Workforce reduction; halted production; medicine demand surge |
| **Festival** | Luxury goods, decorations, food demand spikes temporarily |
| **Resource Discovery** | New vein crashes local prices; creates export boom |
| **Bandit Surge** | Transport costs rise; insurance premiums; route abandonment |
| **Political Embargo** | Specific goods banned; black markets emerge; smuggling profits |

---

## 8. Player Roles in Economy

Players specialize to drive economic activity:

| Role | Function | Value Add |
|------|----------|-----------|
| **Gatherer** | Extract raw resources | Supply foundation |
| **Processor** | Refine materials | Enable crafting |
| **Crafter** | Create finished goods | Utility/Power |
| **Merchant** | Buy low, sell high | Market efficiency |
| **Transporter** | Move goods safely | Logistics |
| **Financier** | Fund operations, loans | Capital liquidity |
| **Speculator** | Predict trends, hoard | Market signaling |

---

## 9. Success Metrics

Economy health measured by:
*   **Trade Volume:** Total goods moved between regions weekly.
*   **Price Stability:** Variance in core commodity prices (too stable = stagnant; too volatile = chaotic).
*   **Participation Rate:** % of active players engaging in economic activities.
*   **New Entrant Viability:** Can new players find profitable niches despite established players?
*   **Crisis Recovery Time:** How quickly markets stabilize after major disruptions.

---

## 10. Technical Considerations

*   **Database:** Track every item's origin, quality, owner history.
*   **Simulation Tick:** Run supply/demand calculations hourly (game time).
*   **Anti-Cheat:** Server-side validation of resource nodes, transaction limits.
*   **Persistence:** Economic state survives server restarts; no resets.

---

## 11. Integration Points

*   **Knowledge Economy:** Trade maps, recipes, market intel.
*   **Crafting System:** Resource quality affects final product.
*   **NPC System:** NPCs consume/produce goods; remember fair/unfair traders.
*   **World Simulation:** Weather, seasons, disasters affect production/transport.
*   **Legacy Scenarios:** Economic achievements (e.g., "First to establish transcontinental trade") recorded in history.

---

## 12. Design Examples

### Scenario 1: Iron Shortage
*   **Trigger:** Major war consumes iron stockpiles in Northern Kingdom.
*   **Effect:** Iron prices triple; miners rush to northern mines; bandits target shipments.
*   **Opportunity:** Players smuggle iron from south; crafters switch to bronze alternatives; merchants profit from arbitrage.

### Scenario 2: Monopoly Broken
*   **Situation:** Guild A controls 90% of Mithril mines, charging exorbitant prices.
*   **Intervention:** Geologist player discovers new Mithril vein in unclaimed territory.
*   **Result:** Prices drop 40%; Guild A loses influence; new mining town emerges.

### Scenario 3: Bot Mitigation
*   **Observation:** Player farms herbs 18 hours/day with perfect efficiency.
*   **System Response:** Diminishing returns activate (10% yield); random pest infestation event triggers.
*   **Outcome:** Bot profitability drops below threshold; human farmers remain competitive.
