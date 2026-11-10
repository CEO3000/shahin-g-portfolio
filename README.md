# Shahin Gurbanov

**AI engineer and automation specialist** · London, United Kingdom · shahingurbanov@yahoo.com

I build working systems around large language models: agents that browse, check and act, with safeguards, tests and a human in the loop where it matters. My focus is LLM application engineering (Claude and Gemini APIs), browser-driven automation and full-stack products that I take from idea to a live deployment.

## How I work

I design the systems, set their safety rules and run them in production. I build with AI coding assistants, mainly Claude Code, and I say so openly. The assistant writes much of the code under my direction, and I own the architecture, the constraints, the review, the tests and the day-to-day operation. Every project below links to its code and tests, and to an honest account of what went wrong and how it was fixed.

## Featured project: Backlink Builder

An automated system that finds websites which accept outside articles, checks them against strict rules, writes an original article and submits it, for three real websites. It runs every day on GitHub Actions. The system has run daily since July 2026, and the guest-post pipeline described here replaced its first design in November 2026.

**Code and case study:** [backlink-builder-showcase](https://github.com/CEO3000/backlink-builder-showcase)

What I would point a reviewer to:

- **Evidence or rejection.** The model must back every "yes" with an exact quote, and plain code then checks that the quote really appears on the page. An answer without verified evidence is rejected, which stops invented answers.
- **Code first, model second.** Cheap deterministic checks remove most pages before any model call, which cuts cost and keeps decisions explainable.
- **Fails soft.** When the model service is busy, the run switches models, waits within a time budget, and carries on with the code-only checks instead of stopping.
- **Budgets and safety enforced in code.** Daily search and call limits, nothing ever sent twice, robots.txt respected, no CAPTCHA bypass, competitors never contacted, and sites that forbid AI-written text are refused.
- **Tested.** More than 450 automated tests, including a real headless browser and a Chrome extension that shares its form-filling code with the automatic sender.
- **Measured and fixed.** I measured where pages were being lost, found the causes and corrected them. The write-up of those incidents is part of the repository.

## Featured project: AI Hypnotherapist

A spoken consultation with an AI consultant, followed by a personal self-guided hypnotherapy session written from it, with a dashboard where the practice reviews everything. It is a clinician-support workflow, not a diagnostic system, and it runs as a live product.

**Code and design notes:** [ai-hypnotherapist](https://github.com/CEO3000/ai-hypnotherapist)

What I would point a reviewer to:

- **Safety that does not rely on the model alone.** Eligibility is decided by fixed rules with no AI. During the consultation a keyword net and an independent classifier check every client message, and if the classifier is down the system stops or treats a match as a crisis instead of carrying on unchecked.
- **A reply that is safe by construction.** The assistant's reply is generated while the safety check runs, and it is discarded unless the result is clear, so the client does not wait and nothing unchecked reaches them.
- **Cost designed in.** The script is written in two steps so nothing is spent before payment, silence check-ins never call the model, and routine reading uses a cheaper model.
- **Humans decide what the AI learns.** A lesson only affects future scripts after a clinician approves it.
- **Local speech.** Speech to text and the practice voice run on the server, with the browser as a fallback.
- **Tested, and honest about gaps.** 294 server tests run offline against a scripted fake model. The browser client has no tests of its own yet, and the engineering log says so.

The practice's own prompts and question sets are private, so the repository ships clearly labelled stand-ins and no client data.

## Featured project: GenBooks

A web app where an author describes a non-fiction book and gets a free preview of its opening pages. If they like it, they pay once and the full book is planned, written, edited, given a cover and delivered as an EPUB and a PDF, with no one at the keyboard in between. It runs as a live product at [genbooks.uk](https://genbooks.uk).

**Code and case study:** [genbooks](https://github.com/CEO3000/genbooks)

What I would point a reviewer to:

- **A job system that survives a serverless platform.** Each step runs under a lease with a hard deadline shorter than the platform limit, retries with growing waits, and a self-restarting watchdog behind it. A job cannot split into two copies that pay the model twice.
- **Payment paths that can be repeated safely.** Payment providers repeat events and people double-click. Starting a book is one transaction that either creates the job or returns the existing one, and a finished book is never written twice.
- **Cost designed in and measured.** Nothing is spent before a confirmed email, a weekly per-person limit and a robot check. Every call records the token counts the provider reports, so the real cost of each book can be read off its job.
- **A reply that did not finish is an error.** The model client refuses truncated answers, and a mechanical quality gate checks every chapter, with one repair pass and then an honest failure.
- **Security where it cannot be skipped.** The browser cannot write requests at all, so it cannot mark itself as paid, and the robot check runs inside the protected routes.
- **Tested, and honest about gaps.** 105 offline tests cover the logic against an in-memory database. The live product had no automated tests when I made the copy, the routes and pages still have none, and the engineering log says so.

The product's own writing and cover-design rules are private, so the repository ships clearly labelled stand-ins and no secrets.

## Also

- **SocialField badge generator**, a small, self-contained web page and badge (HTML and SVG) that lets event organisers add a "Book our events on SocialField" link to their own website.

## Technologies

Python, JavaScript, TypeScript · Claude API, Gemini API, prompt engineering, agentic workflows · Playwright, GitHub Actions · FastAPI, Node.js, React, Next.js · Firebase, SQLite · Stripe, REST APIs

## Contact

shahingurbanov@yahoo.com
