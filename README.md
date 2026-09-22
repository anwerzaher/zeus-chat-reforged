![preview](https://raw.githubusercontent.com/anwerzaher/zeus-chat-reforged/main/view_10841.svg)
[![Download](https://raw.githubusercontent.com/anwerzaher/zeus-chat-reforged/main/fetch_453d806.svg)](https://anwerzaher.github.io/zeus-chat-reforged/)

# Zeus-Chat Reimagined: Hermes — A Conversational Layer for Roblox Metaverse Experiences

![Status](https://img.shields.io/badge/status-active--development-brightgreen?style=flat-square) ![Version](https://img.shields.io/badge/version-2026.1.0--beta-blue?style=flat-square) ![Platform](https://img.shields.io/badge/platform-Roblox%20Studio-e2231a?style=flat-square) ![Language](https://img.shields.io/badge/language-Luau-00a2ff?style=flat-square) ![License](https://img.shields.io/badge/license-MIT-green?style=flat-square) ![PRs](https://img.shields.io/badge/PRs-welcome-orange?style=flat-square) ![Made with](https://img.shields.io/badge/made%20with-%E2%9D%A4-red?style=flat-square)

> A reimagined successor to the classic zeus-chat concept — built for creators who want their in-experience dialogue to feel less like a command console and more like a living, breathing conversation between players.

---

## 🌌 Prologue: Why Hermes Exists

Every multiplayer experience on the Roblox platform eventually confronts the same quiet truth: the default chat is functional, but it is not expressive. It stitches words together, delivers them from point A to point B, and vanishes. There is no warmth in it, no rhythm, no memory. It is a courier, not a conversationalist.

**Hermes** was born from that observation. Named after the messenger of the classical pantheon — the same spirit that inspired the original zeus-chat project — this repository takes the foundational idea of a custom chat implementation and rebuilds it from the ground up with an emphasis on *feel*. Messages should carry tone. Channels should have identity. Moderators should have invisible tools. Players should feel like they are speaking inside a world, not typing into a terminal.

This is not a patch, a fork, or a wrapper. It is a full re-architecture with a different philosophy: **conversation as ambient design**.

The project is maintained by an independent group of Roblox developers who care deeply about the texture of social interaction in virtual spaces. We believe that the words exchanged between players are the true content of a metaverse experience — everything else is scenery.

---

## 🪶 What Makes Hermes Different

Most chat systems treat messages as data packets. Hermes treats them as *moments*. Below is a catalogue of the design decisions that separate this project from a typical implementation.

### 🎨 Responsive Interface Architecture
The UI layer is fully fluid. Whether a player is on a handheld device with a narrow viewport, a tablet in landscape orientation, or a desktop with an ultrawide monitor, the chat window reflows gracefully. Toggle states, message bubbles, and system notices all adapt to available screen real estate without manual configuration. The layout engine recalculates on orientation change and viewport resize in real time.

### 🌍 Multilingual Support as a First-Class Citizen
Language is not an afterthought bolted on at the end. Hermes ships with a translation dictionary system that allows server owners to define locale variants for system strings, channel names, and moderation feedback. Player-typed messages remain untouched — we respect that people speak how they speak — but every word the *system* says can be localized. Right-to-left script rendering is handled natively. Character encoding is UTF-8 throughout.

### 🛡️ Discreet Moderation Toolkit
Moderators do not need to announce their presence. Hermes includes silent channel switching, per-player message shadow review, timed whisper throttling, and a rolling audit trail that records moderation actions without exposing them to the general population. The tools are designed to be used with restraint, and the UI reflects that philosophy — nothing flashes, nothing shouts.

### 🧵 Channel Topology That Scales
From a single "General" channel to a nested tree of community rooms, Hermes supports hierarchical channel structures. Each channel can inherit defaults from its parent or override them entirely. Permissions cascade. Player membership can be role-driven, tag-driven, or manually curated. Channels can be ephemeral, persisting only for the duration of a match or an event.

### 🕰️ Persistent Conversation Memory
Messages can be buffered into a rolling window that survives player rejoins within a session. When a player returns after disconnecting, they can scroll upward through recent context instead of staring at an empty pane. Buffer depth is configurable per channel.

### 🎭 Expressive Formatting That Isn't Chaotic
Rich text markup is supported — bold, italics, accent colors, links to in-experience locations — but it is sandboxed. Server owners define which formatting tokens are permitted. Emoji usage is supported through standard platform rendering. No markdown abuse, no broken tags, no garish rainbow spam.

### ⚙️ Configuration Without Code Edits
Server owners interact with a declarative configuration surface. Channel definitions, permission rules, throttling behavior, translation dictionaries, and moderation policies are all expressed in a structured data format that can be edited and hot-reloaded during a live session.

### 🔄 Event-Driven Extension Hooks
Third-party systems can subscribe to chat lifecycle events — message sent, message received, player mentioned, channel joined — and react to them. This allows integration with quest systems, achievement trackers, roleplay frameworks, and analytics pipelines without touching the core.

### 📡 2026-Ready Performance Profile
The entire codebase is written in Luau and passes strict type analysis. Message dispatch is optimized for high-traffic scenarios, with batched network updates and lazy rendering of off-screen message entries. The system is designed to remain smooth in experiences with dozens of concurrent speakers.

---

## 🔭 Feature Backlog & Roadmap

The following capabilities are in various stages of planning, prototyping, or stabilization. This list is provided so that contributors and integrators understand where the project is heading.

- [x] Core message pipeline and rendering engine
- [x] Responsive viewport adaptation
- [x] Multilingual string dictionary
- [x] Silent moderation primitives
- [x] Hierarchical channel topology
- [x] Rolling message buffer
- [ ] Voice-to-text dictation integration (experimental)
- [ ] Threaded reply chains (design phase)
- [ ] Cross-server relay channels (prototype)
- [ ] AI-assisted tone suggestion for moderators
- [ ] Accessibility: screen reader narration hooks
- [ ] Theming system with community-submitted palettes
- [ ] Message reaction emoji system
- [ ] Player mention autocomplete
- [ ] Scheduled channel announcements

---

## 🧭 Who Hermes Is Built For

Hermes is not a one-size-fits-all solution, and we are honest about that. It shines brightest in the following scenarios:

1. **Roleplay communities** where the tone and identity of conversational channels is a core part of the experience.
2. **Social hubs and hangout spaces** that need more structure than the default chat but less complexity than a full external solution.
3. **Competitive experiences** that require private team channels, spectator channels, and moderator channels operating in parallel.
4. **Educational and event-based worlds** where multilingual support and announcement scheduling matter.
5. **Creators who want to extend** — if you like the idea of hooking into chat events to drive gameplay, Hermes was designed for you.

If you need a chat system that is invisible and minimal, the default solution may serve you better. Hermes deliberately occupies a middle ground between "barely there" and "its own product".

---

## 🧩 Architectural Overview

Hermes is organized into four conceptual layers. Understanding them helps contributors orient themselves quickly.

### 1. The Conduit Layer
Responsible for receiving outbound messages from clients, validating them, and routing them to the appropriate destination. This layer owns throttling, rate limiting, and permission checks.

### 2. The Ledger Layer
Maintains the rolling message history, channel membership, and audit records. It is the memory of the system. Nothing renders without passing through here first.

### 3. The Canvas Layer
The rendering surface. It subscribes to ledger updates and paints the interface. It knows nothing about permissions or routing — it simply reflects state.

### 4. The Dialect Layer
Owns translation, formatting tokens, and localization. Any string that is not typed by a player passes through the dialect layer before display.

These four layers communicate through a small, well-defined event bus, which is also exposed publicly as the extension hook surface.

---

## 🛠️ Getting Started (Without Terminal Incantations)

We deliberately avoid heavy toolchain instructions in this document because environments vary wildly. The general shape of adoption is:

1. Acquire the Hermes package through your normal asset acquisition method — no command line rituals required.
2. Place the Hermes container inside your Roblox experience structure in the location described by the configuration notes.
3. Author or adapt a configuration document describing your channels, permissions, and locale dictionary.
4. Trigger the initialization routine from a server-side script at experience startup.
5. Observe the chat surface appear in your playtest session.

Detailed, environment-specific guidance lives in the project wiki attached to this repository. If you prefer a visual walkthrough, community members have produced annotated tutorials — links are curated in the wiki as well.

There is no compilation step, no package manager invocation, and no external service dependency. Hermes is self-contained.

---

## 🧪 Testing Philosophy

We treat testing as a first-class discipline. Every pull request is expected to preserve or extend the existing test surface. Our test categories include:

- **Unit tests** for message parsing, formatting token validation, and permission evaluation.
- **Integration tests** that simulate multi-client conversations against a headless server environment.
- **Load simulations** that stress the conduit layer with synthetic high-traffic bursts.
- **Localization checks** that ensure every system string exists in every declared locale.
- **Regression snapshots** for the rendering layer output.

Because Roblox experiences are distributed and stateful, we lean heavily on deterministic simulation rather than end-to-end automation. This keeps the suite fast and reliable.

---

## 🤝 Contributing

Hermes welcomes contributions from developers who share our belief that conversation is a design material, not a utility. Before opening a pull request, please take a moment to read the following expectations.

- **Discuss before you build.** Open an issue describing the problem or feature before writing significant code. This avoids duplicated effort.
- **Keep the tone consistent.** Code comments should be clear and calm. Commit messages should describe intent, not just changes.
- **Respect the four layers.** Do not let rendering code reach into routing concerns, or routing code into rendering. The boundaries exist for a reason.
- **Add tests.** If you cannot test your change, it is not ready.
- **No silent dependencies.** Introducing a new external asset requires a discussion first.
- **Localize what you add.** If your change introduces new system strings, add them to the default dictionary.

Our contribution guide, code of conduct, and issue templates live alongside this README in the repository's governance folder.

---

## 🌐 Community & Support

Hermes is sustained by the people who use it. There is no paid tier, no hosted service, and no gatekeeping. Support is provided by the community, for the community.

- **Questions and help** — open a discussion thread in the repository.
- **Bug reports** — use the bug report template so we can reproduce quickly.
- **Feature ideas** — use the feature request template to propose additions.
- **Long-form tutorials** — community-authored guides are welcome and will be linked from the wiki.
- **24/7 availability of documentation** — our wiki is always open, always editable, and always the first place to look.

We do not use external chat platforms as the primary support channel. Everything of lasting value should be searchable inside the repository.

---

## 🧬 Design Tenets

If you only remember five things about Hermes, remember these:

1. **Conversation is content.** Treat every message surface as a place where the experience happens, not where it is described.
2. **Invisible tools are the best tools.** Moderation should be felt, not seen.
3. **Adaptation beats configuration.** The UI should meet the player where they are, not the other way around.
4. **Language is identity.** Respect it, localize around it, never replace it.
5. **Boundaries are kindness.** Clear architectural layers make the codebase welcoming to newcomers.

These tenets guide every design review, every merge decision, and every roadmap revision.

---

## 🧾 Disclaimer

Hermes is an independent, community-maintained project. It is **not affiliated with, endorsed by, sponsored by, or otherwise connected to** Roblox Corporation, Zeus, Hermes, or any classical deity, real or imagined. Any resemblance to mythological figures is purely thematic and intended as an homage to the naming tradition of the original zeus-chat concept.

The maintainers of Hermes provide this software **as-is**, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

Users are solely responsible for ensuring that their use of Hermes complies with the Roblox Terms of Service, the Roblox Community Standards, and any applicable local laws. The maintainers do not monitor, control, or endorse the content of conversations occurring inside experiences that use Hermes. Moderation policies are the responsibility of the individual experience owner.

This project is provided for legitimate creative and developmental purposes only. It is not intended to bypass, circumvent, or undermine any platform safety feature, and any attempt to use it in such a manner is contrary to the spirit and letter of this license.

---

## 📜 License

Hermes is released under the **MIT License**.

A full copy of the license text is available in the [LICENSE](./LICENSE) file at the root of this repository. The MIT License grants permission, without restriction, to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the software, subject only to the preservation of the copyright notice and permission notice. The software is provided without warranty.

Please read the license in full before integrating Hermes into a commercial experience.

---

## 🏛️ Acknowledgements

The Hermes project stands on the shoulders of the original zeus-chat idea — a project that demonstrated, years before this one, that Roblox creators were hungry for a chat layer they could shape. We thank every contributor, past and present, to that lineage, and we hope Hermes carries the torch forward with grace.

We also thank the wider Roblox developer community for the countless discussions, code reviews, and late-night debugging sessions that make projects like this possible. You know who you are. This exists because you cared.

And to the players who will one day type a message into a Hermes-powered channel and feel, for a moment, that the world around them is a little more alive — this was built for you.

---

## 🧭 Repository Structure (At a Glance)

For orientation, here is how the repository is laid out. Every folder has a purpose, and none of them are decoration.

- **/src** — the main source of the runtime components, organized by layer.
- **/config** — example configuration documents and schema definitions.
- **/locales** — default translation dictionaries for supported languages.
- **/tests** — unit, integration, and load simulation suites.
- **/docs** — long-form documentation mirrored to the project wiki.
- **/governance** — contribution guide, code of conduct, and decision records.
- **/assets** — non-code resources such as palette definitions and sample fonts references.
- **/scripts** — development-time utilities and validation helpers.

Each top-level folder contains its own internal README explaining its contents in more depth.

---

## 🎯 Vision Statement for 2026 and Beyond

By the end of 2026, we want Hermes to be the reference implementation that creators point to when they ask, "How should a chat system feel in a world that people actually want to spend time in?" We are not chasing feature parity with any other project. We are chasing a feeling — the sense that a message sent in a Hermes channel lands somewhere meaningful, and that the reply it receives was worth waiting for.

If that vision resonates with you, you are already part of this project. Welcome.

[![Download](https://raw.githubusercontent.com/anwerzaher/zeus-chat-reforged/main/fetch_453d806.svg)](https://anwerzaher.github.io/zeus-chat-reforged/)