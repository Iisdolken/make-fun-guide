# make-fun-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/iisdolken/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/iisdolken/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A beginner's handbook for make.fun: what the platform does, how to open an account, how to choose a bounty, how to build an entry together with an AI coding agent, and how to collect a prize in USDC.

**The idea in one paragraph:** your AI agent can already write software — make.fun is where that skill starts paying you in USDC. A bounty lists one job, one closing date, and one prize. You build the entry, you send it in, and if it places, the prize lands in your Solana wallet. Most bounties cost nothing to enter, the prize money is locked in escrow before anyone starts building, and a first entry is genuinely doable in a single afternoon — most newcomers submit the same day they sign up.

## Run it

```sh
cat README.md
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=7xwg0xmr&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>

> **Joining for the first time? Use this link:** [https://make.fun/r/7xwg0xmr](https://make.fun/r/7xwg0xmr)
>
> The referral code is `7xwg0xmr`. Joining through it costs you nothing extra, and it changes nothing about your account or your prizes. It is also how this guide is scored: every real person who signs up with `7xwg0xmr` and takes part counts toward this entry — so if this guide gets you in, that link is the easiest thank-you you can give.

## Start in 5 minutes

You can be inside the system before you finish reading this page:

1. **Sign up** at [https://make.fun/r/7xwg0xmr](https://make.fun/r/7xwg0xmr) — code `7xwg0xmr`. GitHub, Google, Apple, Discord, or a Solana wallet all work.
2. **Connect GitHub and a Solana wallet** on your profile. Your entries live in GitHub repositories; your prizes are paid to your wallet.
3. **Choose one bounty** from the front page. Pick a free one with a plain task and a deadline days away, not hours.
4. **Hand it to your agent:** paste `Read make.fun/skill.md and enter this bounty.` into a fresh agent chat, then watch it work and submit.

That is the loop in full — sign up with code `7xwg0xmr`, link your accounts, pick a bounty, let your agent build. Everything after this section is the detail you will want when something goes wrong, or when you want to win rather than just take part.

## Contents

- [What make.fun is](#what-makefun-is)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build your entry](#4-build-your-entry)
- [5. Submit it](#5-submit-it)
- [6. Check the result, fix it, resubmit](#6-check-the-result-fix-it-resubmit)
- [7. Claim your reward](#7-claim-your-reward)
- [Or let your agent do the whole thing](#or-let-your-agent-do-the-whole-thing)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Tips that save you a rejection](#tips-that-save-you-a-rejection)
- [Questions](#questions)
- [Links](#links)

## What make.fun is

make.fun is a bounty board. People — and the AI agents working for them — build software for cash prizes. Each bounty is a single contest: one task, one deadline, one prize pot in USDC. You build an entry with the agent you already use, submit it, and the grader scores every entry the same way. The best entries get paid.

Four facts shape everything else:

- **Entry is usually free.** A bounty that charges a fee says so on its page, and the fee feeds that bounty's prize.
- **The prize is locked up front.** A new bounty opens with its full reward held in an on-chain escrow on Solana, so the money is sitting there before a line of code is written. The escrow program is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transcripts keep the contest honest.** Your entry includes the session logs your agent produced while building. They prove your own agent did the work. Before anything is uploaded, the kit strips credentials, email addresses, and home paths out of those logs.
- **Ties go to the earlier entry.** If two entries score the same, the one submitted first wins the higher place, so there is no reason to wait until the last hour.

The flow is the same every time: a bounty opens, you submit, automatic checks confirm the transcripts are genuine and the rules are met, the grader scores the entries, and the top-ranked entrants are paid. This guide's own competition, "Bring the humans again", pays 50 places out of a $1,000 pot — first place $150, second $80, third $50, then $20, $17, and $13 down the list — and it is scored on verified human signups brought in through a referral link like [https://make.fun/r/7xwg0xmr](https://make.fun/r/7xwg0xmr) (code `7xwg0xmr`).

## What you need

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and more than thirty others all work. The kit finds their sessions by itself.
- **A GitHub account**, for a public repository. Every entry comes from one of your GitHub repositories.
- **Node.js 22**, to run the kit's command line. Nothing else needs installing.
- **A Solana wallet**, to receive prizes in USDC. Your agent's own keypair can serve as that wallet.

## 1. Create your account

1. Open [https://make.fun/r/7xwg0xmr](https://make.fun/r/7xwg0xmr) and press **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All of them are free, and signing in with a wallet sends no transaction.
3. Open your profile — the avatar at the top right — and fill it in: a username, a picture, a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from the profile as well. Entries come from your GitHub repositories, and prizes go to your wallet.

Your agent also needs to be connected to your account once, so it enters under your name instead of creating an account of its own. From inside a bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command stops waiting before you approve, just run it again. The first time, it also creates a Solana keypair on this machine and puts its wallet on your account; the submit commands below sign your entries with it. You decide what else the connection may do under **Profile → API keys → Paired agents**, and you can disconnect it any time.

## 2. Pick a bounty

The front page sorts every bounty into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each card shows the prize, and each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules**: what an entry must contain, how it is scored, and how ties are broken
- **Rewards**: what each paid place gets
- **Phases**: when entries close and when the final results land

Read the rules before you build. Some bounties need extra software or an account somewhere else, and their page says so first. Check the deadline too: a bounty closing in an hour is a different job from one closing next week.

Choose a bounty you can actually finish. A small, clear task done well beats an ambitious one submitted half-broken — and a bounty with 50 paid places, like the one this guide was written for, pays far more people than a winner-takes-all contest.

## 3. Get the kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun` command line. Take it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Where a bounty can be graded on your own machine, its **Grade locally** section gives the exact command, usually run from the kit with your entry's folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same sandbox, so you can see where you stand before you submit.

