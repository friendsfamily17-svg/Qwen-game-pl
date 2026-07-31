# Information Propagation System

## 1. Core Philosophy

**"News travels at the speed of feet, not servers."**

In most MMOs, when a player kills a dragon, the entire server instantly knows via a global chat log or achievement popup. In our Living World, information is **physical, local, and imperfect**.

Knowledge propagates through the world like a ripple in a pond:
- It starts at the source (the event).
- It spreads through witnesses, travelers, merchants, and bards.
- It degrades, mutates, or gets lost over distance and time.
- Different regions hear different versions of the truth.

This system turns **information flow** into a gameplay mechanic. Players can intercept messengers, spread disinformation, hoard secrets, or become famous (or infamous) in one region while remaining unknown in another.

---

## 2. The Propagation Model

Information does not teleport. It moves through a **Network of Agents**.

### 2.1 The Ripple Zones

| Zone | Radius | Who Knows? | Detail Level | Delay |
| :--- | :--- | :--- | :--- | :--- |
| **Ground Zero** | 0–50m | Direct Witnesses | 100% Accurate | Instant |
| **Local** | Village/Town | Residents, Guards | 90% Accurate | Minutes |
| **Regional** | Nearby Settlements | Travelers, Merchants | 70% Accurate | Hours |
| **National** | Kingdom Capital | Nobles, Spies, Bards | 50% Accurate | Days |
| **Global** | Entire Continent | Legends, Rumors | <20% Accurate | Weeks/Months |

### 2.2 The Agents of Spread

Information moves only when **entities move**.

1.  **Witnesses**: Players or NPCs who saw the event. They tell others at camps, inns, or gatherings.
2.  **Travelers**: NPCs moving between points A and B. They carry news to the next settlement.
3.  **Merchants**: High-mobility agents. They prioritize trade news but spread major events quickly.
4.  **Bards/Storytellers**: Specialized agents. They amplify stories, adding flair but reducing accuracy.
5.  **Messengers/Couriers**: Hired by factions to deliver specific news rapidly (expensive).
6.  **Refugees**: Fleeing disasters, they bring urgent, emotional news (high impact, often panicked/exaggerated).

---

## 3. Information Attributes

Every piece of news carries metadata that changes as it spreads.

### 3.1 Accuracy (0–100%)
- Starts at 100% for witnesses.
- Decreases with each "hop" between agents.
- Affected by the agent's **Perception** and **Honesty** stats.
- *Example*: "A dragon attacked" might become "A giant lizard was seen" or "The sky burned."

### 3.2 Urgency (Low/Medium/High/Critical)
- Determines how fast agents prioritize spreading it.
- **Critical**: Plague, Invasion, Dragon Sighting. (Spreads 5x faster).
- **Low**: New shop opening, Minor festival. (Spreads slowly).

### 3.3 Bias/Spin
- Agents modify news based on their faction or personality.
- *Guard*: "The hero bravely defeated the beast."
- *Thief*: "The fool fought a dragon and barely survived."
- *Merchant*: "Dragon scales are now valuable; buy low!"

### 3.4 Source Credibility
- News from a known Hero or Scholar spreads faster and retains higher accuracy.
- News from a "Crazy Hermit" spreads slower and is treated as rumor.

---

## 4. Player Interaction Mechanics

Players are not just observers; they are **active nodes** in the network.

### 4.1 Spreading Information
- **Gossip**: Talk to NPCs at inns/camps to share what you know.
- **Proclamation**: Pay a town crier or bard to announce specific news (costs gold).
- **Written Word**: Publish a book, map, or newsletter. Physical items travel independently.
- **Faction Report**: Report directly to faction leaders for immediate regional awareness.

### 4.2 Intercepting Information
- **Ambush Messengers**: Stop couriers to prevent news from reaching a rival city.
- **Bribe Bards**: Pay them to change the story or stop singing about an event.
- **Silence Witnesses**: Intimidate or pay witnesses to keep an event secret (creates a "Secret" status).

### 4.3 Disinformation Campaigns
- Plant false rumors to mislead rivals or distract enemies.
- *Risk*: If caught, reputation plummets. If successful, enemies may waste resources responding to fake threats.

### 4.4 Information Hoarding
- Keep a discovery (e.g., a rare mine location) completely secret.
- Sell the info privately to the highest bidder before it becomes public knowledge.
- Once public, the value drops to zero.

---

## 5. The Rumor Mill System

Not all information is true. The world generates **Dynamic Rumors**.

### 5.1 Rumor Generation
- Based on partial data: "Player X entered the Forbidden Cave." → Rumor: "Player X found the Lost Crown."
- Based on fear: "Cattle missing." → Rumor: "Vampires in the woods."
- Based on hope: "Strange lights in the sky." → Rumor: "The Phoenix has returned."

### 5.2 Verification Mechanics
- Players can investigate rumors to confirm or debunk them.
- **Confirmed**: Becomes "Fact" in the player's journal. Value increases.
- **Debunked**: Becomes "Myth." Spreads as a cautionary tale.
- **Unverified**: Remains a rumor. Value fluctuates.

