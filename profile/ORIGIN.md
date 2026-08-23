# ORIGIN

Why fork FreeBSD? Because of a board that both exists and does not.

**Contents**

- [Schrödinger's Router](#schrödingers-router)
- [The Graveyard](#the-graveyard)
- [The Software Is Already Waiting](#the-software-is-already-waiting)
- [Two Halves of the Same Board](#two-halves-of-the-same-board)
- [The Lie Problem](#the-lie-problem)
- [Not Everyone Is a Bring-Up Person](#not-everyone-is-a-bring-up-person)
- [The Code of Conduct](#the-code-of-conduct)

## Schrödinger's Router

[Martinfx](https://github.com/Martinfx), part of this org, has been bringing up the Banana Pi R2 Pro for over ten months. Alone. The board boots, the work is real, and it is still missing plenty, because he wants it to do a real job: be a router.

That board lives in a quantum superposition. It exists in his repo. It does not exist in the tree. It is simultaneously supported and unsupported, and it will stay that way for as long as one person carries it by himself. Nobody observes the work, so the wave function never collapses.

SoCBSD collapses it. Martinfx becomes a [tribute](GAMES.md#why-tribute). What works gets merged into [`gamemaster`](GAMES.md#the-world) now, not after the board is perfect. Other tributes who own the board add what he doesn't need: one brings USB, one brings the display, one writes the man pages. The board stops being one person's ten-month solo run and becomes an [arena](GAMES.md#the-arena).

And when it is done, it goes [upstream on a silver platter](GAMES.md#the-victory-tour): full support, tested by many tributes, with [real names](README.md#the-decree) attached to every claim.

## The Graveyard

Martinfx is the one who didn't quit. Behind him is a graveyard: dozens of contributors who attempted a bring-up, alone, hit the wall alone, and gave up alone. Their repos are still out there, half-booting, abandoned. Every one of those is a board FreeBSD could have had.

Solo bring-up doesn't fail because people are weak. It fails because bring-up is the single most hostile discipline in systems programming, and we keep sending people in one at a time.

## The Software Is Already Waiting

This is not hardware support for its own sake. The software is already here, waiting for the boards.

[Stefano Marinelli](https://bsd.cafe/@stefano) is building littlefedi, a tiny fediverse server made to run on exactly this class of hardware: a small board on a shelf, serving your corner of the fediverse. It should run on FreeBSD. It can't, because FreeBSD doesn't run on the Raspberry Pi 5 or the Banana Pi R2 Pro.

The demand exists. The applications exist. The gap is the bring-up.

## Two Halves of the Same Board

[seuros](https://github.com/seuros) built [vein](https://github.com/seuros/vein) and ran it on a Raspberry Pi 5 for months. The SoC work behind that was never upstreamed, for the classic reason: no video output, so it felt incomplete, so it stayed home. Meanwhile Michal Meloun (mmel), a FreeBSD committer with a long history of ARM work, did more on his side. The two efforts are complementary. Together they are most of a board. Apart, they are two more superpositions. Note what that means: both halves were held by FreeBSD committers, and the halves still never met. Two people with the power to commit, and the board is still in superposition. The commit bit is not the bottleneck. The collision is.

That is the quiet failure mode: not people quitting, but finished halves that never meet. In an arena, those two are [allies](GAMES.md#the-pressure-valve) on day one, the halves merge in `gamemaster` within a week, and both names go upstream on the patchset. [The Games](GAMES.md) exist to make the halves collide.

## The Lie Problem

Everything in this discipline lies. The silicon lies. The datasheets lie. The reference manual describes a register that does not do what it says, on a die revision the vendor never documented.

Upstream knows this, which is why upstream is cautious. When a patchset for an unknown board arrives from one person, the reviewers cannot know whether it even reaches userland. So it sits. Caution is not the disease; solitude is.

The Games are built on eliminating tributes who lie. [Untested code is death](GAMES.md#deaths). Every claim ships with a [serial log](GAMES.md#scoring). Every log is verified by another tribute who owns the same hardware. By the time a board leaves the arena, its truth has been established the hard way, by people trying to eliminate each other.

That is what upstream receives: not a patchset to be afraid of, but a board whose every claim has already survived hostile review. FreeBSD can merge it with confidence, because the lying tributes are already dead.

## Not Everyone Is a Bring-Up Person

The other thing solo bring-up wastes: everyone who is excellent at something else.

Someone is brilliant at one subsystem and cannot bring up a board to save their life. Someone writes the best man pages in the project and never gets a board to document. Someone has been reading FreeBSD source for years and never sent a patch, because impostor syndrome told them the bar is somewhere above their head.

The arena has room for all of them. A board needs drivers, but it also needs its edge cases hunted, its documentation written, its logs verified, its code reviewed. [Points are points](GAMES.md#scoring). The tribute who writes the man pages for a router is part of why it ships on a silver platter.

## The Code of Conduct

Be excellent to each other. The game is already hostile.