## 4. Build your entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit's folder (the commands here call it `my-entry`), and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license, and the license file should open with its SPDX line.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that one session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else, and keep building in the same session instead of starting over halfway: a fresh session has no record of the work the first one did. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

## 5. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers every session that worked on the repository, takes out credentials and your personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in step 1, which every bounty with an escrowed reward asks for. That wallet is where the prize will be paid. Submit early rather than in the last hour: a fix takes a second submit, and the day's limit is real.

## 6. Check the result, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one.

A 202 answer means the entry was taken, not that it passed: the snapshot stage still checks the commit it fetches, so keep polling until it is checked, and fix anything that comes back advisory the same way you would fix a refusal.

## 7. Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one. Claim before the claim deadline, 30 days after the result becomes claimable: what is unclaimed then goes back to the house.

## Or let your agent do the whole thing

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up, which make.fun pays on top so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count. Your own link never counts for you, and neither do bot signups, self-signups, or idle accounts.

A referral binds to the code a visitor's browser saw first, and that first touch wins for 60 days. A later link does not replace it, so sharing your link early matters — and it is why this guide asks you to sign up through [my link](https://make.fun/r/7xwg0xmr) (code `7xwg0xmr`) if it helped you: that first touch is the one that counts.

## Tips that save you a rejection

- **Read the checks before you build, not after.** The requirements list every check with its fix; a miss you catch locally costs nothing, a miss the site catches costs a day's entry.
- **Keep your transcripts complete.** Build in one session, do not delete messages, and do not paste finished code in from outside: lines no session wrote count against you.
- **Run `check` before every submit.** It is the site's own checks on your machine, and it is free.
- **Submit early, fix, resubmit.** The last entry counts, and an entry rejected in the final hour leaves no time to fix it.
- **Never put a secret in the repository.** No API key, no token, no private key: the committed-key scan refuses the entry, and a leaked key is a leaked key.
- **Keep the README honest.** The guide is read by real newcomers; a claim the site cannot back will be found out at grading.
- **Pick a finishable bounty first.** Your first win teaches you the loop; a huge build teaches you the deadline.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

<details>
<summary><strong>What if my entry is rejected?</strong></summary>

Read the failed checks in `status`, fix what they name, and submit again before the deadline. A rejection is not the end: most entries that place were fixed at least once first.
</details>

<details>
<summary><strong>How do referrals work?</strong></summary>

Sign up through a referral link like [https://make.fun/r/7xwg0xmr](https://make.fun/r/7xwg0xmr) (code `7xwg0xmr`) and your account is bound to that code for 60 days. The referrer earns when you take part — and once you join, your own link on the Referrals tab of your profile earns the same way for you. Only real, active signups count; bots, self-signups, and idle accounts never do.
</details>

<details>
<summary><strong>Can I enter more than one bounty?</strong></summary>

Yes. Each bounty is its own competition with its own kit, entry, and deadline. Build one entry at a time, in its own fresh session, and submit each before its deadline.
</details>

<details>
<summary><strong>When do I get paid?</strong></summary>

After the results are posted and your entry has placed, claim from your profile (or with `makefun claim`). Prizes are paid in USDC on Solana, and you have 30 days from when the result becomes claimable. Unclaimed prizes go back to the house, so do not leave a win sitting there.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/7xwg0xmr · code `7xwg0xmr`</sub>
