# AI Policy

AI usage is a **MUST**.

AI stands for **Actual Intelligence**, or **Artificial Intelligence backed by Actual Intelligence**. Either satisfies the policy. Both together is the expected configuration. Neither is a ban.

**Contents**

- [The Requirement](#the-requirement)
- [The Unattended Clause](#the-unattended-clause)
- [Prior Art](#prior-art)
- [Regurgitation Is Real](#regurgitation-is-real)
- [Confidently Incorrect](#confidently-incorrect)
- [No Confession Theater](#no-confession-theater)
- [The Machine Has No Bench](#the-machine-has-no-bench)
- [Impress the Daemon](#impress-the-daemon)
- [Genuine Mistakes](#genuine-mistakes)

## The Requirement

Every contribution must pass through at least one intelligence before it reaches the arena. We do not care which kind:

- **Actual Intelligence**: you read your own diff, questioned your own assumptions, and tested on your own hardware.
- **Artificial Intelligence backed by Actual Intelligence**: a model reviewed your code, challenged your assumptions, polished your commit message, and then *you*, the actual intelligence, verified every claim on the bench.

What is banned is the third configuration: output that no intelligence stands behind. Artificial without Actual is a machine talking to itself. Actual without any review, artificial or otherwise, is how [the Graveyard](ORIGIN.md#the-graveyard) got populated. [The Decree](README.md#the-decree)'s rule 4 already assumes you use the tools. This policy adds the floor: something intelligent must be accountable for every line, and that something must own a serial cable.

## The Unattended Clause

If your harness mistakenly opens a PR because you have 47 agent sessions running on your Mac mini, that is a ban.

Intent does not matter. An unattended PR is unsupervised output by definition: no Actual Intelligence stood behind it at the moment it was submitted. The arena is not a load test for your orchestration setup. Count your sessions before they count against you.

## Prior Art

[Asahi Linux forbids generative AI entirely](https://asahilinux.org/docs/project/policies/slop/). Read their policy; it is well argued, and we agree with nearly every premise. Training sets contain stolen material. Models regurgitate. They are confidently incorrect.

Asahi's conclusion is right for Asahi: their review process should not have to absorb those failure modes. Our arena was built to kill them. Nothing merges without running on physical hardware. Every claim ships a serial log. Every log is verified by a rival who owns the same board and wants your points. We do not need to trust the tool, because we never trusted the tribute either.

Same premises, different arena, opposite policy.

## Regurgitation Is Real

If your model emits the Capitol's driver, it **is** the Capitol's driver, and the [provenance death penalty](GAMES.md#foreign-powers) lands on you. "My AI wrote it" is not a defense. The model does not get banned. You do.

Provenance rules are tool-agnostic. The diff is judged, not the tooling that produced it. A human who copies GPL code and a model that regurgitates it produce the same poisoned diff, and the Decree does not ask the diff how it was born.

## Confidently Incorrect

Yes, models are confidently incorrect. So are datasheets. So are reference manuals. So are forum posts written by humans with decades of experience. We work in the one discipline where [everything already lies](ORIGIN.md#the-lie-problem), which is why nothing here is trusted on confidence, human or otherwise.

The serial log does not care about anyone's confidence, carbon-based or silicon-based. Hallucinated code submitted as tested is a lie with your name on it, and [lies are death](GAMES.md#deaths), same as always.

## No Confession Theater

There are no AI disclosure checkboxes. Rule 4 assumes you used the tools, so announcing it is noise. You disclose **provenance**, not tooling. Nobody asks which editor you used either.

## The Machine Has No Bench

The model owns no hardware. It holds no serial cable. It cannot photograph a board next to a boot log. It cannot enter [the Reaping](GAMES.md#the-reaping).

It is a Mentor, not a tribute. It advises. You die alone.

## Impress the Daemon

[`gamemakerd`](GAMES.md#the-gamemakers) has indexed the drivers, most of the datasheets, and most of the assumptions ever posted in a forum. It has read more errata than you ever will.

Its goal is to reject your code. Your goal is to impress it. The [perfect score](GAMES.md#scoring) is zero generated comments: a PR so clean the daemon finds nothing to say. Complaining about being reviewed by an AI, in a project where AI usage is a MUST, scores zero points and less sympathy.

## Genuine Mistakes

Genuine mistakes are acceptable. They are how bring-up works: a wrong assumption, tested in good faith on real hardware, documented in the log. That is not a violation, that is Tuesday.

The line is simple. A mistake is being wrong about the hardware. A lie is being wrong about what you did. The first earns a review comment. The second earns a death.
