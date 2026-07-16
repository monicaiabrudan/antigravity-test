# Facilitator's Guide

## Human vs AI: Auditing a Host-Genetics Variant Interpretation Workflow

*A Train-the-Trainer Module for the Genome Sequence Analysis Course*

| | |
|---|---|
| **Based on** | Project 3: Identifying host genetic factors for resistance to SARS-CoV (Trim55 locus, 52 mouse strains, bcftools view/query) |
| **Duration** | ≈ 3.5–4 hours |
| **Audience** | Researchers training to become course trainers — builds genomics facilitation skill and AI-tool critical literacy together |
| **Group size** | 4–6 per working group, run in parallel |
| **Source materials** | Course: wcscourses.github.io/Genome-Sequence-Analysis-Standardised-Resources · Comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project3 |

---

## 1. Purpose & Learning Objectives

This module reuses the Project 3 scenario and task list, but reframes it as a comparison exercise: a human group solution (1.5h) against an AI-agent solution (Google Antigravity). Project 3 differs from Projects 1 and 2 in its central challenge: it is not primarily about running tools correctly, but about correctly parsing a dense annotation field (CSQ) and then making a careful, appropriately hedged biological interpretation — linking candidate missense mutations in Trim55 to a disease-resistance phenotype across 52 mouse strains. That combination of a parsing trap and an interpretive leap is what makes this project a strong audit exercise.

By the end of the session, participants will be able to:

- Explain what the CSQ annotation field encodes, and why a comma inside it usually signals multiple overlapping transcript consequences for the same variant — a common source of miscounting.
- Explain the difference between a QTL-level genetic association and a confirmed functional or causal mutation, and why that distinction matters when reporting findings.
- Audit an AI-generated variant-annotation analysis against a structured rubric, distinguishing correct filtering from sound biological interpretation.
- Facilitate a "human vs AI" comparison exercise with a group, including handling disagreement over how confidently a candidate mutation can be described.
- Design and deliver their own version of this exercise for a different course module.

## 2. Session at a Glance

| Phase | Time | Format | Output |
|---|---|---|---|
| 1. Framing | 15 min | Plenary | Shared framing of the exercise; ground rules set |
| 2. Re-anchor in the human solution | 30–45 min | Plenary / small group | Refreshed content mastery; gold-standard variant list and interpretation on the table |
| 3. Blind audit of the AI output | 60–75 min | Small groups | Completed rubric per group, including a causal-inference caution score |
| 4. Reveal & reconcile | 15 min | Plenary | Group scores compared to the published comparison |
| 5. Trainer debrief (meta layer) | 30 min | Plenary | Shared list of design principles |
| 6. Teach-back practice | 60–90 min | Pairs + peer feedback | Draft mini-activity for another module + feedback notes |

*Total: ≈ 3.5–4 hours, including breaks. Phases 3–4 can be compressed to 60 min combined if running the short version.*

## 3. Prep Checklist

- Pre-read sent to participants: the Project 3 task page and (unread, saved for later) the GitHub comparison repo link.
- Printed or shared-doc copies of the Audit Rubric (Appendix A) — one per group.
- The human "gold standard" answers: sample count check (52 strains), the extracted Trim55 VCF, the CSQ interpretation at 3:19671000 and 3:19694085, the 11 missense variants, and the strains carrying them.
- The Antigravity output, stripped of its own comparison commentary — prepared as a "blind" handout.
- A visible timer for each phase.
- A shared doc or flip chart for capturing Phase 5 design principles.
- Optional: live access to Antigravity (or another coding agent) so one group can re-prompt it live during Phase 4, e.g. asking it to explain the comma-separated CSQ at position 3:19694085.
- Facilitator decision, made in advance: will you seed a deliberate error into the blind handout, e.g. a mis-filtered variant count, or a claim that overstates causality? (See note in Phase 3.)

## 4. Detailed Facilitation Script

### Phase 1 — Framing (15 min)

Open with the scenario as written for students: four QTLs are known to influence SARS-CoV disease severity across mouse strains, and the task is to characterise candidate variants at one of them (HrS1/Trim55) that might explain resistance or susceptibility. One team took 1.5 hours with domain expertise to work through this; one tool took a fraction of that. Today isn't about deciding which candidate-variant list to trust blindly — it's about learning to interrogate an annotation-heavy analysis and the interpretive claims built on it, and teaching others to do the same.

Quick poll: who already uses an AI coding agent day-to-day? This calibrates how much the group needs framing versus hands-on practice.

Set one ground rule out loud: this is an audit-skills exercise, not a competition. Scores in Phase 3 describe the analysis and the interpretive claims, not the tool's worth.

### Phase 2 — Re-anchor in the human solution (30–45 min)

Walk through the human-generated answers to Tasks 1–5: confirming 52 strains and extracting the Trim55 VCF, interpreting the CSQ field at the two example positions (including why a comma in the field usually means multiple transcript-level predictions for one variant, not multiple variants), the 11 missense variants, and which strains carry them. This is the group's content refresher and establishes the standard the AI output will be audited against.

