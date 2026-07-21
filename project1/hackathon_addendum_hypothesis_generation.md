# Addendum: Challenge 3.5 – From Variants to Hypotheses

## Rationale

Challenges 1–3 audit AI as a **workflow generator** (Google Antigravity producing
commands, parameters, and pipelines). This addendum introduces a second, distinct
AI role: AI as a **scientific reasoning partner**, using Google's Hypothesis
Generation tool (built on Co-Scientist).

The two tools fail in different ways and need different audit skills:

| | Antigravity-style output | Hypothesis Generation output |
|---|---|---|
| What it produces | Code, commands, pipelines | Candidate biological explanations |
| How it can be wrong | Wrong parameters, silent bugs, non-reproducible steps | Plausible-sounding but ungrounded, untestable, or already-known claims |
| How you check it | Re-run it, compare outputs, diff results | Check citations, check testability, check novelty vs. known literature |

Running both audits back-to-back gives participants a much richer picture of
"trust but verify" than auditing code alone.

**Access note:** Hypothesis Generation currently requires registration at
labs.google/science and is being rolled out gradually. Confirm access for at
least one device per team before hackathon day — treat it as an optional
extension challenge if access isn't available to everyone.

---

# Challenge 3.5 – Generate and Audit a Hypothesis

[#challenge-35--generate-and-audit-a-hypothesis](#challenge-35--generate-and-audit-a-hypothesis)

## Goal

[#goal](#goal)

Use the team's own validated Project 1 results (from Challenges 1–3) as the
starting point for AI-assisted scientific interpretation, then audit that
output with the same rigour applied to the code audit.

## Steps

1. From your reproduced/corrected variant calling results, identify one
   finding that invites biological explanation (e.g. an unexpected
   variant density in a region, a discordant call between callers with a
   plausible biological cause, a candidate resistance or pathogenicity
   variant).
2. Frame it as a research goal in plain language, e.g.:
   *"Given [specific finding] in [organism/gene/region], what mechanisms
   could explain this, and how would you test them?"*
3. Submit this goal to Hypothesis Generation and let it run its
   generate–critique–rank cycle.
4. Record the top 2–3 ranked hypotheses it returns, along with any cited
   sources.

## Audit questions

For each hypothesis returned, determine:

- Is it grounded in your actual data, or could it apply to almost any dataset?
- Are the cited sources real and relevant (spot-check at least one)?
- Is it testable with a concrete next experiment, or too vague to act on?
- Is it genuinely novel, or just restating textbook knowledge?
- Would you, as a reviewer, recommend pursuing it — and why or why not?

Deliverable:

A short hypothesis audit note (half a page): the research goal you posed,
the hypotheses returned, and your team's verdict on each.

---

# Updated Judging Criteria

[#updated-judging-criteria](#updated-judging-criteria)

If adopting this addendum, adjust the scoring table:

| Category                        | Points  |
| -------------------------------- | ------- |
| Scientific accuracy              | 25      |
| Reproducibility assessment       | 15      |
| Quality of AI audit (workflow)   | 15      |
| Quality of AI audit (hypothesis) | 10      |
| Workflow improvements            | 15      |
| Teaching activity                | 10      |
| Presentation                     | 10      |
| **Total**                        | **100** |

---

# Extending Challenge 4 (Teach the AI)

[#extending-challenge-4-teach-the-ai](#extending-challenge-4-teach-the-ai)

Suggested addition to the lesson-design brief: ask teams to design their
15-minute activity around **comparing failure modes** of the two AI roles
(code-generation vs. hypothesis-generation), rather than treating "AI in
genomics" as a single undifferentiated thing. This directly reinforces the
hackathon's key message that responsible AI use requires recognising *which
kind* of claim is being made and *which kind* of verification it needs.

---

# Extending the Reflection Session

[#extending-the-reflection-session](#extending-the-reflection-session)

Additional suggested question:

- Auditing code and auditing a scientific hypothesis require different
  skills — which was harder for your team, and why?
