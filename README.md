# Object-Oriented Desert Expedition Simulator

## Executive Summary
This project is a **turn-based simulation engine** developed in **C++17**, designed to model a complex economic and survival environment within a terminal interface.

The system leverages advanced **Object-Oriented Programming (OOP)** principles to create a dynamic world where user-controlled trading caravans coexist with autonomous hostile agents (Barbarians). The simulation emphasizes resource management (water, crew, cargo), procedural event generation, and polymorphic entity behaviors.

## Technical Architecture
The core strength of this project lies in its robust software design:

* **Polymorphic Entity System:** All map objects—Cities, Caravans, and Items—inherit from abstract base classes, allowing the game engine to treat diverse entities uniformly while executing unique logic.
* **Memory Safety:** The project eschews raw pointers in favor of **Smart Pointers (`std::unique_ptr`, `std::shared_ptr`)**, ensuring automatic memory management and leak prevention.
* **Buffer-Based Rendering:** To prevent flickering in the console, the visual output utilizes a double-buffering technique, rendering the grid state to a virtual buffer before flushing it to the terminal.
* **Autonomous AI:** Non-player characters (Barbarians) and user caravans (in auto mode) utilize decision-making algorithms to navigate the terrain and engage targets without human intervention.

## Gameplay Mechanics

### 1. The World & Cities
The map is a grid-based wasteland dotted with **Cities**. These serve as economic hubs where players can:
* **Trade:** Monetize cargo collected during expeditions.
* **Recruit:** Replenish crew numbers (`tripul`).
* **Resupply:** Purchase vital resources.

### 2. The Caravan System
Caravans are the primary mobile units, distinct in their stats and capabilities:
* **Commerce:** Optimized for cargo capacity; high load, low defense.
* **Military:** Heavily armed units designed for territory defense and barbarian suppression.
* **Hestia (Secret):** A specialized, high-endurance unit designed for deep exploration.
* **Barbarians:** Hostile AI agents that roam the map autonomously, aggressively pursuing player units.

### 3. Dynamic Map Objects (Items)
Procedurally generated entities appear throughout the simulation, triggering polymorphic events upon contact:
* **Pandora’s Box:** Triggers a randomized global effect (buff or debuff).
* **Treasure Chest:** Grants gold or resources.
* **Mine:** Inflicts hull damage to the traversing caravan.
* **Cage:** Immobilizes the caravan for a set number of turns.
* **Oasis:** Instantly restores water reserves to maximum capacity.

### 4. Combat & Survival Logic
* **Battle Mechanics:** Combat is triggered automatically when opposing factions (Player vs. Barbarian) occupy the same coordinate. Results are calculated based on crew size and caravan tier.
* **Resource Decay:** Movement consumes water. Running dry results in crew death and eventual caravan loss.
* **Environmental Hazards:** Sandstorms can be triggered, obscuring vision and damaging units in the affected radius.

---

## Command Interface
The simulation is controlled via a command-line parser supporting the following directives:

### Simulation Control
* `config <file>` : Initializes the grid using a specific map configuration file.
* `prox <n>` : Advances the simulation state by `n` ticks (turns).
* `terminar` : Gracefully shuts down the engine and cleans up memory.

### Unit Management
* `compraC <city> <type>` : Purchase a unit (Types: **C**ommerce, **M**ilitary, **S**ecret).
* `tripul <id> <n>` : Recruit `n` crew members for caravan `<id>`.
* `vende <id>` : Liquidate all cargo currently held by caravan `<id>`.
* `move <id> <dir>` : Manual movement (Directions: **D**-Right, **E**-Left, **C**-Up, **B**-Down).
* `auto <id>` / `stop <id>` : Toggle autonomous AI pilot for a specific caravan.

### Environmental & Admin
* `barbaro <y> <x>` : Force-spawn a Barbarian unit at the specified coordinates.
* `areia <y> <x> <r>` : Summon a sandstorm at `(y,x)` with radius `r`.

---

## Build & Execution
The project is structured for **CMake**.

* **IDE:** Developed primarily in **CLion** (JetBrains).
* **Setup:** Import the root folder into CLion. The IDE will detect the `CMakeLists.txt` file automatically.
* **Compiler:** Requires a C++ compiler supporting the **C++17** standard or higher.

---

## Academic Context
This software was engineered as the final capstone project for the **"Object-Oriented Programming"** course (2024/2025).

**Team Size:** 2 Members
**Final Evaluation:** 9.5 / 10
