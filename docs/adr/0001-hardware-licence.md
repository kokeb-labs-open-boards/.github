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

## Decision

Not made. The options above are a starting point for an owner's decision; this note is not legal advice, and a
lawyer should confirm the choice, including how it interacts with any future closed boards and with parts or libraries
that carry their own licences.

## Consequences

- Until this is accepted, a board's `board.yml` says `hardware: TBD` and its README says no hardware licence is
  granted. The repositories hold no hardware design files yet.
- Once accepted, each board gets a `LICENSE-HARDWARE` file and `licences.hardware` is set; `kokeb-libs` and
  `kokeb-blocks` follow the same decision or record a reason.
- A closed-board organization, if one is created later, must not derive from files under a reciprocal licence.
