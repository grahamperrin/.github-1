# The Games

SoCBSD bring-up is run as seasonal games. Boards are arenas. Contributors are tributes. The scoreboard is a build artifact, not an opinion.

May the odds be ever in your favor. They won't be. It's hardware bring-up.

**Contents**

- [Why "Tribute"](#why-tribute)
- [Districts](#districts)
- [The Arena](#the-arena)
- [The World](#the-world)
- [The Reaping](#the-reaping)
- [Foreign Powers](#foreign-powers)
- [Scoring](#scoring)
- [The Eleven](#the-eleven)
- [Deaths](#deaths)
- [Closing an Arena](#closing-an-arena)
- [Sponsors](#sponsors)
- [The Victor](#the-victor)
- [The Victory Tour](#the-victory-tour)
- [The Gamemakers](#the-gamemakers)
- [The Pressure Valve](#the-pressure-valve)

## Why "Tribute"

The word was already hiding inside "contributor". Latin `tribuere`, to give. A *con-tributor* is one who gives together. Strip the prefix and what remains is a *tribute*: one who gives alone.

That is what solo bring-up made of people. FreeBSD never lacked givers; it had tributes, paying alone into [a graveyard](ORIGIN.md#the-graveyard). The Games just say the word out loud. You enter the arena a tribute, and the arena gives you back the prefix: allies, Mentors, rivals verifying your logs. [The Victory Tour](#the-victory-tour) is the moment the *con* is restored: many names, one patchset, given together.

A tribute **volunteers**. Nobody is reaped against their will here. You volunteer your time to test, to think about the code, to read the datasheet, to understand cross-code pollution, to make sure a change is not calling a deprecated API, not taking a giant lock, not quietly breaking someone else's board. That is the tribute you pay, and the silicon collects it in months of your life. The finished board is the second payment: tribute rendered upstream to FreeBSD.

What a tribute is not: a fame vehicle. Using AI to farm fame is the fastest way to become unfamous. [`gamemakerd`](GAMEMAKERD.md) will ban you without any drama, and the graph will remember.

## Districts

Each SoC vendor family is a district: Allwinner, Rockchip, Amlogic, Broadcom, NXP, Qualcomm, and any family a tribute brings in. Every district has a label and its own leaderboard.

## The Arena

Each board is an arena, opened as an issue in the org. The arena issue's opening post is the **Cornucopia**: datasheets, schematics, boot ROM notes, and prior art. Everyone draws from the same pile. Provenance rules from [the Decree](README.md#the-decree) apply to everything in it. What foreign code may enter is governed by [Foreign Powers](#foreign-powers).

## The World

The world is the branch topology, and the branch topology is law.

- **`gamemaster`** is the default branch: FreeBSD plus every board that survived the gate. It is what a visitor clones and what boots everything.
- **Arena branches** (`arena/<board>`) cut from `gamemaster`, one per board. Inside an arena, fast merges rule: tribute PRs land quickly, chaos is permitted, the [`gamemakerd` score](#scoring) still counts.
- **Upstream syncs**: `freebsd/main` merges into `gamemaster` monthly, or on demand when a tribute shows that FreeBSD landed something they need. An on-demand request must point at the actual upstream commit. Syncs are not a weapon for forcing rebase pain on rival arenas.
- After a sync, arenas rebase onto the new `gamemaster`. An arena that ignores two consecutive syncs is drifting toward unmergeable and toward starvation.

**The Gate.** Nothing enters `gamemaster` without passing the gate:

1. **Duplicate check**, against `gamemaster` and every sibling arena. Two arenas on the same SoC family will write the same clock and pinctrl drivers. The first arena to merge a shared driver owns it. The second adopts it at their gate.
2. **Concern review.** Edge cases, error paths, provenance.
3. **Refactor.** Board code that belongs at the SoC family level is extracted into shared drivers before merge. Gate refactors score points: they feed every future arena in the district.
4. **Clean history.** The gate produces a bisectable series, board commits and shared-driver commits clearly separated. [The Victory Tour](#the-victory-tour) requires carving a per-board patchset out of `gamemaster`, and archaeology is not a plan.

## The Reaping

Seasons are monthly, tracked as GitHub milestones. A tribute enters an arena by commenting on the arena issue with proof of hardware: a photo of the board and a serial capture of whatever it currently does. No hardware, no entry. [The Decree](README.md#the-decree)'s ownership rule is the gate.

## Foreign Powers

Other operating systems exist in the Games, and they have names.

**The Capitol (Linux).** Vast, wealthy, runs on every board in existence. Its goods are poisoned: GPL code never enters the Cornucopia. Tributes may study the Capitol's technology to extract facts, register maps, interrupt wirings, clock topologies, because facts belong to no one. Taking its code is provenance death under [the Decree](README.md#the-decree). GPL-only device trees stay outside the arena walls.

**The Allies (NetBSD and OpenBSD).** Friendly districts, BSD-licensed. Their drivers enter the Cornucopia freely. The alliance has one price: original copyright notices stay intact. Their ARM coverage, especially NetBSD's Allwinner, Rockchip, and Amlogic work, is the richest legal loot in the Games. But an ally's driver is a port, not a paste: their fdtbus is not our simplebus, and code pasted verbatim and never booted dies by the Decree like everything else.

**Sponsor parachutes (firmware DTBs).** A device tree supplied by the board's own firmware, such as U-Boot, arrives from outside the arena and may be used freely. It is data handed to the kernel, not code inside it. A firmware DTB counts as valid for all tiers.

**Clean-room device trees.** When no dual-licensed or firmware DTB exists, tributes write their own from the datasheet and schematics. Hardware facts are free. Structure, naming, and comments copied from the Capitol's tree are not, and a suspiciously familiar diff earns the provenance death penalty.

## Scoring

Points are awarded per survival tier. Every claim requires a serial boot log attached to the PR, verified by another tribute who owns the same board.

| Tier | Milestone | Points |
|------|-----------|--------|
| 1 | Boot chain reaches the FreeBSD loader | 10 |
| 2 | Kernel boots to single-user with serial console | 25 |
| 3 | Multi-user with working storage (eMMC/SD) | 50 |
| 4 | Network up | 75 |
| 5 | The Final Trial: `make buildworld` natively on the board | 150 |

**Difficulty multiplier**: a board on an SoC family with zero existing FreeBSD support scores double.

**Clean kill**: `gamemakerd` generates zero comments on the PR, bonus points. Every `gamemakerd` comment that survives triage deducts.

## The Eleven

Porting is survival. It is not glory.

Most of these boards were brought up in [the other nations](#foreign-powers) by [one or two people](ORIGIN.md#the-graveyard). Their drivers work for the happy path and nothing else: edge cases unhandled, errata silently ignored, whole subsystems missing. Matching the Capitol makes SoCBSD a follower. Beating it makes SoCBSD a reference.

**The Eleven** is awarded when a tribute introduces something no other OS has on that board:

- An errata workaround the other nations never implemented.
- An edge case handled that crashes or corrupts everywhere else.
- A subsystem the others skipped: suspend/resume, thermal, CPU frequency scaling, a peripheral nobody bothered with.
- Undocumented hardware behavior discovered on the bench and written down for the first time.

An Eleven claim requires two proofs: it works on the hardware, and the Capitol and the Allies do not have it. Link their trees. Absence must be shown, not asserted.

**Score: +50 per Eleven, stacking.** The Gamemakers do not cap audacity.

## Deaths

Untested code is death. A tribute who submits code never run on the hardware is eliminated from that arena for the season.

Dead tributes become **Mentors**. Mentors review, verify boot logs, and sponsor. Mentors do not submit code for that board until the next [Reaping](#the-reaping).

## Closing an Arena

An arena closes when all of its tributes judge there is nothing left to add. The board is done. Its code lives in `gamemaster`, its branch is retired, and its history stands ready for [the Victory Tour](#the-victory-tour).

**New seasons.** A closed arena can be reopened: any tribute may call a new season (`season_2`, `season_3`, and so on). The call carries a price of proof:

- A season is opened only with **working code on the bench**. The call must include the diff and a serial log of it running on the hardware. Not an idea, not a roadmap, not "we could add X". Running code.
- A season call built on hallucination, code that does not exist or does not do what is claimed, gets the caller **banned from the Games for one week**. Not the arena. The Games. All arenas, all districts, seven days of silence to think about what running code means.

## Sponsors

Sponsors ship hardware to tributes. A sponsor whose board reaches [Tier 3](#scoring) or higher gets their name on the arena permanently.

## The Victor

The Victor of an arena is the tribute holding the most points when the board reaches [Tier 5](#scoring). The Victor's name leads the patchset when it is presented upstream to FreeBSD, and the Victor becomes the board's maintainer of record. [Real names only](README.md#the-decree). The glory is real, so the name must be too.

## The Victory Tour

The Victory Tour is the upstream submission itself. A season is not won until FreeBSD sees the work.

## The Gamemakers

Scoring is automated. [`gamemakerd`](GAMEMAKERD.md), the Gamemakers' daemon, reviews every PR and comments on what it finds. A GitHub Action parses merged PRs and `gamemakerd` comment counts, then regenerates `SCOREBOARD.md`. No manual bookkeeping. Disputes are settled by the boot log or not at all.

## The Pressure Valve

Bring-up is [brutal solo](ORIGIN.md#the-graveyard). Arenas with one tribute starve. [Mentors](#deaths) exist, the [Cornucopia](#the-arena) is shared, and tributes on the same board may form alliances and split points. Competition is the engine. Collaboration is the fuel.
