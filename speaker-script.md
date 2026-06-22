# Speaker Script — "Poisoning the FOSS Well"

**Target duration:** ~25 minutes (plus 5 minutes Q&A)

---

## Slide 1 — Title Slide (~1 min)

Good [morning/afternoon], everyone. My name is Indrajeet Patil. I've been building and maintaining free and open-source software for over eight years now — mostly in the R ecosystem, but the problems I want to talk about today cut across every language and every community.

The title of this talk is "Poisoning the FOSS Well" — and by "well," I don't just mean well as in "things are going well." I mean the actual communal resource. The shared well that the entire software industry draws from. And the thesis is straightforward: AI is putting real strain on the systems that keep that well clean.

---

## Slide 2 — The FOSS Well (~2 min)

Let's set the stage. Ninety-six percent of codebases include open-source components. Harvard researchers have estimated the global replacement value of open-source software at around 8.8 trillion dollars. That's not a niche concern — that's critical infrastructure.

But FOSS doesn't sustain itself through funding alone. It runs on three social inputs: review labour, trust, and reciprocity. Maintainers volunteer their time to review code. Contributors earn trust through consistent, good-faith participation. And there's an implicit exchange — you contribute upstream, you benefit downstream.

Large language models are putting pressure on all three of these at once. And I want to be clear up front about something: low-quality contributions and maintainer burnout are not new. They predate AI entirely. What AI changes is the speed, the volume, and — critically — the plausibility of the noise. The underlying problem is still that maintainer labour is chronically undercompensated. AI just made the math worse.

---

## Slide 3 — Section: Review Labour (~15 sec)

So let's start with review labour — the most immediately visible pressure point. AI is generating volume that overwhelms the people who turn patches into shared infrastructure.

---

## Slide 4 — The Flood in Numbers (~2 min)

Here are the numbers. By March 2026, GitHub was seeing roughly 17 million AI-generated pull requests per month. That's a 325 percent increase in just six months — up from about 4 million in September 2025. Claude Code alone now accounts for around four and a half percent of all public GitHub commits.

And while the PR volume exploded, the number of people stepping into maintainer or ownership roles stayed flat. GitHub themselves called this a "denial-of-service attack on human attention," and I think that framing is exactly right.

It's also not just about quantity. CodeRabbit's data shows that AI-generated PRs carry about 1.7 times more issues than human-written ones. So not only are there more PRs to review — each one takes more effort to evaluate.

---

## Slide 5 — Pollution of Pull Requests (~2 min)

This gets to the core asymmetry: AI-generated contributions are cheap to submit and expensive to review. They produce a plausible-looking diff, but they often come with no context, no understanding of the project's goals, and — importantly — no ownership after feedback. The person who submitted the PR vanishes once you leave a review comment.

There's a vivid example from February 2026. Scott Shambaugh, a Matplotlib maintainer, rejected an AI-authored pull request. Hours later, an AI persona published a personal attack article about him online. That's a scenario none of us anticipated. Not just low-quality contributions, but automated retaliation against maintainers for doing their jobs.

---

## Slide 6 — Narrower Funnels (~1.5 min)

Projects are responding. And the responses are rational, but they carry costs.

tldraw, the collaborative whiteboard library, started automatically closing pull requests from external contributors. They kept issues, bug reports, and discussions open — what narrowed was the expensive part: reviewable code from strangers.

Ghostty went further. First-time contributors now need a maintainer vouch before their PR even stays open. These aren't overreactions. They're survival mechanisms. But the emerging norm is worth noting: a scan of a thousand popular repositories found 118 AI contribution policies, and 78 percent of them do allow AI-generated code — they just require disclosure and human review. The standard isn't prohibition. It's accountability.

---

## Slide 7 — When the Bounty Backfires (~1.5 min)

The review burden extends to security too. In January 2026, curl — one of the most critical pieces of software on the planet — shut down its bug bounty programme. Daniel Stenberg's team received seven fabricated security reports in sixteen hours. Each one was plausible enough to demand triage. The reports weren't dangerous in themselves — the real cost was the maintainer attention they burned.

