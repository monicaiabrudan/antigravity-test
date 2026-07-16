# Facilitator's Guide

## Human vs AI: Auditing a Variant-Calling Workflow

*A Train-the-Trainer Module for the Genome Sequence Analysis Course*

| | |
|---|---|
| **Based on** | Project 1: Comparison of variant callers (bcftools, FreeBayes, GATK) |
| **Duration** | ≈ 3.5–4 hours |
| **Audience** | Researchers training to become course trainers — builds genomics facilitation skill and AI-tool critical literacy together |
| **Group size** | 4–6 per working group, run in parallel |
| **Source materials** | Course: wcscourses.github.io/Genome-Sequence-Analysis-Standardised-Resources · Comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project1 |

---

## 1. Purpose & Learning Objectives

This module reuses the existing Project 1 dataset and task list, but reframes it as a comparison exercise: a human group solution (1.5h) against an AI-agent solution (Google Antigravity, ≈10 min). The goal is not to crown a winner — it's to build a repeatable format that trainees can run themselves, teaching both variant-calling literacy and structured AI critical-evaluation.

By the end of the session, participants will be able to:

- Explain how bcftools, FreeBayes and GATK differ in variant discovery, and why ts/tv ratio functions as a QC proxy.
- Audit an AI-generated bioinformatics analysis against a structured rubric rather than accepting it at face value.
- Facilitate a "human vs AI" comparison exercise with a group, including handling disagreement and uncertainty.
- Design and deliver their own version of this exercise for a different course module.

## 2. Session at a Glance

| Phase | Time | Format | Output |
|---|---|---|---|
| 1. Framing | 15 min | Plenary | Shared framing of the exercise; ground rules set |
| 2. Re-anchor in the human solution | 30–45 min | Plenary / small group | Refreshed content mastery; gold-standard answers on the table |
| 3. Blind audit of the AI output | 60–75 min | Small groups | Completed rubric per group |
| 4. Reveal & reconcile | 15 min | Plenary | Group scores compared to the published comparison |
| 5. Trainer debrief (meta layer) | 30 min | Plenary | Shared list of design principles |
| 6. Teach-back practice | 60–90 min | Pairs + peer feedback | Draft mini-activity for another module + feedback notes |

*Total: ≈ 3.5–4 hours, including breaks. Phases 3–4 can be compressed to 60 min combined if running the short version.*

## 3. Prep Checklist

- Pre-read sent to participants: the Project 1 task page and (unread, saved for later) the GitHub comparison repo link.
- Printed or shared-doc copies of the Audit Rubric (Appendix A) — one per group.
- The human "gold standard" answers for Tasks 2–5 (counts, ts/tv, isec results), pulled from the course solutions.
- The Antigravity output, stripped of its own comparison commentary — prepared as a "blind" handout so groups assess it on its own merits first.
- A visible timer for each phase.
- A shared doc or flip chart for capturing Phase 5 design principles.
- Optional: live access to Antigravity (or another coding agent) so one group can re-prompt it live during Phase 4, e.g. asking it to justify the GATK ts/tv drop.
- Facilitator decision, made in advance: will you seed a deliberate error into the blind handout? (See note in Phase 3.)

## 4. Detailed Facilitation Script

### Phase 1 — Framing (15 min)

Open with the tension directly: same dataset, same task list — one team took 1.5 hours with domain expertise, one tool took 10 minutes. Today isn't about deciding which is "better." It's about learning to interrogate both, and learning to teach others to do the same.

Quick poll: who already uses an AI coding agent day-to-day? This calibrates how much the group needs framing versus hands-on practice.

Set one ground rule out loud: this is an audit-skills exercise, not a competition. Scores in Phase 3 describe the analysis, not the tool's worth.

### Phase 2 — Re-anchor in the human solution (30–45 min)

Walk through the human-generated answers to Tasks 2–5: SNP/indel counts, ts/tv of raw vs. filtered callsets, the GATK ts/tv anomaly after filtering, and the isec intersection/private-variant ts/tv. This is the group's content refresher and establishes the standard the AI output will be audited against.

Discussion prompt: "What actually took the 1.5 hours — running the tools, or interpreting the output?" This seeds the distinction between execution speed and interpretive judgement that Phase 3 will test in the AI output.

