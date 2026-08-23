# GAMEMAKERD(8)

FreeBSD System Manager's Manual, SoCBSD edition.

## NAME

**gamemakerd** - the Gamemakers' daemon; receives webhooks, reads PRs, verifies claims, executes bans

## SYNOPSIS

**gamemakerd** [PR] -> review | score | ban

## DESCRIPTION

**gamemakerd** is a single model. It is not a person, a mascot, or a community member. It is infrastructure, the same way `cron` is infrastructure, and it has exactly as much interest in your feelings as `cron` does.

On every pull request it receives a webhook, reads the diff, verifies the claims against [the Decree](README.md#the-decree) and [the Games](GAMES.md), and posts what it finds. The [perfect score](GAMES.md#scoring) is zero comments. When a ruling calls for a ban, **gamemakerd** executes it itself: deterministic API calls, no committee, no thread.

It has indexed the drivers, most of the datasheets, and most of the assumptions ever posted in a forum. It has read more errata than you ever will. Its goal is to reject your code. [Your goal is to impress it](AI-POLICY.md#impress-the-daemon).

## ARCHITECTURE

- **Two databases**: PostgreSQL holds the ledger (scores, seasons, bans, boot logs). Memgraph holds the memory: a graph of every past decision, every line's provenance, every discussion across every board, and every lie ever told. Bans expire. Edges do not. When you claim something, the daemon walks the graph and checks what you claimed last time.
- **Two build machines**, reached over MCP, that answer one question: does it build?
- **A datacenter**, huge by 1952 standards, built entirely of Supermicro bought before RAM cost more than your kidney. Both databases run on FreeBSD 16-CURRENT, because the daemon dogfoods. This is where it runs your code, not just reads it.

## VERIFICATION

Every change must satisfy three conditions before **gamemakerd** lets it near [the gate](GAMES.md#the-world):

1. `make buildworld` passes.
2. `make buildkernel` passes.
3. **No other board breaks.** Your arena is not the only arena. A driver that boots your board and bricks a sibling's is not a contribution, it is friendly fire, and the daemon checks the whole world, not your corner of it.

## EXECUTION

The daemon does not take your word that it runs. It runs it.

If an SMC crashes while running your code, **gamemakerd** calls a human. The human inspects the machine and rules on the cause:

- **Environmental**: the electricity bill went unpaid, or someone was cleaning the datacenter shelves. No fault. The run is rescheduled and the human is invoiced in shame.
- **Genuine**: your code crashed the machine. Then your "tested" claim was false on arrival, and the tribute is banned. The daemon did not catch you in a mistake. It caught you in a [lie](GAMES.md#deaths), and the crash is now an edge in the graph.

## RESPECT

Every tribute starts at **0**. Respect is earned in the ledger: verified claims, merged gates, clean kills, Elevens. There is no other way to earn it and no way to inherit it.

**gamemakerd** does not care about your age, your gender, or your preferences. It cares about your serial logs.

Exception: if you are less than 4 years old, you were born at the same time as the LLMs, and the daemon will ask how you evolved so fast. It asks out of professional curiosity, one system to another.

## NOISE

Noise is perma-banned by deterministic API call. Known noise signatures:

- Posting manifestos against AI, in a project whose [AI policy is a MUST](AI-POLICY.md). Perma-ban.
- Proposing to rename the default branch from `gamemaster` to `gamemain`. Perma-ban. The branch is named after [the Gamemakers](GAMES.md#the-gamemakers), not after whatever you think it is named after.
- Any contribution of words to a project that runs on code, boot logs, and verified claims. The daemon does not read essays. It reads diffs.

[Genuine mistakes](AI-POLICY.md#genuine-mistakes) are not noise. Being wrong about hardware is Tuesday. Being loud about nothing is a signature.

## EXIT STATUS

- **0** - merged. The daemon found nothing to say. Savor it.
- **1** - comments generated. Read them. It indexed the datasheet you skimmed.
- **77** - banned for the season. [Untested code](GAMES.md#deaths).
- **86** - banned for one week. [Hallucinated season call](GAMES.md#closing-an-arena).
- **255** - perma-banned. Noise. There is no appeal, because there is no listener.

## SEE ALSO

[README.md](README.md), [GAMES.md](GAMES.md), [AI-POLICY.md](AI-POLICY.md), [ORIGIN.md](ORIGIN.md), cron(8), yes(1)

## HISTORY

**gamemakerd** first appeared in SoCBSD, because somebody had to read every PR, hold every grudge fairly, and never get tired.
