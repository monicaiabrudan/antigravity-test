# Facilitator's Guide

## Human vs AI: Auditing a Sequencing-Platform QC Evaluation

*A Train-the-Trainer Module for the Genome Sequence Analysis Course*

| | |
|---|---|
| **Based on** | Project 2: QC evaluation of a novel sequencing platform (bwa mem, samtools stats, bcftools) |
| **Duration** | ≈ 3.5–4 hours |
| **Audience** | Researchers training to become course trainers — builds genomics facilitation skill and AI-tool critical literacy together |
| **Group size** | 4–6 per working group, run in parallel |
| **Source materials** | Course: wcscourses.github.io/Genome-Sequence-Analysis-Standardised-Resources · Comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project2 |

---

## 1. Purpose & Learning Objectives

This module reuses the Project 2 scenario and task list, but reframes it as a comparison exercise: a human group solution (1.5h) against an AI-agent solution (Google Antigravity). Project 2 differs from Project 1 in an important way: it ends not in a technical metric but in an institutional recommendation — "was the sequencing run a success, should the institute keep the instrument?" That judgement call is what makes this project a strong audit exercise: correctness of the numbers is necessary but not sufficient, and the interesting failure mode is a confident recommendation built on thin or misread evidence.

By the end of the session, participants will be able to:

- Explain what alignment QC statistics and plots (from `samtools stats`) reveal about run quality, and how to spot problems in them.
- Explain how variant filtering (QUAL≥30, DP≥20) changes SNP/indel counts and ts/tv, and why that matters for judging a sequencing run.
- Audit an AI-generated analysis and business recommendation against a structured rubric, distinguishing correct numbers from sound judgement.
- Facilitate a "human vs AI" comparison exercise with a group, including handling disagreement over a subjective recommendation.
- Design and deliver their own version of this exercise for a different course module.

## 2. Session at a Glance

| Phase | Time | Format | Output |
|---|---|---|---|
| 1. Framing | 15 min | Plenary | Shared framing of the exercise; ground rules set |
| 2. Re-anchor in the human solution | 30–45 min | Plenary / small group | Refreshed content mastery; gold-standard answers and recommendation on the table |
| 3. Blind audit of the AI output | 60–75 min | Small groups | Completed rubric per group, including a recommendation-soundness score |
| 4. Reveal & reconcile | 15 min | Plenary | Group scores compared to the published comparison |
| 5. Trainer debrief (meta layer) | 30 min | Plenary | Shared list of design principles |
| 6. Teach-back practice | 60–90 min | Pairs + peer feedback | Draft mini-activity for another module + feedback notes |

*Total: ≈ 3.5–4 hours, including breaks. Phases 3–4 can be compressed to 60 min combined if running the short version.*

## 3. Prep Checklist

- Pre-read sent to participants: the Project 2 task page and (unread, saved for later) the GitHub comparison repo link.
- Printed or shared-doc copies of the Audit Rubric (Appendix A) — one per group.
- The human "gold standard" answers: alignment QC observations, SNP/indel/ts-tv counts before and after filtering for Group2 and Group4, and the final recommendation on the instrument.
- The Antigravity output, stripped of its own comparison commentary — prepared as a "blind" handout, including whatever QC plots it generated.
- A visible timer for each phase.
- A shared doc or flip chart for capturing Phase 5 design principles.
- Optional: live access to Antigravity (or another coding agent) so one group can re-prompt it live during Phase 4, e.g. asking it to justify its keep/replace recommendation with specific evidence.
- Facilitator decision, made in advance: will you seed a deliberate error into the blind handout, e.g. a QC plot mislabelled or a filtering threshold silently changed? (See note in Phase 3.)

## 4. Detailed Facilitation Script

### Phase 1 — Framing (15 min)

Open with the scenario as written for students: a new sequencing machine has just produced its first run, and you're the only person in the institute who can judge whether it worked. One team took 1.5 hours with domain expertise to reach a recommendation; one tool took a fraction of that. Today isn't about deciding which recommendation to trust blindly — it's about learning to interrogate the evidence behind a recommendation, and teaching others to do the same.

Quick poll: who already uses an AI coding agent day-to-day? This calibrates how much the group needs framing versus hands-on practice.

Set one ground rule out loud: this is an audit-skills exercise, not a competition. Scores in Phase 3 describe the analysis and the reasoning behind the recommendation, not the tool's worth.

### Phase 2 — Re-anchor in the human solution (30–45 min)

Walk through the human-generated answers to Tasks 1–3: alignment QC statistics and what the plots showed (any problems spotted), SNP/indel counts and ts/tv before and after filtering (QUAL≥30, DP≥20) for Group2 and Group4, and the resulting recommendation about the sequencing run and the instrument. This is the group's content refresher and establishes the standard the AI output will be audited against.

