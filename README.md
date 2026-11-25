# OWASP Juice Shop – My CTF Journey

This repo is where I document my progress solving the challenges in
[OWASP Juice Shop](https://owasp.org/www-project-juice-shop/), a deliberately
insecure web application built for learning web security.

I'm learning as I go, so I'll take it slow: one challenge at a time, writing down
what I tried, what worked, and what I learned.

## What is OWASP Juice Shop?

Juice Shop is a fake online juice store that is full of real-world security
vulnerabilities on purpose. It covers the
[OWASP Top 10](https://owasp.org/www-project-top-ten/) and more, for example:

- Injection (SQL injection, NoSQL injection)
- Broken authentication
- Cross-Site Scripting (XSS)
- Broken access control
- Sensitive data exposure
- Security misconfiguration

Challenges are rated from ⭐ (easy) to ⭐⭐⭐⭐⭐⭐ (very hard). A built-in
**Score Board** tracks which ones are solved.

## Goals

- Understand how common web vulnerabilities work
- Practice using browser DevTools and tools like Burp Suite
- Write a clear writeup for every challenge I solve
- Work my way up from 1-star to harder challenges

## Getting started

See [SETUP.md](SETUP.md) for how to run Juice Shop locally.

## Repo structure

```
.
├── README.md        # This file
├── SETUP.md         # How to install and run Juice Shop
├── PROGRESS.md      # Checklist of challenges solved
├── REVISIT.md       # Challenges I want to redo on my own
├── screenshots/     # Screenshots used in the writeups
└── writeups/        # One file per challenge
    └── _TEMPLATE.md # Template to copy for each new writeup
```

## Progress

Tracked in [PROGRESS.md](PROGRESS.md). Challenges I want to go back to are
listed in [REVISIT.md](REVISIT.md).

## Disclaimer

Everything here is done against my **own local copy** of Juice Shop, for
learning purposes only. Never use these techniques on systems you don't own or
don't have explicit permission to test.

## Resources

- [Official Juice Shop project](https://owasp.org/www-project-juice-shop/)
- [Pwning OWASP Juice Shop (official guide book)](https://pwning.owasp-juice.shop/)
- [Juice Shop on GitHub](https://github.com/juice-shop/juice-shop)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
