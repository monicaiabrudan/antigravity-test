# Human vs AI Genomics Audit Hackathon — Project 2

## Theme

**Trust, but Verify: Auditing an AI-Generated Sequencing-Platform QC Evaluation**

---

# Overview

In this hackathon, participants work in teams to evaluate an AI-generated solution to a real sequencing-platform QC evaluation.

Rather than competing against AI, participants act as **scientific reviewers**, assessing whether an AI-generated workflow is:

- scientifically correct
- reproducible
- transparent
- well justified
- suitable for teaching others

The activity is based on Project 2 from the Genome Sequence Analysis course and uses both a human-generated solution and an AI-generated solution (Google Antigravity) as the starting point.

Project 2 differs from a straightforward QC exercise in one important way: it ends not in a technical metric but in an institutional recommendation — *was the sequencing run a success, and should the institute keep the instrument?* Getting the numbers right is necessary but not sufficient. The interesting failure mode is a confident recommendation built on a misread of the evidence — most notably, Group 2's elevated total mismatches (861,448 vs. 92,930 for Group 4) and high post-filter SNP count (17,160), which can be read either as **QC/contamination artifacts** or as **evidence of a genuinely divergent strain**. The two candidate solutions disagree on exactly this point, which makes it the centrepiece of the audit.

---

# Learning objectives

By the end of the hackathon, participants will be able to:

- Critically evaluate AI-generated bioinformatics analyses.
- Reproduce and validate a sequencing-platform QC and variant-calling workflow (`bwa mem`, `samtools stats`, `bcftools`).
- Identify missing assumptions, errors and limitations in AI outputs.
- Generate and test competing hypotheses to distinguish a contamination/QC artifact from genuine biological divergence.
- Improve AI-generated workflows and recommendations using evidence.
- Communicate a scientific and business recommendation clearly to a non-technical stakeholder.
- Design teaching activities that promote responsible use of AI in genomics.

---

# Audience

- Researchers
- Bioinformaticians
- Trainers
- Educators
- Graduate students

Participants should have completed the Genome Sequence Analysis course or possess equivalent knowledge.

---

# Duration

**Half-day (4–5 hours)**

or

**Full-day (6–7 hours)**

---

# Team size

3–5 participants

Each team should include a mixture of experience where possible.

---

# Materials provided

Each team receives:

- Project 2 task description (QC evaluation of a novel sequencing platform)
- Sequencing dataset (Group 2 and Group 4 reads, aligned to the *Salmonella enterica* serovar Paratyphi B str. SPB7 reference)
- Human solution (alignment QC stats, pre/post-filter variant counts, ts/tv, final recommendation)
- AI-generated solution (Google Antigravity), stripped of its own comparison commentary
- Audit rubric, including a recommendation-soundness dimension
- Hypothesis-generation worksheet (see Challenge 3)
- Report template
- Internet access, including access to a hypothesis-generation tool (see Challenge 3)
- Course materials

---

# Hackathon Schedule

| Time  | Activity                                                   | Output                        |
| ----- | ------------------------------------------------------------ | ------------------------------ |
| 09:30 | Welcome and briefing                                        | Teams formed                  |
| 10:00 | Challenge 1 – Reproduce the QC evaluation                   | Verified results               |
| 11:00 | Challenge 2 – Audit the AI solution                          | Annotated AI report            |
| 12:00 | Lunch                                                        |                                |
| 13:00 | Challenge 3 – Hypothesis generation: contamination or new species? | Ranked hypotheses + test plan |
| 14:00 | Challenge 4 – Improve the workflow and recommendation        | Corrected workflow             |
| 15:00 | Challenge 5 – Design a teaching activity                     | Mini lesson plan               |
| 15:45 | Team presentations                                           | 5-minute pitch                 |
| 16:30 | Awards and discussion                                        | Reflection                     |

---

# Challenge 1 – Reproduce the Analysis

## Goal

Verify that the reported QC and variant-calling results can be reproduced.

Participants should:

- run the alignment and QC workflow (`bwa mem` → `samtools sort` → `samtools stats`, noting whether duplicate marking was performed)
- run variant calling and filtering (`bcftools mpileup | bcftools call`, filtered at QUAL≥30, DP≥20)
- reproduce key outputs: mapping rate, error rate, total mismatches, insert size, GC content, and SNP/indel counts and ts/tv before and after filtering, for both Group 2 and Group 4
- compare their results with the human and AI solutions
- document any discrepancies, especially any missing pipeline steps (e.g. a skipped `picard MarkDuplicates` step)

Deliverable:

A short reproducibility report.

---

# Challenge 2 – Audit the AI Solution

Treat the AI-generated solution as if reviewing a manuscript.

For every task, determine:

- Is the answer scientifically correct?
- Is the command correct?
- Are assumptions explained?
- Are parameters appropriate?
- Did it correctly interpret the QC plots (insert size, GC content, mismatches-per-cycle), not just generate them?
- Can another researcher reproduce it?
- Would you trust this result?
- Does the keep/replace recommendation follow proportionately from the evidence, or does it overreach from a single run?

Record all issues with supporting evidence.

Deliverable:

Annotated AI solution, including a recommendation-soundness score.

---

# Challenge 3 – Hypothesis Generation: Contamination or New Species?

## Goal

Group 2 shows a cluster of unusual signals: a 7.5% unmapped-read rate, a 10x higher error rate than Group 4, 861,448 total mismatches, a possible insert-size anomaly, a ~65% GC bump in the first fragment, and elevated high-quality (Q>30) mismatches that stay flat across all cycles. After filtering, Group 2 still carries 17,160 high-confidence SNPs with a high ts/tv ratio (3.75) against the reference genome.

