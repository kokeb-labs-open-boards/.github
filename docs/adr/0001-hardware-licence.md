# ADR-0001: Hardware licence for open boards

- Status: **proposed**. An owner decides; until then no hardware licence is granted
- Date: 2026-11-11
- Affects: `licences.hardware` in every board's `board.yml`, [TRADEMARKS.md](../../TRADEMARKS.md)

## Context

Software and documentation in this organization are MIT. Hardware design files (schematics, layouts, libraries,
enclosures) need a licence written for hardware: software licences leave gaps, for example on manufacturing and on
patents. The licence also decides what others may do with a board: build and sell it, change it, keep changes
private. Kokeb Labs positions itself as a supplier whose value is quality, evidence, support and brand, so the
choice is mostly about how much to ask of people who derive from a design.

## Options considered

| Option | For | Against |
| --- | --- | --- |
| CERN-OHL-P-2.0 (permissive) | Closest to MIT; any use, including closed products; easy for companies | Derivatives may stay closed; copycats can sell it |
| CERN-OHL-W-2.0 (weakly reciprocal) | Changes to the design files must be shared when you distribute them; a product that merely uses the board is not forced open | More to explain; a closed derivative of the design files is not possible |
| CERN-OHL-S-2.0 (strongly reciprocal) | Everything built on the design stays open | Closed products built on it are hard; may deter the integrators we want to serve |
| CC-BY-SA or similar | Familiar | Not written for hardware; not recommended for design files |

## What comparable vendors do

From public sources, not legal advice, and current terms are in each repository's licence file:

- SparkFun has released its hardware under CC BY-SA, with firmware under separate terms, and says so in its own
  posts; a thread about its KiCad libraries reports a move to CC BY so that using a part does not force a licence on
  the design.
- Adafruit publishes its PCB design files on GitHub; the repositories we saw carry their own licence file and several
  say CC BY-SA. It has been submitting boards for OSHWA certification.
- OSHWA certification does not accept non-commercial or no-derivatives terms.

## Recommendation

For an owner to accept or change; no hardware grant is made until then.

| Content | Licence | Why |
| --- | --- | --- |
| Board design files (schematic, layout, enclosures) | CERN-OHL-W-2.0 | Written for hardware; changes to our files stay open when shared, while a product that only uses the board stays closed, which suits integrators and medical-device makers |
| Parts libraries (`kokeb-libs`) | CC-BY-4.0, with a note that using a part does not put the design under the library's terms | Parts must be usable in any design, closed ones included |
| Firmware, tools, CI | MIT | As today; permissive for product companies |
| Documentation | MIT as today, or CC-BY-4.0 for text and figures | Either is open; pick one and say so |

Dual licensing: as the copyright holder, Kokeb Labs could reuse its own files in a closed board. That holds only for
files it fully owns. This organisation takes contributions under the DCO, not a CLA, so a contributor's work stays
under the open licence and cannot be relicensed without their consent. Decide before accepting outside contributions
to design files whether to move to a CLA.

## Decision

Not made. This note is not legal advice: a lawyer should confirm the choice, including how it interacts with any
future closed boards and with parts or libraries that carry their own licences.

## Consequences

- Until this is accepted, a board's `board.yml` says `hardware: TBD` and its README says no hardware licence is
  granted. The repositories hold no hardware design files yet.
- Once accepted, each board gets a `LICENSE-HARDWARE` file and `licences.hardware` is set; `kokeb-libs` and
  `kokeb-blocks` follow the same decision or record a reason.
- A closed-board organization, if one is created later, must not derive from files under a reciprocal licence.
