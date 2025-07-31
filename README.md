# Multiplayer Procedural Tower Defence Game — Project Scope

## 🎯 Overview
A real-time, top-down **multiplayer tower defence** game where players control a **playable hero character** in addition to placing automated towers.  
Unlike traditional linear tower defence games, this game features a **procedurally generated world** with goal-oriented progression, encouraging exploration, cooperation, and replayability.

---

## ⚙️ Tech Stack

### 🖥 Frontend
- **Engine**: [Phaser 3](https://phaser.io/) (HTML5 game engine)
- **Map Editor**: [Tiled](https://www.mapeditor.org/) for chunk/prefab design
- **Networking**: WebSockets (via socket.io or native ws)
- **UI Framework**: TailwindCSS (optional) for overlays & menus
- **Packaging**: [Electron](https://www.electronjs.org/) for desktop app

### 🗄 Backend
- **Server Runtime**: Node.js
- **WebSocket Server**: socket.io or native ws server
- **Game State Sync**: Server-authoritative (player positions, waves, tower state)
- **Database**: PostgreSQL or Redis (player progression, stats)
- **Matchmaking/Lobbies**: Simple room system, per-session world state

### 🌐 Deployment
- **Game Hosting**: DigitalOcean
- **Realtime Infrastructure**: Self-hosted or cloud-socket provider (e.g. Socket.IO server)
- **Version Control**: Git (GitHub / GitLab)
- **CI/CD**: GitHub Actions (build/test on push)

---

## 🗺 Gameplay Structure

### Core Loop
1. Players enter a **co-op multiplayer match**
2. The game generates a **procedural world map** with connected zones
3. Players vote or choose paths toward the **final treasure goal**
4. Each zone is a **mini tower defence level**
5. Survive the waves, gather resources, level up, and advance

### World Generation
- Procedural world = series of interconnected **nodes/zones**
- Each zone has:
  - **Randomised path layout**
  - **Themed enemy types**
  - **Environmental modifiers** (fog, fire, ice, etc.)
  - **Unique objectives or bonuses**

---

## 🎮 Gameplay Features

### 👤 Player-Controlled Heroes

Players select from a variety of **hero classes**, each with unique combat abilities and strategic roles. Each class is designed for synergy in co-op gameplay.

#### 🧑‍🚀 Hero Class System
- Each player chooses a class before the match
- Classes are **locked into specific roles**:
  - Only **Engineers** can place, upgrade, and repair towers
  - Other classes focus on combat, crowd control, buffs, etc.
- Players can level up their hero and unlock cosmetics, perks, or variants

#### Example Classes

| Class      | Role           | Towers | Skills                          |
|------------|----------------|--------|----------------------------------|
| Engineer   | Builder         | ✅ Yes | Turret boost, repair beam        |
| Soldier    | DPS             | ❌ No  | Grenade, rapid fire              |
| Arcanist   | AoE Caster      | ❌ No  | Fire wave, freeze aura           |
| Scout      | Mobility/Support| ❌ No  | Dash, radar scan, revive boost  |
| Guardian   | Tank            | ❌ No  | Taunt, damage absorb shield      |

#### Hero Features
- Top-down movement
- Basic attack (projectile or melee)
- Class-specific skills (dash, stun, buff, heal)
- XP/level system (per run and meta progression)

### 🏰 Towers
- **Placement/Upgrades/Repairs** are restricted to **Engineer-class heroes**
- Types: Arrow, Cannon, Magic, Slow, AoE, etc.
- Upgradeable in match by Engineers
- Placement zones only
- Damage types (physical, elemental)

### 🧟 Enemies
- Procedurally selected per zone
- Types: Melee, ranged, fast, tank, flying
- Elemental resistances

### 💰 Economy
- Gold/resource drops from kills
- Used for tower upgrades and skills
- Optional: Shared pool or individual

### 📊 Progression Systems
- **Match-based XP** for all heroes
- Hero-specific unlocks: alternate skills, skins, voice lines
- **Tower unlocks** via Engineer progression
- Perma-perks, skill trees, and seasonal cosmetics

---

## 🧩 Game Modes

### 📌 Core Mode (Seasonal Adventure)
- Procedural world with 5–10 zones
- Final boss or treasure zone
- Replayable with increasing difficulty
- Perma-unlocks via currency or XP

### ⚔️ Future Modes
- **Versus Mode**: 2 teams defend different paths, send mobs to opponents
- **Endless Mode**: Single zone, infinite waves
- **Guild Events**: Group challenges with leaderboard rewards

---

## 🎨 UI / UX Components
- Lobby screen (join/create match)
- World map UI (node connections, difficulty indicators)
- Match HUD (player info, gold, towers, minimap)
- Tower placement & upgrade UI
- Post-match summary screen

---

## 📦 Planned Features

### ✅ MVP
- [ ] Basic multiplayer with room-based connection
- [ ] Procedural world map generation
- [ ] Player-controlled hero
- [ ] Tower placement and upgrades
- [ ] Enemy waves with scaling difficulty
- [ ] Match-based progression

### 🚀 Phase 2
- [ ] Meta progression (XP, tower unlocks, skins)
- [ ] Battlepass and seasonal content system
- [ ] Server-side anti-cheat & validation
- [ ] Cross-platform desktop packaging (Electron)

### 💡 Nice-to-Haves
- [ ] Emotes, pets, and companion systems
- [ ] In-game map voting (branching path)
- [ ] Twitch / Discord integration
- [ ] Community-built map chunks (Tiled plugin)
- [ ] Procedural story events

---

## 🔐 Future Monetisation Ideas
- Battlepass (seasonal unlocks)
- Cosmetic tower skins / hero skins
- Pets or avatars
- Currency packs (non-pay-to-win)
- Merch integration

---

## 👥 Collaboration Plan

### Git Structure

    /client   # Phaser frontend
    /server   # Node.js + WebSocket server
    /shared   # Shared game definitions (enums, maps, etc.)
    /assets   # Sprites, audio, maps (Tiled)
    /docs     # Design docs, planning

### Contribution Guidelines
- Use Git branches for features
- PRs with linked issues

---

## 🧠 Notes
- Tiled can still be used for **modular prefab design** (e.g., path segments)
- Procedural levels can be **chunk-based**, not 100% random
- Networking sync must be prioritised early for smooth co-op
