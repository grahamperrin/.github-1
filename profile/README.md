# SoCBSD

**A FreeBSD fork dedicated to SoC board bring-up. A playground, not a distro.**

Hundreds of boards run Linux. Only a handful run FreeBSD. SoCBSD exists to close that gap: FreeBSD, brought to the SoC boards it does not support today.

Why a fork? Read [ORIGIN.md](ORIGIN.md). The short version: solo bring-up creates boards that exist in someone's repo and nowhere else, and it burns out the people carrying them.

**Code of Conduct**: Be excellent to each other. The game is already hostile.

## Scope

- SoC board bring-up only. Everything outside SoC support stays as upstream ships it.
- Fast iteration, fast merges. Experiment here, stabilize, then present the work upstream to FreeBSD.
- A board is in scope when it is an SoC board, it boots FreeBSD, and it does something useful.
- Hardware that FreeBSD has already removed stays removed. This is not a resurrection project. No retro archaeology, no NetBSD-with-Amiga-support.
- No ISOs, no wallpapers, no distro.

## The Decree

Hardware bring-up only works when claims are verifiable. These rules are not optional:

1. **Own the device.** Contributions are accepted only for boards the contributor physically has on their desk.
2. **The device must be in proper working condition.** Dead boards produce dead code.
3. **Untested code gets you benched.** Submitting code never run on the hardware means a ban from that board for the season ([Deaths](GAMES.md#deaths)). Other contributors double-check every submission.
4. **AI review is assumed.** Every contributor is expected to use AI to review their code, double-check their assumptions, and polish their commit messages and replies. Use the tools. Full ruling in the [AI Policy](AI-POLICY.md).
5. **`gamemakerd` runs on every PR.** The org's review bot comments on what it finds. The perfect score is **zero generated comments**. Clean PRs merge fast.
6. **Real names only.** No hiding behind nicknames. Upstreaming to FreeBSD requires real names attached to real commits.
7. **Provenance matters.** No copying GPL code, ever ([Foreign Powers](GAMES.md#foreign-powers)). Every line must be clean for FreeBSD. Code without provable origin does not go in.

## The Games

Bring-up runs as seasonal games. Boards are [arenas](GAMES.md#the-arena), contributors are [tributes](GAMES.md#the-reaping), and the scoreboard is [generated, not negotiated](GAMES.md#the-gamemakers). Full rules in [GAMES.md](GAMES.md).

## The Path

1. A contributor picks a board they own.
2. Existing bring-up work is checked first. New targets are claimed by [opening an issue](GAMES.md#the-arena).
3. Code is built, flashed, and tested **on the hardware** before a PR is opened.
4. Contributors who own the same board review each other's work. Independent verification is how untested code gets caught.

## Contact

The work happens on GitHub: issues, discussions, and PRs on the org repositories. A Forgejo mirror may come later.
