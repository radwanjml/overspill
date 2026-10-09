# Overspill

**A chain-reaction strategy game played on a generated 3D network.**
Play it: **https://overspill-game.netlify.app**

Tap a node to charge it. Each tap lights one of its connections; when every
connection is lit, the next tap detonates it, pushes a charge into each
neighbour and turns them your colour. Neighbours that overflow detonate in turn,
so one tap can ripple across the whole board. Last player holding anything wins.

2–4 players on one device, or 2 players online with a five-character room code.

## Why a network, not a grid
The classic chain-reaction rule is a known mathematical object, a
**chip-firing game** (the abelian sandpile model). On a square grid every cell
is the same. On a real network every node is different: a 2-connection branch is
cheap and fragile, a 6-connection hub is expensive and decisive.
**Topology is the level design.** Four graph families (organic, scale-free,
small-world, lattice) plus a random mix generate a new board every game.

## Design decisions worth reading
- **The half-edge counter.** Players never count taps. Each tap lights one edge
  from the node outward; the dark edges are the taps remaining. Rule and readout
  are the same object, and a fully lit hub reads as a loaded gun.
- **The sky is the turn indicator.** The nebula washes toward the active
  player's colour instead of a HUD label.
- **Colour-blind-safe player pairs.** Gold and violet are 223° apart and stay
  separable under deuteranopia, protanopia and tritanopia.
- **Balance tested by bots that play toward the opponent:** 300 seeded games
  across four families and three player counts, zero timeouts, zero invariant
  violations.

## Tech
One self-contained `index.html` (~1 MB). No build step, no framework.
- Three.js with custom shaders, bloom and a procedural nebula
- PeerJS (WebRTC) for peer-to-peer online play
- Fonts and libraries inlined, so it runs from a single file

Run locally: open `index.html`, or `python -m http.server` in this folder.

## Credits
Design and code: Radwan Jameel ([Tibr Studio](https://github.com/radwanjml)).
Third-party code and fonts: see `THIRD_PARTY_NOTICES.md`.

© 2026 Radwan Jameel. All rights reserved. The source is published to read and
learn from; it is not licensed for reuse or redistribution.