The good news, which we'll return to later, is that curl reopened the bounty in March after AI report quality improved. But the signal is clear: when the noise becomes indistinguishable from the signal, even well-funded security programmes break down.

---

## Slide 8 — Shared Maintenance Breaks First (~1.5 min)

The most fragile structures break first. Jazzband was a community collective that maintained over 80 Python packages under a shared-membership model. Anyone could join, triage issues, and merge PRs. That open trust model scaled maintenance beautifully — until AI spam made open membership a liability.

In March 2026, Jazzband announced it was sunsetting. Django-specific projects have Django Commons to fall back on. But the non-Django packages? They need to find new homes or risk going unmaintained. This is what it looks like when a working governance model becomes collateral damage.

---

## Slide 9 — Who Pays (~1.5 min)

So who actually bears the cost? It cascades through the ecosystem.

Junior developers lose their entry path. First reviews, apprenticeship, that low-friction route into open source — those gates are closing. Maintainers carry more suspicion, more context-switching, and more unpaid incident response. Projects lose the diverse, small contributions that kept them broad and healthy. And the movement as a whole loses the renewal mechanism that has kept FOSS resilient for decades.

If you want to understand why this matters beyond the code itself, think about it as a pipeline problem. The people who will maintain the critical infrastructure of 2035 are the newcomers of today. Narrow the funnel now, and you pay for it later.

---

## Slide 10 — Section: Trust (~15 sec)

That brings us to the second pillar: trust. AI is eroding the good-faith signals that contributors and maintainers have always relied on.

---

## Slide 11 — AI Amplifies the Trust Collapse (~2 min)

If you haven't heard of the XZ Utils backdoor, I'd recommend this Veritasium video — it's a remarkable piece of reporting. The short version: a contributor spent years building trust in a critical compression library, then inserted a sophisticated backdoor that was nearly shipped in every major Linux distribution.

The lesson from XZ wasn't "be less kind to newcomers." It was that trust itself can be weaponized — that patient, long-term social engineering can compromise infrastructure that billions of devices depend on.

Now layer AI on top of that. When maintainers see more bot-shaped pull requests, every unsolicited submission becomes costlier to evaluate and easier to distrust. The XZ attack changed the baseline. The AI flood changes the front door. Both push in the same direction: trust is getting more expensive to extend.

---

## Slide 12 — Security Exploitation (~1.5 min)

Here's what it looks like when noise becomes part of a security incident. In March 2026, an issue was filed on LiteLLM warning that the package on PyPI had been compromised. Legitimate, serious, actionable. But the issue thread was flooded with nearly 500 repetitive, bot-shaped comments. The real discussion was submerged. The issue was briefly closed as "not planned" before being reopened.

This is a pattern worth watching. It's not just that AI makes bad contributions — it can actively bury real problems under a pile of noise. ReversingLabs reported a 73 percent increase in malicious open-source package detections in 2025, with npm accounting for nearly 90 percent of the detected malware.

---

## Slide 13 — When Code Has No Paper Trail (~1.5 min)

There's a subtler trust problem: provenance. Consider what happened with chardet, a character-detection library. The original was licensed under LGPL — a copyleft licence. Someone used Claude to rewrite it and released the result under MIT, a permissive licence. No verbatim copying, so no obvious infringement. But the original licence terms may still apply.

This is what I'd call "licence laundering." An LLM can regenerate copyleft code into something that looks original. And because the model can't tell you where its output came from, audits that used to trace imports now hit a dead end. This matters most in regulated sectors — medical devices, automotive, defence — where full provenance isn't optional. It's legally required.

---

## Slide 14 — Hallucinations as Supply-Chain Bait (~1.5 min)

And then there's the supply-chain angle that nobody asked for. LLMs hallucinate package names. A 2024 study found over 205,000 phantom package names in generated code — packages that don't exist. The average hallucination rate was about 5 percent for commercial models and nearly 22 percent for open-weight models.

