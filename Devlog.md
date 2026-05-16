# Devlog - Sky Era

---

## Tech Stack

- **Engine:** Unreal Engine 5.4
- **Logic:** 99% Blueprints / 1% C++.
	- I used **C++** as the "foundation" to expose engine features and set up the **Gameplay Ability System (GAS)** architecture.  	
- **Tools:** Visual Studio

---

## Core Systems

- **Skill & Attributes:** Twelve character abilities and ten attributes are fully driven by GAS.
- **Inventory:** system made using Data Tables for item definitions. Supports Drag & Drop operation.
- **Quest:** Linear quest system with three types of tasks: kill, interact, collect item.
- **Navigation:** NavMesh system with pathfinding to prevent characters from getting stuck on geometry.
- **Save/Load:** A serialization system handling character progression, location, inventory, action bars and quest progress across play sessions.
- **Enemy AI:** Created an AI behaviour in an MMORPG style, using **Behaviour trees**. There are three types of enemies: aggresive ranged that uses EQS, neutral melee and agressive melee.

---

## Engineering Highlights

- **GAS Integration:** Implemented Epic's GAS framework within a predominantly Blueprint-driven project to handle Gameplay Attributes, Abilities, Effects, and Cues.
- **Environment:**
	- Manually sculpted landscape with basic tools. For bodies of water, I used the official **Water** plugin as well as planes with water materials for specific areas.
	- Fog is adjusted to match the view distance quality.
- **Optimization:**
    - Applied foliage culling and **Cull Distance Volume** to ensure vegetation and other environment objects arent rendered at certain distance from the player.
    - Implemented a **custom render range** logic for enemies, NPCs, and items to keep the frame rate more stable.
- **Pattern Designs:** 
    - **Component Pattern:** I followed a modular approach by moving Inventory and Quest handling into **Actor Components**.
    - **UI Architecture:** I implemented a separation between data and UI using the **Model-View-ViewModel (MVVM)** pattern and a custom **Widget Controller** to handle incoming experience points.
- **Loading Screen:** Integrated the **Async Loading Screen** plugin to manage background level streaming. This ensures that the game remains responsive during heavy data transitions.

---

## Generative AI Utilization

Generative AI tools were used for:
- Main menu and loading screen images
- NPC portraits
- Two in-game 3D models

---

## Project Vision

There are no strict deadlines, but the following represent the long-term vision for the game.

**Long-Term Goal - Multiplayer Integration:**

The ultimate vision is to transition from a single-player experience into a massively multiplayer environment, requiring significant architectural refactoring:
- **Client-Server Architecture:** Refactoring core Blueprint logic to support **Server Authority**. This involves moving gameplay-critical decisions to the server to prevent cheating and ensure a synchronized world state.
- **Replication:** Implementing robust networking layer using Unreal's **RPCs (Remote Procedure Calls)**.
- **Backend Scalability:** Designing a scalable networking infrastructure to support a high volume of concurrent players
- **C++ Migration:** Porting performance-heavy systems and core networking logic from Blueprints to **C++**. This will optimize CPU overhead and provide better control over memory management during high player density.
- **Visual Evolution:** Replacing generative AI placeholders and marketplace assets with **custom-made 3D models** to suit the projects needs and establish a unique and cohesive art style.
- **Refactoring existing systems and expanding content of the game**:
	- **Grid-Based Inventory:** Transitioning from the current slot based system to a **coordinate based grid**, where items have varying dimensions. This will require implementing spatial management logic.
    	- **Enhanced Quest Framework:** Refactoring the quest system to support an **unlimited number of tasks** within a single mission, allowing for much more complex and multi-stage objectives.
	- **World-Building & Lore:** Developing the game's **Lore** and deep backstory through quest system.
	- **World Expansion:** Designing and implementing multiple new maps.