The AI solution and the human solution disagree on what this means: one treats it as a **QC/contamination artifact producing false-positive variant calls**; the other treats the high ts/tv ratio as **confirmation that Group 2 is a genuinely divergent strain**. Both readings are plausible from the numbers alone — this challenge asks teams to move from "which reading do I prefer" to "which reading survives a targeted test."

## Task

1. As a team, list every piece of evidence available (mapping rate, error rate, total mismatches, insert-size profile, GC content bump, mismatches-per-cycle pattern, ts/tv ratio, poly-G/poly-T unmapped reads, SNP density and distribution).
2. Use an AI hypothesis-generation tool (e.g. prompt an AI assistant such as Google Antigravity/Gemini, or another available coding agent, to act as a hypothesis generator) to produce **at least three competing hypotheses** that could explain Group 2's numbers — for example: (a) sample/library contamination with a related organism, (b) a genuinely divergent Paratyphi B strain, (c) a sequencing-chemistry or lane-specific artifact, (d) a reference-genome mismatch or misassembly.
3. For each hypothesis, ask the tool — and then verify yourselves — what a **discriminating test** would look like: a check whose result would differ depending on which hypothesis is true. Candidates include: BLASTing a sample of unmapped/mismatched reads against a broader database, running a taxonomic classifier (e.g. Kraken2/Kaiju) on the unmapped reads, checking whether high-quality mismatches cluster at specific genome positions (contamination/misassembly) versus spreading genome-wide with a transition bias (real divergence), checking whether the GC bump coincides with the mismatch-dense regions, and comparing Group 2's SNP pattern against known Paratyphi B strain variation.
4. Run at least one discriminating test on the provided data, or clearly specify how you would run it if tooling access is limited.
5. Score each hypothesis for plausibility given the evidence, and state which one your team currently favours — and what result would change your mind.

Deliverable:

A short hypothesis-generation worksheet: the list of hypotheses (AI-generated and team-reviewed), the discriminating test(s) chosen, results if run, and a ranked conclusion with justification.

**Facilitator note:** the goal is not to force a single "correct" answer — the value of this challenge is watching teams design a test that could actually distinguish the hypotheses, rather than defaulting to whichever explanation the AI stated most confidently.

---

# Challenge 4 – Improve the Workflow

Using evidence from the audit and the hypothesis-generation exercise, produce an improved workflow and recommendation.

Teams should:

- correct commands and add any missing pipeline steps (e.g. duplicate marking)
- improve explanations of the QC plots
- document assumptions
- improve reproducibility
- revise the institutional recommendation so that it is proportionate to the evidence and explicitly states whether the Group 2 SNP excess is treated as artifact or biology, and why
- recommend best practices for the next sequencing run

Deliverable:

A revised workflow and recommendation.

---

# Challenge 5 –  How to critically evaluate AI-generated bioinformatics work

Imagine you are delivering this project to future students.

Design a 15-minute classroom activity that teaches learners how to critically evaluate AI-generated bioinformatics analyses and AI-generated business recommendations.

The activity should include:

- learning objectives
- instructions
- discussion questions
- expected outcomes
- assessment method

Deliverable:

Mini lesson plan.

---

# Final Presentation

Each team delivers a **5-minute presentation** covering:

1. What did the AI do well?
2. What errors were identified?
3. Which issues would affect the scientific and business conclusions?
4. Contamination or new species — what did your team conclude, and what test drove that conclusion?
5. How did your team improve the workflow and recommendation?
6. How would you teach responsible AI use using this example?

---

# Judging Criteria

| Category                          | Points  |
| ---------------------------------- | ------- |
| Scientific accuracy                | 20      |
| Reproducibility assessment         | 15      |
| Quality of AI audit                | 15      |
| Hypothesis generation & test design | 20      |
| Workflow and recommendation improvements | 15 |
| Teaching activity                  | 5       |
| Presentation                       | 10      |
| **Total**                          | **100** |

---

# Awards

Suggested awards:

- Best Scientific Audit
- Best Reproducibility Champion
- Best Hypothesis Detective (contamination-vs-new-species reasoning)
- Best Workflow Improvement
- Best Teaching Activity
- Best Presentation
- People's Choice Award

---

# Reflection Session

Conclude the hackathon with a facilitated discussion.

Suggested questions:

- When should researchers trust AI?
- What kinds of mistakes are easy to overlook, especially in a confidently stated recommendation?
- How can AI improve productivity without reducing scientific rigour?
- Which tasks still require human expertise — was distinguishing contamination from a new species one of them?
- How should we teach responsible AI use in genome sequence analysis, including AI-assisted hypothesis generation?

---

# Expected Outputs

Each team submits:

- AI audit report
- Reproducibility notes
- Hypothesis-generation worksheet
- Corrected workflow and revised recommendation
- Mini teaching activity
- Presentation slides (optional)

---

# Key Message

The purpose of this hackathon is **not** to determine whether AI is faster than humans.

Instead, participants learn that modern researchers must be able to:

- verify AI-generated analyses,
- generate and test competing explanations for ambiguous evidence rather than accepting the first plausible story,
- understand the underlying science,
- recognise limitations,
- improve reproducibility, and
- teach others how to use AI responsibly in genome sequence analysis.

The goal is to develop researchers who can work **with AI**, while maintaining scientific rigour, critical thinking and reproducible research practices — including when AI is used not just to run the analysis, but to help generate the hypotheses that explain it.
