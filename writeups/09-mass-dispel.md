# Mass Dispel

- **Difficulty:** ⭐
- **Category:** Miscellaneous
- **Date solved:** 2026-11-25

## The goal

Close multiple "Challenge solved" notifications in one go.

## Background

Every time a challenge is solved, Juice Shop shows a green "You successfully
solved a challenge" banner at the top of the page. After solving a few
challenges in a row, these banners pile up. This challenge isn't about a
vulnerability. It teaches you to **read the documentation**, because the way
to close them all at once is a feature described there.

## What I did

### Step 1: Read the companion guide

I opened the official
[Pwning OWASP Juice Shop companion guide](https://pwning.owasp-juice.shop/companion-guide/latest/part1/challenges.html),
which documents how the app and its challenges work.

### Step 2: Find the notification shortcut

In the guide I found the part about notifications: holding **`Shift`** while
clicking the close button (**X**) on one notification closes all of them at
once.

### Step 3: Apply it

I opened Juice Shop and solved several challenges so that multiple "Challenge
solved" notifications were showing. Then I held `Shift` and clicked the **X**
on one of them. All the notifications closed together, and the challenge was
solved.

## Why it works

Juice Shop is built so that a `Shift` + click on a notification's close button
closes every visible notification, not just that one. It's a documented
convenience feature, and the challenge rewards finding and using it.

## What I learned

- Documentation is part of recon. Guides, help pages and docs often describe
  features and shortcuts you'd never find by clicking around.
- The Juice Shop companion guide is a useful resource when stuck on how a
  feature works.

## Remediation

**Vulnerability:** none. This challenge teaches an application feature, not a
security flaw.

The takeaway for real-world testing:

1. **Read the documentation of the app you're testing.** Hidden features,
   keyboard shortcuts and admin options are often documented somewhere public.
2. **For developers:** remember that anything in public docs will be read by
   attackers too, so don't document features that rely on staying secret.