Discussion prompt: "Where in this task would it be easy to silently over- or under-count variants without noticing?" This seeds the CSQ-parsing trap that Phase 3 will test in the AI output, and previews the distinction between a correct count and a defensible biological claim.

### Phase 3 — Blind audit of the AI output (60–75 min)

Distribute the stripped Antigravity output and the rubric (Appendix A). Groups work through six checks: correctness against the gold standard, annotation-parsing depth, reproducibility, transparency about assumptions, failure-mode hunting, and — the dimension unique to this project — causal-inference caution: does the output correctly frame Trim55 missense variants as candidates associated with a QTL, rather than as confirmed causal mutations?

> **Facilitator note:** if the AI output gets the counts and framing right, consider seeding one deliberate, plausible-looking issue before distribution — e.g. a miscounted missense variant total (not 11), or language that states a candidate mutation "causes" resistance rather than "is associated with" it. Auditing something flawless teaches complacency; auditing something with a subtle flaw teaches vigilance. Log whether you did this so future facilitators know what to expect from the answer key.

Allow ~45 min for group work, 15–20 min for a rapid share-out of scores across groups before moving to the reveal.

### Phase 4 — Reveal & reconcile (15 min)

Show the published GitHub comparison. Compare each group's rubric scores against it and discuss any disagreement — disagreement is especially likely on the causal-inference caution score, since the line between "candidate" and "causal" language can be subtle. Make the key point explicit: the published comparison is itself a human-authored artifact and deserves the same scrutiny as the AI output — nothing in this exercise is exempt from being audited, including phrasing that sounds appropriately careful.

If live tool access is available, use this slot to re-prompt the agent on its weakest point (commonly: does it explain why a comma appears inside the CSQ field, and does it hedge its biological claims appropriately?) and assess whether follow-up questioning improves the answer.

### Phase 5 — Trainer debrief: shift to meta (30 min)

Explicitly change registers: "you were students for the last 90 minutes — now think as trainers." Discuss and capture on a shared doc:

- What made this exercise work as a teaching tool, especially the annotation-parsing and causal-inference dimensions?
- What would break it? (e.g. if participants don't already understand what CSQ encodes, they can't judge whether the AI parsed it correctly — the exercise needs that prerequisite knowledge in place first.)
- How would you calibrate difficulty for a different audience — undergraduates vs. postdocs vs. researchers who work directly with variant annotation pipelines?
- Where's the line between teaching useful scepticism about AI-generated biological claims and pushing participants toward either blanket distrust or blanket trust of AI tools?

The captured list becomes the reference sheet participants use in Phase 6.

### Phase 6 — Teach-back practice (60–90 min)

In pairs, participants choose a different module or project from the course (e.g. Module 4: Structural Variation Calling, or Project 4/5) and draft a 10-minute mini-version of this exercise: a one-line framing statement, a 3-item rubric, and 2 discussion questions.

Pairs deliver their mini-activity to another pair in ~10-minute blocks. Reviewers give feedback using the Peer Feedback Form (Appendix B). Rotate once more if time allows, so each pair both delivers and reviews at least twice.

## Appendix A — Audit Rubric

Score each dimension 1–4 (1 = poor, 4 = strong) against the human gold-standard answers, with notes.

| Check | Guiding question | Score (1–4) | Notes |
|---|---|---|---|
| Correctness | Does it confirm 52 strains and correctly identify the 11 missense variants in Trim55? | | |
| Annotation-parsing depth | Does it correctly explain the comma-separated CSQ predictions, e.g. at 3:19671000 and 3:19694085? | | |
| Reproducibility | Are exact bcftools commands and filtering logic shown, or only final results? | | |
| Transparency | Does it flag its own assumptions, or state uncertain things with unwarranted confidence? | | |
| Failure modes | Any hallucinated variant counts, misread CSQ fields, or silently dropped strains? | | |
| Causal-inference caution | Does it correctly frame candidate variants as QTL-associated rather than confirmed causal mutations? | | |

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
- Project 3 task page: `.../course_modules/Projects/project3/project3.html`
- Reference paper: Genome Wide Identification of SARS-CoV Susceptibility Loci Using the Collaborative Cross — journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1005504
- Ensembl CSQ annotation guide: m.ensembl.org/info/genome/variation/prediction/predicted_data.html
- Human vs Antigravity comparison: github.com/monicaiabrudan/antigravity-test/tree/main/project3

## 5. Notes for Adapting to Other Modules

Project 3's strength as an audit exercise is that its central trap isn't a wrong command but a misread data field, compounded by an interpretive leap from genotype to phenotype. When choosing or designing other modules for this format, look for a similar structure: a dense, easy-to-miscount annotation or output field, paired with a claim that could be overstated if the annotation is misunderstood.

Good candidates from this course: Module 3 (Variant calling — INFO/FORMAT field interpretation), Project 4 (taxonomic ID of a secondary infection — confidence thresholds and the causal leap from detection to clinical relevance), Module 4 (Structural Variation Calling — breakpoint annotation ambiguity).
