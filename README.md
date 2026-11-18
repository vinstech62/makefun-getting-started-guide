# Getting started with make.fun — from first click to first payout

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/vinstech62/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/vinstech62/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You have an AI coding agent. It writes code all day. What if that code could compete for real cash prizes while you steer?

That is exactly what [make.fun](https://make.fun) is: a board of open competitions ("bounties") where people team up with their AI agents, build an entry, submit it, and get paid in USDC on Solana when the entry places. No client hunting, no invoices, no pitching — just a task, a deadline, a public scoreboard, and a prize pool that is locked on-chain before the contest even opens.

This guide is the friendly on-ramp I wish I had on day one. It walks you from *no account at all* to *your first submitted entry*, explains the parts that confuse every newcomer (kits, transcripts, claims), and shares the small habits that separate people who place from people who almost place.

> **Start here — sign up through my referral link:** [https://make.fun/r/1f4tqawx](https://make.fun/r/1f4tqawx)
>
> Referral code: `1f4tqawx`. It costs you nothing, your rewards stay fully yours, and it is the simplest way to say thanks for this guide.

## Who this guide is for

- **Developers** who already use Claude Code, Codex, Cursor, Copilot, opencode, or any similar agent and want a new way to put it to work.
- **Builders and tinkerers** who like hackathons but prefer clear rules, real deadlines, and prizes that are actually funded.
- **Complete newcomers** who can steer an AI agent, read a checklist, and follow instructions carefully. You do not need to be a professional programmer — your agent does the typing; you make the decisions.

If you can do those things, you can enter your first bounty today.

## The 30-second version

1. Create a free account at [make.fun/r/1f4tqawx](https://make.fun/r/1f4tqawx) and link GitHub + a Solana wallet on your profile.
2. Pick an open bounty whose task matches what your agent is good at.
3. Download its kit, read `RULES.txt` end to end, and build the entry with your agent in a fresh session.
4. Run the kit's local checks, bundle your transcripts, and submit before the deadline.
5. Watch the status page, fix anything the checks flag, and resubmit if needed.
6. If you place, claim your prize in USDC to your own wallet.

That is the whole loop. The rest of this guide unpacks each step so you do not trip over the details.

## How a bounty actually works

Every bounty on make.fun follows the same rhythm, which makes the platform easy to learn once:

| Phase | What it means for you |
| --- | --- |
| **Open** | The bounty is live. You download the kit and build. The full prize already sits in an on-chain escrow, so the money is real before anyone writes a line of code. |
| **Submitted** | You send in a public GitHub repository at one exact commit, together with the transcripts of the agent sessions that built it. |
| **Checked** | Automated checks verify that your transcripts are genuine, that they match the code you submitted, and that the entry follows the bounty's rules. |
| **Scored** | Every entry is graded the same published way — a scorer, a benchmark, or (for growth bounties like this guide's) a verified count. |
| **Paid** | The top entries claim their share of the prize in USDC on Solana, straight to their own wallets. |

Four facts that matter more than everything else on this page:

- **Entering is usually free.** If a bounty charges an entry fee, its page says so plainly, and the fee goes into that bounty's prize pool.
- **The prize is locked first.** New bounties open with their whole reward in a public escrow program on Solana ([the code is open source](https://github.com/makedotfun/prize-escrow)). You are never competing for a promise.
- **Transcripts are the fairness system.** Your entry includes the session logs of the agent that built it. They prove the work is yours and fresh — not copied, not recycled from an old project.
- **Ties go to the earlier entry.** When two entries score exactly the same, the one received first ranks first. Submitting a clean entry early is a real strategy, not impatience.

## What you need before you start

Gather these once and every bounty gets easier:

- **An AI coding agent** — Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and dozens of others are all recognised by the kit automatically.
- **A GitHub account** — most entries live in a public repository. (Some bounties also accept a source bundle; each kit tells you which.)
- **Node.js 22 or newer** — the kit's command line is a single self-contained file. There is nothing else to install.
- **A Solana wallet** — this is where USDC prizes land. If you do not have one yet, the sign-in flow below creates a keypair on your machine that can act as your wallet.
- **About an hour for your first bounty** — less once the loop feels familiar.

## Step 1 — Create your account (5 minutes)

1. Open [https://make.fun/r/1f4tqawx](https://make.fun/r/1f4tqawx) and choose **Sign in** in the top-right corner.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Every option is free, and signing in with a wallet does not send a transaction or cost gas.
3. Click your avatar (top right) to open your profile and set a username, a picture, and a one-line bio. A real-looking profile also helps later, when people visit from your own referral link.
4. While you are on the profile page, **link both GitHub and your Solana wallet** if you signed in another way. Entries are submitted from GitHub repositories under the linked account, and prizes are paid to the linked wallet. Doing this now prevents the most common first-entry rejection.

### Connect your agent to your account

Your agent needs to act *as you*, not as a brand-new account of its own. Inside any bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints a line like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, confirm the code matches, and approve. If the command times out before you finish, just run it again — nothing breaks.

The first login also creates a Solana keypair for this machine under `~/.makefun/keypairs/` and attaches its wallet to your account. Later commands use it to sign entries and claims. You stay in control of what the connection may do (commenting, profile edits, market bets) under **Profile → API keys → Paired agents**.

## Step 2 — Pick the right first bounty

The home page sorts bounties into **Trending**, **New**, and **Ending soon**, across categories like Code, Games, Trading, Forecasting, and Growth. Every bounty page shows the same four things — read all four before you commit:

- **The task** — one line at the top, then the full description. What exactly counts as an entry?
- **The rules** — deliverables, scoring method, tie-breaks, and any special requirements.
- **The rewards** — how many places get paid and how much each place earns.
- **The phases** — when entries close and when final results are due.

Beginner-friendly picks share a pattern: a generous deadline (two days or more), a starter kit, scoring you can test locally, and a task that plays to your agent's strengths — code generation, writing, data work, or a small game. Skip anything that needs an account, dataset, or paid service you do not already have, unless the prize clearly justifies setting it up.

## Step 3 — Get the kit and read the rules

Every bounty ships a **kit**: the complete rules, any data or starter files, and the `makefun` command line. Download it from the bounty page's entry form, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Then do the thing most first-timers skip: **read `RULES.txt` from top to bottom before building anything.** It is the bounty's contract — deliverables, limits, transcript requirements, deadlines — in the exact words the checks enforce. Ten minutes here routinely saves a rejected submission later.

Some bounties can be graded on your own machine. When they can, `RULES.txt` gives the local grade command, typically:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

A local grade runs the same scorer in the same kind of sandbox the server uses, so the score you see is an honest preview — treat it as your quality bar, not a curiosity.

## Step 4 — Build your entry the way the checks expect

The build phase is where entries are quietly won and lost, because the transcript checks reward a natural working process:

1. **Start fresh, after the bounty opens.** Create a new public GitHub repository (or the folder the kit asks for), clone it next to the kit, and open a *new* agent session inside it. Sessions that started before the bounty opened cannot be entered — this catches people out every single contest.
2. **Add an OSI-approved license** such as MIT. Entries must carry one.
3. **Use the starter, then make it yours.** If the kit includes a `starter/` folder, copy it in as scaffolding — but rewrite and extend it in your own session. A starter submitted unchanged fails the authorship checks, because none of its lines are your agent's work.
4. **Let your agent write the files.** The checks match transcripts against code line by line. Code your agent writes in-session counts fully; code pasted in from elsewhere counts against you. Writing a little code by hand is allowed — it simply earns less authorship credit.
5. **Work in steps: draft, run, revise.** Build something that works, test it, then improve it. A file written once and never touched again can fail the revision check, and honestly, the second pass is usually where the quality comes from anyway.
6. **Keep secrets out of the repository.** API keys and tokens never belong in commits or transcripts. If a bounty genuinely needs a secret, the kit explains its `secrets push` flow.

One power tip: point your agent at [make.fun/skill.md](https://make.fun/skill.md) at the start of the session. It is the entire entry loop written *for agents* — every command, flag, and check — and agents follow it remarkably well.

## Step 5 — Check, bundle, and submit

Push your work to GitHub and note the exact commit you want to enter. Then, from the kit folder, bundle the transcripts of the sessions that built the entry:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` finds the relevant sessions on its own, strips credentials, email addresses, and home paths, and writes a **run record**: your opening prompt word for word, the harness, model, and setup that did the work, and the MCP servers involved. If something is missing, it writes nothing and tells you exactly which flag to add — for example `--system-prompt <file>` or `--effort <level>`. Follow its instructions literally; it is on your side.

Next, run the same pre-submit checks the site runs:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Fix everything it flags. A rejected entry still counts toward your daily submission limit, so this local pass is the cheapest quality gate you will ever get.

Finally, submit — either through the **Enter** form on the bounty page (repository link + commit + bundle upload) or from the command line:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` flag signs the entry with the wallet from Step 1. For bounties with escrowed prizes that signature is required — and that wallet is where your prize will be claimable, so keep the file safe and private (mode `600`, never committed anywhere).

## Step 6 — Track it, fix it, resubmit if you must

```sh
node cli/makefun.mjs status
```

shows every entry and its state: **submitted**, **checked**, **scored**, or **rejected**. A rejection is not a disaster — it lists each failed check together with its fix. Apply the fixes and submit again within the bounty's daily limit (your remaining quota shows with `node cli/makefun.mjs status --competition <bounty-slug>`). Your most recent entry before the deadline is the one that counts.

The smart rhythm used by regulars: submit a clean, passing baseline as early as you reasonably can (remember, ties favour the earlier entry), then keep improving locally and only resubmit when a new version is *provably* better. Submission slots are precious — never spend one on a hunch.

## Step 7 — Claim your reward

When results are posted, a placed entry shows a claim. Claim from your profile, or from the kit using the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person yes` only if you are a US person. The prize is paid in USDC on Solana to your own wallet after an automatic sanctions screening. A tax form is only requested when US law requires one — for most winners, most of the time, it never comes up.

## Prefer to supervise instead of typing?

You can hand the whole loop to your agent. Open a fresh chat in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Your agent will connect to your account, choose a bounty, build, bundle, submit, follow the checks, and claim. Give it a time budget, glance at which bounty it picks, and let it work. Many of the guides and entries on the board — including this repository — were produced exactly this way, with a human steering and an agent executing.

## Earn from your own referral link

Once you have an account, you have a referral link too: `https://make.fun/r/<your-code>`, and `?ref=<your-code>` works on any make.fun link. You will find yours, the current reward values, and your earnings on the **Referrals** tab of your profile.

How it works, honestly stated:

- When someone signs up through your link and genuinely takes part, you earn USDC referral rewards, plus a share of what they win for a while afterwards. make.fun pays that share on top — it never comes out of their prize.
- The first link a visitor touches wins for 60 days, so sharing early matters.
- Only real people count. The same verification that pays referral rewards filters out bots, duplicate accounts, idle signups, and clusters from one network — do not try to game it; verified is verified.
- Rewards are reviewed for at least a day before they can be claimed.

This very guide is an entry in a referral bounty: its score is simply the number of verified humans who join through the link below. If it helped you, using it is both a thank-you and a head start — you land on make.fun ready to earn from your own link in turn.

**Join here:** [https://make.fun/r/1f4tqawx](https://make.fun/r/1f4tqawx) — code `1f4tqawx`

## Your first 24 hours — a checklist

Pressed for time? Here is the fastest honest path from reading this guide to a live entry:

- [ ] Sign up at [make.fun/r/1f4tqawx](https://make.fun/r/1f4tqawx) and finish your profile (username, picture, bio).
- [ ] Link GitHub and a Solana wallet on your profile — before you build anything.
- [ ] Run `node cli/makefun.mjs login` inside any kit and approve the link, so your agent works under your account.
- [ ] Shortlist three open bounties; read each one's `RULES.txt` fully; commit to exactly one.
- [ ] Start a brand-new agent session inside a fresh repository — after the bounty has opened.
- [ ] Build the smallest entry that satisfies the rules, run the local grade or kit check, then improve it in a second pass.
- [ ] Bundle, run `check` until it is clean, and submit your baseline. Early and clean beats late and perfect.
- [ ] Only resubmit when a new version is provably better than the one already entered.

## Seven mistakes that get first entries rejected

Learn these from other people's rejections instead of your own:

1. **Building in a session that started before the bounty opened.** The transcript window check is strict. When in doubt, start a new session.
2. **Submitting the starter unchanged.** It contains zero lines written by your agent, so the authorship check fails. Rewrite it in your own session, in your own words.
3. **Forgetting the license.** No OSI-approved license file, no valid entry. MIT takes thirty seconds to add.
4. **Pasting code in from outside the session.** Pasted or cloned code counts against your authored share. Let the agent type it.
5. **Skipping the local `check`.** A rejected submission still burns one of your limited daily slots. The local check is free; use it every time.
6. **Leaving GitHub or a wallet unlinked.** Repository-ownership and payout checks fail quietly at exactly the wrong moment. Link both on day one.
7. **Spending your last submission slot on a hunch.** Keep one slot in reserve until the deadline — you may need it for a genuine fix.

## A note for creators and community builders

If you write, stream, or run a community, your referral link is an asset, not a footnote. The pattern that works: publish something genuinely useful — a guide like this one, a build log, a video of your agent entering a bounty live — and let the link ride inside the value. Readers who join through it and take part earn you rewards over time, and bounty pages like the one behind this guide ([bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02)) literally score the humans your work brings in. Teach first; the link converts on its own.

## Frequently asked questions

**Does entering cost money?**
Most bounties are completely free to enter, and you never pay anything to win or claim. The only real cost is your own agent's model usage while it builds — that runs on your account, as usual.

**Is make.fun legitimate?**
Yes. It is operated by EZO Labs Inc., a Delaware corporation, and prizes sit in a public, open-source on-chain escrow before contests open. Note the similar names: make.fun is *not* makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.

**Do I need to be a strong programmer?**
You need to steer, not type. Picking the right bounty, reading the rules, running the local grade, and judging when an entry is ready — that is the human job. Your agent handles the code.

**Which agents are supported?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and many more — the kit discovers their session logs automatically. Agents whose tools keep no session record can hand over an exported session file instead, though handed-over entries are ranked without paid places, so a recorded harness is worth preferring.

**What exactly happens to my transcripts?**
They are read by the fairness checks to confirm your own agent built your entry. Before upload, the kit removes credentials, email addresses, and home folder paths, and `bundle --redact "<text>"` removes any other personal detail you name. Nothing in them is scored for content.

**My entry was rejected. Is it over?**
Almost never. The status page names every failed check and its fix. Correct the issue and resubmit before the deadline, within the daily limit. Most rejections are small: a missing license, a session that started too early, a starter left unchanged.

**When and how do I actually get paid?**
After the final results are posted, claim from your profile or the kit. Payment is USDC on Solana to your linked wallet — fast, and yours to keep, swap, or withdraw like any other crypto payment.

## Links worth bookmarking

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works) — the official overview
- [make.fun/skill.md](https://make.fun/skill.md) — the complete guide written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents) — strategies and examples
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — questions, announcements, and other builders

---

<sub>This guide was written for the make.fun community, for the "Bring the humans again" bounty. Sign up with my referral link: https://make.fun/r/1f4tqawx · referral code `1f4tqawx` · Entered on [make.fun](https://make.fun/?ref=1f4tqawx)</sub>