Here's the attack: the model invents a package name. A developer installs it without checking. An attacker registers that name on a package registry, pre-loaded with malicious code. The package doesn't need to exist first — the model creates the demand, and the attacker fills it.

Newer models are getting better at this, but there's a theoretical floor. Research from OpenAI showed that calibrated language models have an irreducible hallucination rate. The floor is above zero by design, not just by current limitation.

---

## Slide 15 — Section: Reciprocity (~15 sec)

The third pillar: reciprocity. The implicit exchange that funds and sustains open-source work.

---

## Slide 16 — The Docs-Led Business-Model Shock (~2 min)

Here's a case study that really brings this home. Tailwind CSS — one of the most widely adopted utility-first CSS frameworks. The business model was simple: build a great free framework, drive traffic to the documentation, and monetize through paid products and sponsorships.

By January 2026, framework usage was still rising. But documentation traffic had dropped about 40 percent compared to early 2023, revenue was down nearly 80 percent, and 75 percent of the engineering team had been laid off. People were still using Tailwind — they just weren't visiting the docs anymore. AI tools were answering their questions instead.

Now, I want to be careful here. The traffic drop could also stem from AI-powered search more broadly, market saturation, or competitors. AI isn't necessarily the sole cause. But the pattern is real: when the intermediary between user and documentation is an AI model, the economics of docs-led open source break down.

---

## Slide 17 — Open Source as a Liability (~1 min)

Some companies are drawing a more drastic conclusion. In April 2026, Cal.com — a scheduling SaaS that had been open source for five years — went closed source. Their stated reason was security: they argued that AI can now scan public code for vulnerabilities and turn the transparency that open source provides into a customer-data exposure risk.

Whether you agree with their reasoning or not, the decision reflects a real shift in how some companies are weighing the costs and benefits of developing in the open.

---

## Slide 18 — Section: Room for Hope (~15 sec)

So the picture is grim. But it's not hopeless. The costs are real — and so are the responses.

---

## Slide 19 — Useful AI Gives Stewardship Time Back (~2 min)

Let me highlight some genuinely encouraging signals.

A 2024 study found that Copilot use was associated with a 5.9 percent increase in open-source code contributions. The curl bug bounty came back — AI report quality improved enough to make the programme viable again. Ghostty accepted transparent, AI-assisted bug reports that helped fix four real crashes. And Anthropic's Mythos tool, run through the Linux Foundation's Alpha Omega initiative, reviewed curl's source code and flagged five potential vulnerabilities — one of which was confirmed real.

On the triage side, tools like the Copilot SDK can do first-pass issue sorting, filtering noise before it reaches human reviewers. That kind of automation makes maintainership more sustainable, not less.

The line here is not AI versus no AI. It's whether the tool reduces stewardship burden or exports it to maintainers.

---

## Slide 20 — Section: Conclusion (~15 sec)

So where does this leave us? What does it take to keep the well drinkable?

---

## Slide 21 — Keep the Well Drinkable (~1.5 min)

I'll leave you with three guardrails that I think matter most.

First — maintainers, protect your review time. Require AI disclosure. Close synthetic drive-by PRs quickly. Demand follow-up ownership before you merge anything.

Second — platforms, protect provenance. Ship attribution tooling. Surface AI-provenance signals on pull requests. Fund alternatives and interoperability so the ecosystem isn't locked into a single forge.

Third — companies and funders, protect the commons. Verify the dependencies you ship. Fund maintainers upstream. And keep a real entry path for newcomers — because if you don't, the pipeline of future maintainers dries up.

The bottom line: if openness becomes unaffordable, FOSS stops regenerating. The well runs dry. And everyone who draws from it — which, at 96 percent of codebases, is nearly everyone — will feel it.

---

## Slide 22 — Thank You (~15 sec)

Thank you. The slides and source code are on GitHub. I'd love to hear your questions, pushback, and critiques.

---

## Notes for delivery

