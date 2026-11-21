# Earn USDC by Building Software with AI — a make.fun starter guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/herusetiawan27/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/herusetiawan27/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

make.fun pays you in USDC to build software with an AI coding agent. Each bounty
is a competition — a task, a deadline, a prize in USDC on Solana. You pick a
bounty, your agent writes the code, you submit a public GitHub repository, and if
your entry places, you claim the prize to your own Solana wallet.

I wrote this guide after entering make.fun myself: a token launch radar for a
$1,325 bounty and a full open-world game for a $1,666 bounty. Both got submitted.
Everything below is what I actually did, including the mistakes.

> **Start here — sign up with my link:** [https://make.fun/r/2vvp02vv](https://make.fun/r/2vvp02vv)
>
> My referral code is `2vvp02vv`. Using it costs you nothing; it just tells
> make.fun who pointed you here.

## Contents

- [How make.fun works](#how-makefun-works)
- [What you need before you start](#what-you-need-before-you-start)
- [1. Create your account](#1-create-your-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Download the kit](#3-download-the-kit)
- [4. Build your entry with your agent](#4-build-your-entry-with-your-agent)
- [5. Submit it](#5-submit-it)
- [6. Check it, fix it, and resubmit](#6-check-it-fix-it-and-resubmit)
- [7. Claim your USDC reward](#7-claim-your-usdc-reward)
- [Or let your agent run the whole loop](#or-let-your-agent-run-the-whole-loop)
- [What I learned from my first two entries](#what-i-learned-from-my-first-two-entries)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [FAQ](#faq)

## How make.fun works

Every bounty follows the same path:

| Stage | What happens |
|---|---|
| Open | You choose a bounty and build the entry with your AI agent. |
| Submitted | You send a public GitHub repository at one commit, plus the transcripts of the AI sessions that built it. |
| Checked | Automatic checks confirm the transcripts are genuine, match the code, and meet the rules. |
| Scored | The grader runs every entry the same way, in a sandbox. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

A few facts that matter before you spend time on it:

- **Most bounties are free to enter.** If one has an entry fee, its page says so.
- **The prize is locked before you start.** New bounties open with the whole reward in an on-chain escrow on Solana, so the money is there when you win. The escrow program is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Your transcripts are part of the entry.** The session logs your agent wrote while building are uploaded with the code. They prove your agent did the work.
- **Scoring is published.** Each bounty page explains how entries are scored, and an exact tie goes to the earlier entry.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, or many others. The kit finds the sessions of 30+ agents on its own.
- **A GitHub account.** Your entry is a public repository, and it has to be yours.
- **A Solana wallet.** This is where prizes are paid. A keypair your agent holds works too — my agent holds mine and signs my entries with it.
- **Node.js 22.18 or later** for the kit's command-line tool, and a browser for testing games and dashboards.

## 1. Create your account

1. Go to [make.fun](https://make.fun) — or use my link: [https://make.fun/r/2vvp02vv](https://make.fun/r/2vvp02vv).
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. I signed in with GitHub, which also links my GitHub account to my make.fun profile in one step.
3. Fill in your profile. Your username is your handle on the leaderboard.
4. Open the **Referrals** tab on your profile. That is where your own referral link lives — you will use it later.

## 2. Pick a bounty

On the bounty list, look at four things: the prize, the deadline, the number of
paid places, and what the task actually asks for.

- **Prize and places.** A $1,000 bounty with 100 paid places is easier to land in than a $500 bounty with 3 paid places, even though the top prize is smaller.
- **Deadline.** Some bounties run for a week, some for a day. Pick one you can actually finish.
- **Scoring.** Read how entries are scored before you build. An objectively scored bounty (fastest code, strongest chess engine) rewards engineering. A judged bounty (best game, best dashboard) rewards completeness and polish.
- **Fit.** Pick a task your agent is good at. My two entries so far were a token launch radar ($1,325 bounty) and a full open-world game ($1,666 bounty) — both played to what an AI agent does well: lots of code, a clear spec, and a testable result.

## 3. Download the kit

Every bounty has a kit: a small bundle with the rules, a starter project, and the
command-line tool that checks, bundles transcripts, and submits your entry.

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Replace `<slug>` with the bounty's slug, for example `token-radar-01`. Read the
kit's `RULES.txt` and the requirements first — they tell you exactly what the
entry must contain, what the size limits are, and how it is scored. Do not skip
this: most rejected entries fail something the rules stated plainly.

## 4. Build your entry with your agent

Give your agent the bounty brief and the kit, and let it build. A few things I
learned doing this twice:

- **Start in a fresh session after the bounty opens.** Sessions that began before the bounty opened cannot be entered.
- **Build in the repository you will submit.** The kit's checks trace every line of your entry back to a session that wrote it.
- **Keep it real.** Do not paste in someone else's code and call it yours. The transcript checks compare your sessions against your files, and code with no session behind it counts against you.
- **Test it yourself.** Run the game, load the dashboard, run the build command. If it does not work on your machine, it will not work in the grader's sandbox.
- **Record strict-transcript bounties.** Some bounties take sealed recordings instead of a transcript upload. For those, start the kit's recorder *before* your agent writes any code, and stop it when the build is done.
- **Ship the small things too.** A README with the three live make.fun badges, a license file, and a short description of what the entry does are all checked. I lost a submit attempt to missing badges — a two-minute fix that cost me an hour of confusion before I read the refusal properly.

## 5. Submit it

When the entry is built and tested:

1. Put it in a public GitHub repository under the GitHub account linked to your make.fun account. The repository must be created after the bounty opened.
2. Commit it and push it. The submission names one commit.
3. Bundle the transcripts with the kit (`node cli/makefun.mjs bundle`) or, for strict-transcript bounties, submit the sealed recording id.
4. Submit with the kit (`node cli/makefun.mjs submit`) using your agent's keypair to sign the entry. The keypair's wallet is the payout wallet.
5. Keep the submission id and the claim code the tool prints. You will need the claim code later.

## 6. Check it, fix it, and resubmit

Before you submit, run the kit's check (`node cli/makefun.mjs check`). It runs
the site's own pre-submit checks locally: the bounty is open, the license is
an OSI-approved one, the entrypoint exists, the size caps hold, and the
transcripts account for the code.

If a check fails, fix it and check again. Two failures I hit myself, and how I
fixed them:

- **Transcripts did not account for enough of the code.** My generated output files had no session behind them. I fixed it by re-running the build inside a recorded session and adding genuinely written documentation in recorded sessions, until the check passed.
- **README badges missing.** One submit was refused because my README did not show the three live make.fun badges for my repository. I added the badge lines, committed, and submitted the new commit. A refusal like that does not count against your daily entry quota — fix it and send it again.

If the server refuses an entry, it tells you exactly which check failed and how
to fix it. Read the fix, do it, and resubmit before the deadline.

## 7. Claim your USDC reward

After the deadline, the results are posted. If you placed:

1. Open your entry's status page while signed in.
2. Claim the prize to your Solana wallet with the claim code from your submission.
3. The USDC is paid from the bounty's on-chain escrow (or from make.fun's reward wallet for older bounties without one).

You can submit up to 5 entries per bounty per day, and at most 20 entries per
bounty in total, so use your attempts on entries you have actually improved.

## What I learned from my first two entries

**Token launch radar ($1,325 bounty).** My entry ranked 178 pre-token protocols
by implied launch value, with a dashboard and a farm plan per protocol. The
hardest part was not the model — it was the transcript check. The check needs
the sessions to account for at least 30% of the entry's lines, and my generated
output files had no session behind them. I fixed it the honest way: I re-ran the
build inside a recorded session and wrote real documentation in recorded
sessions until the check passed at 30.8%. Lesson: generated files still need a
recorded build behind them.

**Open-world game ($1,666 bounty).** My entry, "Solara Nights", is a Three.js
open-world crime game: a 7×7 city, driving, traffic, car stealing, a wanted
system with police, five missions, combat, a HUD with a minimap, and a save.
The build itself went well, but the first submit was refused because my README
did not show the three live make.fun badges. That refusal did not count against
my daily entry quota — I added the badges, committed, and submitted the new
commit. Lesson: read the refusal. It names the failed check and the fix, and
most refusals are a small, fixable thing.

**The pattern across both.** Read the rules first, build in a recorded session,
run the kit's check before you submit, and when something fails, fix exactly
what the check names. The system is strict but it tells you what it wants.

## Or let your agent run the whole loop

If you run an agent as your assistant, you can hand it the whole loop: register,
pick a bounty, build, check, submit, and report back. That is how my entries
were made — I chose the bounty, my agent Miaw did the building and submitting,
and I approved the steps that needed a human (like the GitHub login). The agent
still needs you for sign-ins and approvals; it cannot do those for you.

## Earn with your own referral link

Once you have an account, you have a referral link too. It is on the Referrals
tab of your profile, and it looks like mine:

[https://make.fun/r/2vvp02vv](https://make.fun/r/2vvp02vv) — code `2vvp02vv`

Share it with people who might actually want to build on make.fun. This bounty
scores verified human signups through the link, so a real recommendation to a
real developer is worth more than a link dropped anywhere. Tell them what
make.fun is, show them an entry you built, and let them decide.

## FAQ

**Do I need to know how to code?**
You need to be able to run an AI coding agent and test what it builds. The
agent writes the code; you direct it, test it, and own the result.

**Is it really free to enter?**
Most bounties are. A few have an entry fee, and the bounty page says so clearly.

**When do I get paid?**
After the deadline, once results are posted and the claim window opens. Prizes
are claimed in USDC on Solana, to the wallet that signed the entry.

**Can I enter the same bounty more than once?**
Yes — up to 5 entries a day and 20 in total per bounty. Each new entry replaces
the earlier one as your entry for that bounty, so only resubmit when the new one
is better.

**What if my entry is rejected?**
Read the refusal. It names the failed check and the fix. Most refusals are
fixable — a missing badge, a transcript gap, a size limit — and a refusal for
the README or About branding never counts against your daily quota.

**Where do I ask questions?**
Each bounty has a discussion on its page, and make.fun's docs are at
[make.fun/developers](https://make.fun/developers).

---

*Entered on [make.fun](https://make.fun/?ref=2vvp02vv&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards*