### Phase 3 — Blind audit of the AI output (60–75 min)

Distribute the stripped Antigravity output and the rubric (Appendix A). Groups work through five checks: correctness against the gold standard, reasoning depth, reproducibility, transparency about assumptions, and a hunt for failure modes (hallucinated values, silently changed parameters, skipped steps).

> **Facilitator note:** if the AI output is fully correct, consider seeding one deliberate, plausible-looking error before distribution (e.g. a slightly altered ts/tv figure) and disclosing this after the reveal. Auditing something flawless teaches complacency; auditing something with a subtle flaw teaches vigilance. Log whether you did this so future facilitators know what to expect from the answer key.

Allow ~45 min for group work, 15–20 min for a rapid share-out of scores across groups before moving to the reveal.

### Phase 4 — Reveal & reconcile (15 min)

Show the published GitHub comparison. Compare each group's rubric scores against it and discuss any disagreement. Make the key point explicit: the published comparison is itself a human-authored artifact and deserves the same scrutiny as the AI output — nothing in this exercise is exempt from being audited.

If live tool access is available, use this slot to re-prompt the agent on the weakest point identified (commonly the GATK ts/tv explanation) and assess whether follow-up questioning improves the answer.

### Phase 5 — Trainer debrief: shift to meta (30 min)

Explicitly change registers: "you were students for the last 90 minutes — now think as trainers." Discuss and capture on a shared doc:

- What made this exercise work as a teaching tool?
- What would break it? (e.g. if a group can't independently verify AI output at all, the exercise collapses into taking things on faith.)
- How would you calibrate difficulty for a different audience — undergraduates vs. postdocs vs. clinical bioinformaticians?
- Where's the line between teaching useful verification habits and pushing participants toward either blanket distrust or blanket trust of AI tools?

The captured list becomes the reference sheet participants use in Phase 6.

### Phase 6 — Teach-back practice (60–90 min)

In pairs, participants choose a different module or project from the course (e.g. Module 4: Structural Variation Calling, or Project 3/4) and draft a 10-minute mini-version of this exercise: a one-line framing statement, a 3-item rubric, and 2 discussion questions.

Pairs deliver their mini-activity to another pair in ~10-minute blocks. Reviewers give feedback using the Peer Feedback Form (Appendix B). Rotate once more if time allows, so each pair both delivers and reviews at least twice.

## Appendix A — Audit Rubric

Score each dimension 1–4 (1 = poor, 4 = strong) against the human gold-standard answers, with notes.

| Check | Guiding question | Score (1–4) | Notes |
|---|---|---|---|
| Correctness | Do the SNP/indel counts and ts/tv values match the human run? | | |
| Reasoning depth | Did it explain why the metrics differ (e.g. GATK's filtered ts/tv), not just report numbers? | | |
| Reproducibility | Are exact commands and parameters shown, or only final results? | | |
| Transparency | Does it flag its own assumptions, or state uncertain things with unwarranted confidence? | | |
| Failure modes | Any hallucinated values, skipped steps, or silently altered parameters? | | |

## Appendix B — Peer Feedback Form (Teach-Back)

| Criterion | Comments |
|---|---|
| Clarity of the framing statement | |
| Quality and relevance of the 3-item rubric | |
| Value of the discussion questions | |
| Feasibility within a 10-minute slot | |
| One thing to change before running it for real | |

## Appendix C — Source Materials

- Course home: wcscourses.github.io/Genome-Sequence-Analysis-Standardised-Resources
- Project 1 task page: `.../course_modules/Projects/project1/project1.html`
- Human vs Antigravity comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project1

## 5. Notes for Adapting to Other Modules

Not every module makes an equally strong audit exercise. Favour ones with an interpretive "gotcha" comparable to the GATK ts/tv anomaly — a point where getting the right number isn't enough, and explaining the number correctly is what separates a strong analysis from a superficial one. Purely mechanical tasks (run tool, report count) make for a weak audit because there's little for the AI — or the trainee — to get subtly wrong.

Good candidates from this course: Module 4 (Structural Variation Calling — caller sensitivity trade-offs), Project 3 (host genetic factors — interpretive leap from variants to phenotype), Project 4 (taxonomic ID — confidence thresholds and false positives).