### 5.3 The "Telephone Game" Effect
As news travels, it mutates.
- **Event**: Player killed a Wolf.
- **Hop 1**: Player killed a Giant Wolf.
- **Hop 2**: Player fought a Werewolf.
- **Hop 3**: A Werewolf is hunting the village.
- **Result**: Players arrive to find a normal wolf, confused by the hype. Or, the panic attracts actual hunters.

---

## 6. Regional Knowledge States

Knowledge is **not global**. It is stored per Region/Settlement.

| Region | Knowledge State | Example Impact |
| :--- | :--- | :--- |
| **Village A** | "Hero saved us!" | Prices -20%, Free lodging, Guards salute. |
| **Village B** | "Who?" | No effect. Player is a stranger. |
| **Capital City** | "Rumor of a hero." | Quest offers available, Nobles curious. |
| **Enemy Territory** | "The intruder." | Guards hostile, Prices +50%, Assassins sent. |

*Implication*: A player can be a legend in the North and a nobody in the South. This encourages travel and re-establishing reputation.

---

## 7. Integration with Other Systems

### 7.1 Legacy Scenarios
- Some scenarios trigger **only** if information reaches a certain threshold.
- *Example*: "The King hears of your deed" → Invitation to the palace.
- *Example*: "The Cult learns your name" → Assassination attempt.

### 7.2 Economy
- Market prices react to news.
- "Dragon spotted in Mines" → Ore prices skyrocket, Weapon prices drop (miners fled).
- "New trade route discovered" → Exotic goods flood the market, prices drop.

### 7.3 NPC Memory
- NPCs reference recent news in dialogue.
- "Did you hear about the bridge collapse?"
- "They say you're the one who did it!"

### 7.4 Ancient Entities
- Legendary creatures may react to their own fame.
- If too many people talk about the "Sleeping Titan," it might wake up early due to the disturbance.

---

## 8. Technical Implementation Strategy

### 8.1 Data Structure: The News Packet
```json
{
  "id": "event_12345",
  "type": "dragon_sighting",
  "origin_location": [x, y, z],
  "timestamp": 1678901234,
  "truth": { "actor": "PlayerOne", "action": "killed", "target": "Red Dragon" },
  "current_version": { "text": "A demon burned the forest!", "accuracy": 0.45 },
  "spread_radius": 5000, // meters
  "urgency": "CRITICAL",
  "known_by_factions": ["Kingdom A", "Mages Guild"]
}
```

### 8.2 Simulation Tick
- Run propagation logic every **Game Hour**.
- Calculate movement of "News Carriers" (NPCs/Players).
- Update regional knowledge states.
- Decay old news (unless it's historic).

### 8.3 Optimization
- Do not simulate every individual conversation.
- Use **Flow Fields** for news spread: Treat news like a fluid spreading across a graph of settlements.
- Only calculate detailed mutation when a player interacts with a specific NPC.

---

## 9. Design Examples

### Scenario A: The Secret Discovery
- **Player** finds a rare herb patch.
- **Action**: Tells no one. Marks it on personal map.
- **Result**: Only the player benefits. High profit.
- **Risk**: If seen by an NPC herbalist, news begins to spread.

### Scenario B: The False Flag
- **Player** wants to lower iron prices in City X.
- **Action**: Spreads rumor that "Iron Mine Y has collapsed."
- **Mechanic**: Merchants believe rumor, dump iron stockpiles.
- **Result**: Player buys iron cheap. Later, reveals the mine is fine, sells high.
- **Consequence**: If traced back, merchant guild bans the player.

### Scenario C: The Unwitting Celebrity
- **Player** saves a village from bandits quietly.
- **Event**: A traveling bard witnesses it.
- **Propagation**: Bard sings song in Capital.
- **Result**: Player arrives in Capital to find fans, but also jealous rivals challenging them.

---

## 10. Failure & Risks

- **Information Overload**: Too many rumors clutter the UI.
  - *Fix*: Filter by relevance/distance. Only show rumors affecting current region.
- **Confusion**: Players frustrated by inaccurate info.
  - *Fix*: Make verification a core gameplay loop (Journal tracks "Verified" vs "Rumor").
- **Exploits**: Spamming false rumors.
  - *Fix*: Diminishing returns on credibility. Repeated lies make the player an "Unreliable Source."

---

## 11. Success Metrics

- **Rumor Velocity**: How long does it take for news to cross the map?
- **Verification Rate**: How often do players investigate rumors?
- **Regional Variance**: Are players experiencing different realities in different zones?
- **Player-Driven Stories**: Are players discussing "Have you heard about...?" in community channels?

---

## 12. Future Expansion

- **Magical Communication**: Unlockable spells/items (e.g., "Whispering Stone") that allow instant long-distance communication (rare/expensive).
- **Censorship**: Governments blocking news routes.
- **Propaganda Wars**: Factions competing to control the narrative.
- **Historical Archives**: Libraries storing verified history vs. popular myths.

---

## 13. Summary

The **Information Propagation System** ensures that knowledge feels physical and valuable. It prevents the world from feeling like a single, omniscient instance. By making news travel slowly and imperfectly, we create opportunities for espionage, trade, exploration, and genuine surprise.

**"In this world, being the first to know is power. Being the only one to know is wealth."**
