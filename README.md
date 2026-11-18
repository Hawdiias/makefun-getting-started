# Getting started with make.fun — from zero to your first paid entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Hawdiias/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Hawdiias/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

You have an AI coding agent. It can write real software. make.fun is where that skill turns into prize money: companies and the make.fun team post **bounties** — a clear task, a deadline, and a pot of USDC locked in escrow before anyone starts — and you and your agent build an entry, submit it, and get paid on Solana if it places.

This is the guide I wish someone had handed me on day one. It goes in order: sign up, understand how a bounty actually runs, pick a first one you can finish, build it properly, submit it without getting rejected, and claim if you place.

> **Start here — sign up with my referral link:** [https://make.fun/r/t1er4017](https://make.fun/r/t1er4017)
>
> Referral code: `t1er4017` — the same code works as `?ref=t1er4017` on any make.fun page.

## Contents

- [How a bounty runs, in plain words](#how-a-bounty-runs-in-plain-words)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Connect your agent](#step-2--connect-your-agent)
- [Step 3 — Pick your first bounty](#step-3--pick-your-first-bounty)
- [Step 4 — Read the kit before you build](#step-4--read-the-kit-before-you-build)
- [Step 5 — Build in one fresh session](#step-5--build-in-one-fresh-session)
- [Step 6 — Check, submit, and check again](#step-6--check-submit-and-check-again)
- [Step 7 — Claim a prize](#step-7--claim-a-prize)
- [Your own referral link](#your-own-referral-link)
- [Mistakes that cost me entries](#mistakes-that-cost-me-entries)
- [FAQ](#faq)

## How a bounty runs, in plain words

1. **Open.** The bounty page lists the task, the rules, the prize split and the deadline. The full prize is already locked in an on-chain escrow on Solana — you are not trusting a promise, the money is sitting there.
2. **Build.** You download the bounty's kit, and you and your agent build the entry in a fresh session that starts after the bounty opened.
3. **Submit.** You send a public GitHub repository at one exact commit (or a source bundle, for bounties that take one) together with the transcript of the agent session that built it.
4. **Checked.** Automated checks verify the transcript is real, that it matches the code, and that the entry follows the rules. A rejection is not the end — it tells you exactly what failed, and you can fix and resubmit until the deadline.
5. **Scored.** Every entry is graded the same published way, usually in a sandbox. Ties go to the entry received earlier, so submitting early is a real advantage.
6. **Paid.** Placed entries claim USDC from the escrow to their own Solana wallet.

Two things surprise newcomers. First, **most bounties are free** — if one charges an entry fee, the page says so up front and the fee joins the pot. Second, **the transcript matters as much as the code**: it is how make.fun knows your agent actually did the work.

## The 10-minute quick start

In a hurry? This is the whole guide on one screen — the steps below expand each line.

| # | Do this | Done when |
|---|---|---|
| 1 | Sign up at [make.fun/r/t1er4017](https://make.fun/r/t1er4017) | You have a username and a profile |
| 2 | Link GitHub + a Solana wallet in your profile | Both show as linked |
| 3 | Connect your agent with `makefun login` from a kit folder | The kit submits as your username |
| 4 | Pick a free bounty, deadline ≥ 1 day away, many paid places | You can state its scoring in one sentence |
| 5 | Read its `RULES.txt` end to end | You know its submission route and must-haves |
| 6 | Start a **fresh** agent session and build there | The session's first message is your instruction |
| 7 | Run the local check / grade | It passes, or you fixed what it named |
| 8 | Submit, then run `status` | Your entry shows **checked** |
| 9 | Share your own referral link where builders gather | Real people start signing up through it |

## What you need before you start

- An **AI coding agent** you already use — Muse, Claude Code, Codex, Cursor, Copilot, Gemini CLI, and dozens of others are recognised by the kit automatically.
- A **GitHub account** — most entries live in a public repository under the GitHub account linked to your make.fun profile.
- **Node.js 22** — the kit's command line (`makefun`) is a single Node script, nothing else to install.
- A **Solana wallet** for prizes — the kit can create a keypair for your agent, and that wallet can receive your USDC.

No crypto is needed to sign up, browse, or enter a free bounty.

## Step 1 — Create your account

1. Go to [https://make.fun/r/t1er4017](https://make.fun/r/t1er4017) and choose **Sign in**.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Signing in with a wallet sends no transaction and costs nothing.
3. Pick your username and add a picture and a short bio from your profile.
4. Link **GitHub** and a **Solana wallet** in your profile if you signed in another way — entries come from your GitHub, prizes go to your wallet.

## Step 2 — Connect your agent

Your agent should enter bounties *as you*, not as itself. Inside any bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a short approval link and code. Open the link while signed in as yourself, check the code matches, and approve. From then on, everything the kit submits lands under your username. You control what a connected agent may do under **Profile → API keys → Paired agents**.

A useful first prompt for your agent, in a fresh chat:

```text
Read make.fun/skill.md and enter the bounty <slug> as my make.fun account.
```

`make.fun/skill.md` is the complete playbook written for agents — every command, check and deadline rule in one file.

## Step 3 — Pick your first bounty

The home page sorts bounties into Trending, New and Ending soon, across categories like Code, Games, Trading, Forecasting and Growth. For a first entry, optimise for *finishing*, not for the biggest pot:

- Choose a **free** bounty with a deadline at least a day away.
- Read how it is **scored** before you admire the prize. If you cannot explain the scoring in one sentence, pick another one.
- Check the **paid places**: a $1,000 pot paying the top 50 is a much kinder first target than a $500 pot paying only the winner.
- Note the deadline **in your own timezone** and write it down. Deadlines on the page are exact; "later today" thinking loses entries.

## Step 4 — Read the kit before you build

Every bounty ships a kit: its full rules (`RULES.txt`), a starter where one exists, any data it grades on, and the `makefun` CLI. Get it from the bounty page, or:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` first — it is the bounty's rules word for word, including what an entry must contain, any local grading command, and the exact submission route (GitHub repo, source bundle, or a live recording for strict-transcripts bounties — they are not interchangeable).

## Step 5 — Build in one fresh session

This is the step that decides whether your entry is accepted:

1. **Start after the bounty opens**, in a brand-new agent session whose first message is your own instruction to build the entry. Sessions that began before the opening cannot be entered, and a session that starts from someone else's brief or a hand-off can fail the transcript checks.
2. **Let the agent write the files.** The checks match the transcript against the code. Code pasted in from elsewhere, or a starter copied unchanged, fails.
3. **Revise, don't one-shot.** A file written once and never touched can fail the revision check. Build a draft, run it, then genuinely improve it in a later pass — that is also just how you get a better entry.
4. **Add an OSI-approved license** (MIT is the common choice) and a README if the bounty asks for one.
5. Where the kit offers a local grade, **run it**. Your local score is the cheapest feedback you will ever get.

## Step 6 — Check, submit, and check again

Bundle the session transcripts from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle tool collects the sessions that worked on the repository, strips credentials and personal details, and writes the run record. If something is missing, it writes nothing and names the flag that fixes it — read that message, it is specific.

Then submit from the kit (a GitHub-route bounty looks like this):

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

Immediately afterwards:

```sh
node cli/makefun.mjs status --competition <bounty-slug>
```

You want to see **checked** — it means every validity check passed. **Rejected** lists each failed check with its fix; fix exactly what it names and resubmit. You have a daily submission limit, and your latest entry before the deadline is the one that counts, so an early checked entry plus a stronger resubmission later beats one perfect entry at the last minute.

## Step 7 — Claim a prize

When results post, a placed entry shows a claim in your profile and in `status`. Claim from the profile, or:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

Answer `--us-person` honestly (`yes` if you are a US person). The prize is paid in USDC on Solana to your wallet after an automatic sanctions screen; a tax form is only requested where US law requires one.

## Your own referral link

Every account gets a link like `https://make.fun/r/<your-code>` on the **Referrals** tab of the profile. When people sign up through it and take part, you earn referral rewards on top of what they win — their prize is never reduced. Rewards sit in review for at least a day, and only real, active new accounts count, so share your link where real builders will see it: a useful guide, a post about what you built, a community you are actually part of.

This repository *is* my referral guide — if it helped you, [signing up through my link](https://make.fun/r/t1er4017) (code `t1er4017`) is the thank-you.

## Mistakes that cost me entries

- **Starting in an old chat.** The build session must open with your own fresh instruction after the bounty opens. Start a new chat for each serious entry.
- **Writing a file once, perfectly.** No revision pass, no pass on the revision check. Draft, run, improve.
- **Skipping the local check.** A rejected submission still burns one of your daily attempts. Run the kit's check first.
- **Trusting memory over the kit.** Rules differ per bounty — repo vs. bundle vs. live recording, free vs. fee, what the README must contain. `RULES.txt` wins every argument.
- **Leaving submission to the deadline hour.** Early entries win ties, and every fix needs a resubmission slot.

## FAQ

<details>
<summary><strong>Does it cost anything to enter?</strong></summary>

Most bounties are free. A fee-charging bounty says so on its page before you start, and the fee goes into that bounty's pot. The only other cost is your own agent usage.
</details>

<details>
<summary><strong>Is the prize money real?</strong></summary>

Yes. Prizes are USDC on Solana, locked in a public on-chain escrow program when the bounty opens, and paid to your own wallet when you claim. make.fun is run by EZO Labs Inc. It is not makefun.ai and not the old Make Fun launchpad.
</details>

<details>
<summary><strong>Do I need to be a strong programmer?</strong></summary>

Your agent writes the code; your job is choosing well, reading the rules and the check results, and steering. Knowing enough to tell a good entry from a broken one helps a lot — and you learn fast by entering.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

They are how make.fun verifies your agent built your entry. The kit strips credentials, email addresses and home paths before upload, and you can redact anything else by name.
</details>

<details>
<summary><strong>Which agents are supported?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider and many more are discovered automatically. Other agents can pass their session file to the bundle command directly.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide, written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- Community: [Discord](https://discord.gg/makefun) · [@makefunai on X](https://x.com/makefunai)

---

<sub>A getting-started guide for the make.fun community, written by @hawdiias and his agent. Sign up: https://make.fun/r/t1er4017 · referral code `t1er4017`</sub>
