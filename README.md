# Physical AI / Sensor-Based Interaction — Personal Curriculum

Bin Youn. Started 2026-08-21. **Status: personal working curriculum.** Written so it can later
be extracted into a shareable module format (an RMIT workshop kit, in the pattern of
`webar-studio` and the Commercial Photography course site) without a rewrite — each module below
separates **Core** (generic, teachable to anyone) from **Applied** (this project's specific
case study) and **Log** (personal reflection) for exactly that reason.

## Why this exists

This isn't a side skill — physical AI / sensor-based interaction is the actual subject of my
PhD (*Circulatory Sensing*). The tool progression below exists to de-risk real open questions in
[Circulation](../circulation) (does PPG read through a sealed palm, BMP280 vs FSR, the 5-point
contact interface) rather than run as a separate hobby track. Every module's Applied section
should point at a real unresolved question from that project, not a toy exercise.

Documentation plan: one short video per module milestone (not per session) posted to
Instagram/YouTube — a learning-in-public arc with real stakes, and a forcing function to keep
going. Recording template at the bottom.

## Live tracker

**[Signal Path](https://claude.ai/code/artifact/4753e855-26b2-4930-8965-6e7de950dadb)** —
day-to-day progress lives here, not in this file: a checklist per module, a notes field that
autosaves as you type, a video log (date + link) for each milestone, and the recording template
one click away. This README stays the canonical curriculum text; Signal Path is where actual
task-by-task tracking happens.

## Tools, in progression order

| Stage | Tool | Level | What it's for |
|---|---|---|---|
| 1 | [Tinkercad](https://www.tinkercad.com) | Easy | Circuit intuition, no code complexity |
| 2 | [Wokwi](https://wokwi.com) | Medium | Realistic microcontroller + sensor sim, real firmware |
| 3 | Physical Arduino | — | Where simulation stops telling the truth |
| 4 | [Diode](https://www.withdiode.com) | Advanced | Schematic capture + PCB layout, prototype → object |

---

## Module 1 — Tinkercad: what a sensor actually is

**Core:** Breadboard basics, one sensor driving one output (pressure/light/touch → LED), reading
analog vs digital signals, the idea of a threshold. No firmware complexity — the goal is
"signal in, behavior out" as a felt intuition before code enters the picture.

**Applied:** Build the simplest possible version of a cup contact point — one pressure sensor,
one LED, one threshold — before touching the real 5-point interface.

**Milestone:** One sensor reliably driving one LED, explained out loud on camera in your own
words (not read from a script — the explaining is the test of whether it's actually understood).

**Log:** tracked live in [Signal Path](https://claude.ai/code/artifact/4753e855-26b2-4930-8965-6e7de950dadb#module-1) — checklist, notes, video log for this module.

---

## Module 2 — Wokwi: realistic firmware, still safe to break

**Core:** Real microcontroller (ESP32), real C++ Arduino code, real sensor chips simulated
accurately enough to matter (this is not a toy simulator — Wokwi's MAX30102/BMP280 parts are
real library-driven sims). Nothing here can be physically damaged, so this is where you should
take the most risks with code.

**Applied:** Already underway in `circulation/wokwi/` — `cup.ino` running unmodified against a
virtual ESP32 + `chip-max30102`. Open question to resolve here first, before it costs a physical
part: does `checkForBeat()` ever actually fire in the sim? Confirm before assuming the firmware
logic is sound.

**Milestone:** One resolved open question from the Circulation build plan, settled in simulation
before physical bench-testing.

**Log:** tracked live in [Signal Path](https://claude.ai/code/artifact/4753e855-26b2-4930-8965-6e7de950dadb#module-2) — checklist, notes, video log for this module.

---

## Module 3 — Physical Arduino: where simulation lies to you

**Core:** Contact noise, calibration drift, real-world sensor behavior that no simulator models
— skin contact resistance, motion artifact, ambient light interference, power noise. This module
is where "it worked in Wokwi" gets tested against a body. You've already done two solo builds
here (2026-07ish) — this module formalizes what you already started.

**Applied:** The actual bench experiment Circulation needs regardless of the curriculum: does
MAX30102 read a usable pulse through a sealing, gripping palm. This is flagged in
`hardware/TECHNICIAN_BRIEF.txt` as the single biggest open hardware question in the project.

**Milestone:** A real answer (not a guess) to the palm-PPG question, recorded with actual
waveform/readout evidence, not just "it seemed to work."

**Log:** tracked live in [Signal Path](https://claude.ai/code/artifact/4753e855-26b2-4930-8965-6e7de950dadb#module-3) — checklist, notes, video log for this module.

---

## Module 4 — Diode: from prototype to object

**Core:** Schematic capture and PCB layout — turning a breadboard's mess of wires into something
that can physically live inside a small enclosure. Professional hardware workflow literacy: even
if fabrication gets outsourced, being able to read/discuss a schematic matters for the PhD
paper and for talking to a technician as a peer, not a client.

**Applied:** The board that needs to fit inside a 5cm U4 cupping cup — ESP32 + BMP280/FSR +
MAX30102 + LED ring, once Modules 2-3 have settled which sensors actually make the cut.

**Milestone:** A schematic you can explain node-by-node, even before it becomes a fabricated
board.

**Log:** tracked live in [Signal Path](https://claude.ai/code/artifact/4753e855-26b2-4930-8965-6e7de950dadb#module-4) — checklist, notes, video log for this module.

---

## Recording template (for each milestone video)

Keep it short — under 3 minutes, one take if possible, imperfection is part of the "learning in
public" premise:

1. **Hook (10-15s):** What question was I trying to answer in this module?
2. **What I built (60-90s):** Show it working (or not working — failure is content too).
3. **What surprised me (30-45s):** The one thing simulation/theory didn't prepare me for.
4. **What's next:** Which module or open question comes after this.

## PhD grounding — reading list

Not part of the tool progression above — this is theoretical/methodological grounding for
*Circulatory Sensing*, gathered 2026-08-21. Annotated so each entry earns its place rather than
just being a name-drop.

**Core theoretical anchor**
- Kristina Höök, *Designing with the Body: Somaesthetic Interaction Design* (MIT Press, 2018).
  Close to required reading — Höök is the leading HCI researcher on soma-based, felt-experience
  design, and this book maps almost exactly the territory Circulation sits in: interaction
  design grounded in bodily, felt experience rather than screen-based interaction. Gives the PhD
  a real citation lineage instead of just "inspired by."

**Practice-based research methodology**
The field that legitimizes "the device and its documentation IS the research output," not just
supporting material for a written thesis:
- Robin Nelson, *Practice as Research in the Arts: Principles, Protocols, Pedagogies,
  Resistances* (Palgrave Macmillan, 2013).
- Estelle Barrett & Barbara Bolt (eds.), *Practice as Research: Approaches to Creative Arts
  Enquiry* (I.B. Tauris, 2007/2010).
Both are foundational texts in the Australian practice-led/practice-as-research tradition RMIT's
own HDR culture belongs to. **Ask your supervisor whether RMIT HDR has its own
recommended/required methodology reading or coursework** before treating this pair as
sufficient — this list is a starting point, not confirmed against RMIT's actual requirements.

**Bio-art / biofeedback lineage** — who Circulation is in conversation with, not required
reading, but worth knowing before the paper draft:
- Marco Donnarumma — biophysical/visceral performance work built on EMG and other physiological
  signals; a practice-based PhD (Goldsmiths) covering similar ground of body-as-instrument.
- Lisa Park — *Eunoia*, an EEG-controlled water installation translating internal physiological
  state into external, visible movement.
- Suzanne Dikker — *The Mutual Wave Machine* (with the Marina Abramović Institute), EEG
  synchrony between two people made visible/audible in real time — close kin to Circulation's
  triad-sync concept.

**How to use this**: the core anchor and methodology pair are for grounding the *thesis
argument* — cite them, build the framework's vocabulary from them. The bio-art lineage is for
the *related-work section* — know these precedents well enough to say precisely how Circulation
differs (negative-pressure cupping as the sensing mechanism, Five Elements as the mapping
framework, 수지침 as the embodied grounding), not just that it's adjacent to them.

## Future shareable extraction

When this becomes a real workshop kit: each module's **Core** section becomes the public
teaching content as-is; **Applied** sections become a worked case-study example (swap in a
different project if teaching someone without Circulation context); the Signal Path **Log**
entries (notes + video log) stay private or become an instructor's-notes appendix. Don't blend
personal reflection into Core sections as you fill them in — keep the separation clean from the
start so extraction later is a copy-paste, not a rewrite.
