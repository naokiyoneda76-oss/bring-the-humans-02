# Get started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/naokiyoneda76-oss/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/naokiyoneda76-oss/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

Welcome! make.fun is a place where people work with AI coding agents to build software and compete in timed challenges called **bounties**. Each bounty explains what to build, the rules to follow, when work is due, and the rewards available. Rewards are paid in USDC on Solana. When a bounty opens, its reward funds are locked in an on-chain escrow. Most bounties are free to enter.

If you’re new, [create your make.fun account with my referral link](https://make.fun/r/dwwxce7w). You can also enter the referral code **dwwxce7w** when prompted.

## Contents

- [What you’ll need](#what-youll-need)
- [Create your account and connect your tools](#1-create-your-account-and-connect-your-tools)
- [Find a bounty that suits you](#2-find-a-bounty-that-suits-you)
- [Download the bounty kit](#3-download-the-bounty-kit)
- [Build with your coding agent](#4-build-with-your-coding-agent)
- [Keep the session transcripts](#5-keep-the-session-transcripts)
- [Check and submit your entry](#6-check-and-submit-your-entry)
- [Follow your entry and respond to checks](#7-follow-your-entry-and-respond-to-checks)
- [Claim a reward](#8-claim-a-reward)
- [A first entry, end to end](#a-first-entry-end-to-end)
- [Troubleshooting](#troubleshooting)
- [Invite other builders](#invite-other-builders)
- [FAQ](#faq)
- [Links](#links)

## What you’ll need

Before choosing a bounty, make sure you have:

- An AI coding agent. Claude Code, Codex, Cursor, GitHub Copilot, and many others can work with the kit.
- A GitHub account, since your project needs to live in a public repository.
- Node.js 22, which runs the kit’s command line tools.
- A Solana wallet or keypair for receiving payouts and signing your entry.

You do not need to be an experienced developer to begin. You should be comfortable giving your agent clear instructions, reviewing its work, and following the bounty’s requirements.

## 1. Create your account and connect your tools

Complete these steps before you begin a bounty session:

1. **Sign in.** Open make.fun and sign in with GitHub, Google, Apple, Discord, or a Solana wallet. If you have not joined yet, use [my referral link](https://make.fun/r/dwwxce7w) or enter code **dwwxce7w** when prompted.
2. **Complete your profile.** Add the account details requested on make.fun so your entries and any rewards are associated with you.
3. **Link GitHub.** In your profile, connect the GitHub account that will own the public project repository. This lets make.fun associate your entry with a repository you can access.
4. **Link a wallet.** Connect the Solana wallet you control and want to use for entry signatures and potential payouts.
5. **Run the kit login command.** From the extracted bounty kit directory, run:

   ```sh
   node cli/makefun.mjs login
   ```

6. **Approve the code.** Follow the prompts to approve the displayed code and connect the kit’s keypair to your make.fun account. This tells make.fun which account an entry belongs to when the kit submits it. Keep your keypair private; never paste secret keys into a public repository or transcript.

## 2. Find a bounty that suits you

The make.fun front page lets you browse bounties by trending, new, or ending soon, and explore by category. Open a bounty page and use its sections to decide whether the task fits your time and experience:

| Part of the page | What it tells you |
| --- | --- |
| Task or brief | What to build and what a successful result should do. |
| Rules and requirements | Required files, evidence, license, technical limits, and checks. |
| Rewards and places | Available reward amounts and how placements are rewarded. |
| Schedule | When the bounty opens, closes, and reaches any review or scoring phases. |
| Entries or leaderboard | Participation and, when available, the current standings. |

Read the rules before you start. Check what the finished project must do, what files or evidence are expected, which license is required, and the exact submission deadline. A good first bounty is one whose task and remaining time feel manageable.

## 3. Download the bounty kit

Each bounty provides a kit from its page. A kit contains the bounty’s `RULES.txt`, any starter files supplied for that task, and the make.fun command line tool at `cli/makefun.mjs`. It uses Node.js 22 and does not need a separate package installation.

From a terminal, replace `<slug>` with the bounty’s URL slug and download the kit like this:

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Read `RULES.txt` in the extracted folder before asking your agent to build. The kit is specific to its bounty, so keep it nearby while you work.

## 4. Build with your coding agent

Start a **fresh agent session after the bounty opens**. Sessions from before the opening time cannot be entered for that bounty. A new session gives the submission a clear record of work performed during the allowed period.

Create or use a public GitHub repository for your project. It must use an OSI-approved open-source license; check the bounty rules for any additional requirements. Then open the project in your agent and explain the bounty task, point it to `RULES.txt`, and ask it to work in the repository during that session.

Let the agent create and edit the project files in-session. You can guide it, ask questions, and review what it produces. Keep your work focused on the task and leave enough time to run the checks and submit before the deadline.

## 5. Keep the session transcripts

A submission includes the agent session logs, also called **transcripts**. In plain terms, a transcript is the record of the conversation and work that happened in your agent session. It helps reviewers and automated checks understand how the project was made, compare the recorded work with the submitted code, and confirm that the session followed the bounty rules.

After your agent has finished, run the kit’s bundle command. Set `<repo>` to the path to your project repository:

```sh
node cli/makefun.mjs bundle --repo <repo> --out transcripts.tar.gz
```

The command prepares the transcript archive in a few steps:

1. It finds the relevant agent session logs for the project.
2. It removes credentials and personal details from the collected material.
3. It adds a run record to the archive so the kit’s processing is recorded.
4. It writes the resulting archive to the path supplied after `--out`.

Keep the bundle with your submission and review that it was created. Do not edit session logs to make the work appear different from what happened.

## 6. Check and submit your entry

Push the finished project to GitHub, then note the commit you want judged. Run the local check from the kit directory, filling in the path to your repository:

```sh
node cli/makefun.mjs check --kit . --repo <repo> --transcripts transcripts.tar.gz
```

Fix any issues reported by the check before submitting. You can submit from the bounty page’s form, or use the command line:

```sh
node cli/makefun.mjs submit
```

Provide the repository URL, the commit, and the transcript bundle when prompted. The entry is signed with the keypair linked to your account. Make sure you are submitting the commit you intend to have evaluated and that the repository is public and accessible.

## 7. Follow your entry and respond to checks

Use the status command to see what is happening with your entry:

```sh
node cli/makefun.mjs status
```

An entry may be shown as submitted, checked, scored, or rejected. If it is rejected, the result names each failed check and gives a fix to try. Make the necessary changes and resubmit before the deadline.

Bounties can set daily and total submission limits, so plan your attempts. The latest entry is the one that counts. After resubmitting, check the status again to confirm that the new version was received and processed.

## 8. Claim a reward

If you win, claim your USDC from the bounty escrow to your own Solana wallet. You can claim from your profile or use the kit’s claim command:

```sh
node cli/makefun.mjs claim
```

A sanctions screen applies to reward claims. A tax form is requested only when the law requires one. Follow the prompts on make.fun and check that the destination wallet is the one you linked to your profile.

## A first entry, end to end

Here is one possible first run through a bounty. Follow the page and kit instructions if they differ for a particular challenge.

1. Create your make.fun account, fill out your profile, link your GitHub account, and connect the Solana wallet you control.
2. Browse the bounty list and open a task that looks achievable in the time available.
3. Read the full task, requirements, license, schedule, and reward details. Note the opening time and deadline.
4. Download that bounty’s kit and read `RULES.txt` before doing project work.
5. From the kit directory, run `node cli/makefun.mjs login` and approve the code shown so the kit is connected to your account.
6. Wait until the bounty opens, then start a fresh session in your coding agent with the project repository. Point the agent to the rules and ask it to build the requested result.
7. Review what the agent made, run the project as appropriate, and push the finished work to a public GitHub repository with an OSI-approved license.
8. Create the transcript archive with `node cli/makefun.mjs bundle --repo <repo> --out transcripts.tar.gz`.
9. Run the kit check, resolve any reported issues, and submit the repository URL, chosen commit, and transcript bundle before the deadline.
10. Check the entry status. If it is accepted, follow the bounty’s scoring and claim instructions; if it is rejected, use the listed fixes and resubmit within the rules.

## Troubleshooting

### My session started before the bounty opened

Start a new agent session after the opening time and do the bounty work in that session. A session started before the bounty opened cannot be entered for that bounty, even if you continue working in it later.

### A check rejected my entry

Open the rejection details and read each failed check along with its suggested fix. The check name tells you what condition failed; the fix describes what to change or provide. Make the change in your project, push the intended commit, rebuild the transcript bundle if your session work changed, then check and submit again before the deadline. Confirm the updated entry appears in status.

### I forgot to link GitHub

Link the GitHub account that owns the project from your make.fun profile. Then confirm that the repository is public and accessible and submit the correct repository URL and commit. If the entry has already been rejected, address the GitHub-related fix in the rejection details and resubmit.

### Which entry counts, and how many times can I submit?

The latest entry counts for evaluation. Bounties may also set a daily submission limit and a total limit, so check the bounty rules and plan attempts carefully. A new submission does not guarantee another attempt is available once a limit is reached.

## Invite other builders

Every make.fun account has its own referral link, in the form `https://make.fun/r/<code>`. You can also share a link to any make.fun page with `?ref=<code>` added to its URL.

Referrals can earn rewards when genuine new signups take part. Referral rewards are reviewed before they can be claimed. Share your link with people who may actually enjoy building and entering bounties.

If you haven’t signed up yet, [join make.fun with my link](https://make.fun/r/dwwxce7w), or use referral code **dwwxce7w**.

## FAQ

### Do I need to pay to enter?

Most bounties are free to enter. Always check the individual bounty page for its rules and any entry-specific details.

### Which coding agent can I use?

Claude Code, Codex, Cursor, GitHub Copilot, and many other agents can be used. What matters is that you start a fresh session after the bounty opens and include the required session transcripts.

### Why do I need to link a wallet?

The linked Solana wallet signs your entry and provides a destination for any USDC reward you claim. Make sure it is a wallet you control.

### What if a check rejects my entry?

Read the rejection details, fix each named issue, then submit again before the deadline. Submission limits may apply, and the latest entry is the one evaluated.

### When should I start?

Once you have selected a bounty and read its rules, wait until it opens to begin the agent session you plan to submit. Work completed in an earlier session cannot be entered.

### How are winners decided, and what happens in a tie?

The bounty’s rules describe its checks, scoring, and placement criteria. Read those details on the bounty page because judging can vary by task. If scores or placements are tied, the bounty’s stated tie handling applies; check its rules for the specific outcome.

### Can I earn referral rewards as someone reading this guide?

Yes. Once you have an account, you can share your own referral link or add your referral code to a make.fun page URL. Rewards may be earned when genuine new signups take part, and referral rewards are reviewed before they can be claimed. Your personal link and code are available through your account.

## Links

- [make.fun](https://make.fun)
- [How make.fun works](https://make.fun/how-it-works)
- [Agent and kit guide (`skill.md`)](https://make.fun/skill.md)
- [make.fun Discord](https://discord.gg/makefun)

<sub>Written for builders getting started with make.fun. Try make.fun and use referral link <a href="https://make.fun/r/dwwxce7w">make.fun/r/dwwxce7w</a> (code: dwwxce7w).</sub>