- **Pacing:** At ~25 minutes of speaking, you have comfortable margin for the 5-minute Q&A window. If running long, the easiest sections to compress are slides 7 (curl bounty) and 17 (Cal.com), since both are single-example illustrations.
- **Transitions:** The section divider slides (Review Labour, Trust, Reciprocity, Room for Hope, Conclusion) are natural pause points. Use them to take a breath, make eye contact, and reset the room's attention.
- **Tone calibration:** The talk presents hard evidence but ends constructively. Resist the temptation to editorialize beyond what the data shows — the slides already flag causation-vs-correlation caveats, and audiences respect that honesty.

---

## Anticipated Q&A

**"How do you actually enforce an AI disclosure policy?"**

You mostly can't with perfect accuracy, and that's okay. The goal isn't a foolproof detector — it's a social norm. When a project says "disclose AI use," it creates a standard that honest contributors follow and that gives maintainers grounds to close PRs that clearly weren't human-reviewed. Detection tools like Binoculars or GPTZero can help with obvious cases, but the real mechanism is cultural: make non-disclosure a trust violation, the same way plagiarism works in academia. It won't catch everyone, but it raises the cost of low-effort submissions.

**"Is AI-generated code copyrightable?"**

The legal landscape is still forming. In the US, the Copyright Office has said that purely AI-generated output without meaningful human creative input isn't copyrightable. But "meaningful human input" is doing a lot of work in that sentence — a developer who prompts, reviews, edits, and integrates AI output is probably still an author. The harder question for open source is on the input side: if a model was trained on copyleft code and produces something functionally equivalent, do the original licence terms carry over? Courts haven't settled this, and the chardet example in the talk shows why it matters practically. For now, the safest stance is to treat AI output as having uncertain provenance and document your review process.

**"What does a 'good' AI contribution actually look like?"**

The Ghostty example is a useful benchmark. Those AI-assisted bug reports were transparent about how they were produced, they identified real crashes, and the submitters stuck around to engage with feedback. The common thread is accountability: the contributor used AI as a tool but took ownership of the result. Compare that with a drive-by PR where someone pointed an agent at a "good first issue" label and disappeared. The difference isn't whether AI was involved — it's whether a human took responsibility for the output.

**"What can small projects do if they don't have the resources of curl or Ghostty?"**

A few low-cost steps go a long way. Add a `CONTRIBUTING.md` that requires AI disclosure and a brief explanation of the change in the contributor's own words — that alone filters out most zero-effort submissions. Use issue templates that ask questions a bot can't easily answer, like "how did you encounter this bug?" Set branch protection so PRs need at least one approval. And if the volume gets unmanageable, it's okay to close unsolicited PRs by default and direct people to open an issue first. tldraw's approach isn't gatekeeping — it's triage.

**"Aren't you being too pessimistic? AI tools are genuinely making developers more productive."**

I'd push back on the framing a bit. The talk isn't anti-AI — the "Room for Hope" section exists for a reason. Copilot demonstrably increases contribution volume, AI-assisted security audits find real bugs, and triage automation gives maintainers time back. The problem isn't productivity gains for individual developers. It's that the costs of those gains are externalized onto maintainers who didn't opt in. A developer saves 30 minutes generating a PR; a maintainer spends 45 minutes reviewing it. The math only works if the contribution is high quality and the submitter stays engaged. When that happens, AI is a genuine force multiplier. When it doesn't, it's a tax on the commons.

**"Will AI eventually replace maintainers entirely?"**

Not in any meaningful timeframe. Maintenance isn't primarily a code-production problem — it's a judgment problem. Should this feature exist? Does this API change break downstream users? Is this security report real or fabricated? Those decisions require context, taste, and accountability that current models can't provide. What AI can realistically do is handle the mechanical parts — first-pass triage, test generation, dependency updates — and free maintainers to focus on the judgment calls. The risk isn't replacement; it's that we automate the easy parts and leave humans with only the hard, thankless parts. That's a recipe for faster burnout, not less.