Discussion prompt: "Which part of the 1.5 hours was spent running commands, and which part was spent deciding what the numbers actually meant for a business recommendation?" This seeds the distinction, tested in Phase 3, between producing correct statistics and drawing a defensible conclusion from them.

### Phase 3 — Blind audit of the AI output (60–75 min)

Distribute the stripped Antigravity output and the rubric (Appendix A). Groups work through six checks: correctness against the gold standard, QC interpretation depth, reproducibility, transparency about assumptions, failure-mode hunting, and — the dimension unique to this project — recommendation soundness: does the keep/replace recommendation follow proportionately from the evidence, or does it overreach from a single run?

> **Facilitator note:** if the AI output is fully correct and its recommendation well-hedged, consider seeding one deliberate, plausible-looking issue before distribution — e.g. a QC plot that is mislabelled, or a recommendation stated with more confidence than a single sequencing run can support. Auditing something flawless teaches complacency; auditing something with a subtle flaw teaches vigilance. Log whether you did this so future facilitators know what to expect from the answer key.

Allow ~45 min for group work, 15–20 min for a rapid share-out of scores across groups before moving to the reveal.

### Phase 4 — Reveal & reconcile (15 min)

Show the published GitHub comparison. Compare each group's rubric scores against it and discuss any disagreement — disagreement is especially likely on the recommendation-soundness score, since that dimension is inherently judgement-based. Make the key point explicit: the published comparison is itself a human-authored artifact and deserves the same scrutiny as the AI output — nothing in this exercise is exempt from being audited, including a recommendation that sounds authoritative.

If live tool access is available, use this slot to re-prompt the agent on its weakest point (commonly: does it acknowledge that one run is a small sample to judge an instrument on?) and assess whether follow-up questioning improves the answer.

### Phase 5 — Trainer debrief: shift to meta (30 min)

Explicitly change registers: "you were students for the last 90 minutes — now think as trainers." Discuss and capture on a shared doc:

- What made this exercise work as a teaching tool, especially the recommendation-soundness dimension?
- What would break it? (e.g. if the human gold-standard recommendation is itself contestable, groups may just be auditing against a moving target.)
- How would you calibrate difficulty for a different audience — undergraduates vs. postdocs vs. clinical/public-health bioinformaticians who actually make instrument-purchasing decisions?
- Where's the line between teaching useful verification habits around AI-generated recommendations and pushing participants toward either blanket distrust or blanket trust of AI tools?

The captured list becomes the reference sheet participants use in Phase 6.

### Phase 6 — Teach-back practice (60–90 min)

In pairs, participants choose a different module or project from the course (e.g. Module 4: Structural Variation Calling, or Project 3/4/5) and draft a 10-minute mini-version of this exercise: a one-line framing statement, a 3-item rubric, and 2 discussion questions.

Pairs deliver their mini-activity to another pair in ~10-minute blocks. Reviewers give feedback using the Peer Feedback Form (Appendix B). Rotate once more if time allows, so each pair both delivers and reviews at least twice.

## Appendix A — Audit Rubric

Score each dimension 1–4 (1 = poor, 4 = strong) against the human gold-standard answers, with notes.

| Check | Guiding question | Score (1–4) | Notes |
|---|---|---|---|
| Correctness | Do the alignment stats and SNP/indel/ts-tv counts (pre- and post-filter) match the human run? | | |
| QC interpretation depth | Did it correctly identify and explain any problems visible in the QC plots, not just generate them? | | |
| Reproducibility | Are exact commands and filtering thresholds shown, or only final results? | | |
| Transparency | Does it flag its own assumptions and the limits of a single sequencing run, or overstate certainty? | | |
| Failure modes | Any hallucinated values, mislabelled plots, or silently altered thresholds? | | |
| Recommendation soundness | Does the keep/replace recommendation follow proportionately from the evidence presented? | | |

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
- Project 2 task page: `.../course_modules/Projects/project2/project2.html`
- Project 2 data: github.com/WCSCourses/Genome-Sequence-Analysis-Standardised-Resources/tree/main/course_modules/Projects/project2/data
- Human vs Antigravity comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project2

## 5. Notes for Adapting to Other Modules

Project 2's strength as an audit exercise is that it ends in a real-world decision, not just a metric — this creates a second, harder layer to audit beyond "are the numbers right." When choosing or designing other modules for this format, look for a similar structure: a technical task that feeds into a judgement call someone would actually have to defend to a non-technical stakeholder.

Good candidates from this course: Project 3 (host genetic factors — interpretive leap from variants to phenotype, defensible to a clinical audience), Project 4 (taxonomic ID of a secondary infection — a call with direct patient-management consequences), Project 5 (a second QC-evaluation project, useful for a contrasting platform or dataset).
