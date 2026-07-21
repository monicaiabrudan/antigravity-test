# Human vs AI Genomics Audit Hackathon — Project 3

## Theme

**Trust, but Verify: Auditing an AI-Generated Host-Genetics Variant Interpretation**

---

# Overview

In this hackathon, participants work in teams to evaluate an AI-generated solution to a real host-genetics variant-annotation and interpretation project.

Rather than competing against AI, participants act as **scientific reviewers**, assessing whether an AI-generated workflow is:

- scientifically correct
- reproducible
- transparent
- well justified
- suitable for teaching others

The activity is based on Project 3 from the Genome Sequence Analysis course and uses both a human-generated solution and an AI-generated solution (Google Antigravity) as the starting point.

Project 3 differs from Projects 1 and 2 in its central trap: it is not primarily about running the right commands, but about correctly parsing a dense annotation field (`CSQ`) and then making a careful, appropriately hedged biological interpretation — linking candidate missense mutations in *Trim55* to a SARS-CoV disease-resistance phenotype across 52 mouse strains. Two candidate solutions agree on the raw numbers (52 strains, 2,711 Trim55 variants, 4,659 CSQ predictions, 11 missense positions / 12 alleles) but diverge sharply in interpretive depth: one explicitly resolves the multiallelic site at `3:19672870`, names the 6 missense mutations carried by CAST/EiJ, and links them to the known *Trim55*-knockout phenocopy; the other conveys the same information less explicitly and stops short of that integrated claim. That gap — between a correct count and a scientifically sound, appropriately hedged interpretation — is the centrepiece of the audit.

---

# Learning objectives

By the end of the hackathon, participants will be able to:

- Critically evaluate AI-generated bioinformatics analyses.
- Reproduce and validate a variant-extraction and annotation workflow (`bcftools view`/`query`, CSQ parsing).
- Identify missing assumptions, errors and limitations in AI outputs, especially silent miscounts hidden inside a comma-separated annotation field.
- Generate and test competing hypotheses about *why* a candidate locus might drive a phenotype, and which follow-up analyses could discriminate between them.
- Improve AI-generated workflows and interpretive claims using evidence.
- Communicate a genotype-to-phenotype finding with appropriately hedged, causally cautious language.
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

- Project 3 task description (host genetic factors for SARS-CoV resistance, *Trim55*/HrS1 locus, 52 mouse strains)
- VCF dataset (52-strain callset; region `3:19639519-19697415`)
- Human solution (sample verification, Trim55 extraction, CSQ interpretation at two example positions, missense-variant table, genotype matrix, biological discussion)
- AI-generated solution (Google Antigravity), stripped of its own comparison commentary
- Audit rubric, including a causal-inference caution dimension
- Hypothesis-generation worksheet (see Challenge 3)
- Report template
- Internet access, including access to a hypothesis-generation tool (see Challenge 3)
- Course materials, including the Ensembl CSQ annotation guide and the reference paper (Genome Wide Identification of SARS-CoV Susceptibility Loci Using the Collaborative Cross)

---

# Hackathon Schedule

| Time  | Activity                                                        | Output                          |
| ----- | ---------------------------------------------------------------- | -------------------------------- |
| 09:30 | Welcome and briefing                                             | Teams formed                     |
| 10:00 | Challenge 1 – Reproduce the variant extraction and annotation    | Verified results                 |
| 11:00 | Challenge 2 – Audit the AI solution                               | Annotated AI report              |
| 12:00 | Lunch                                                             |                                  |
| 13:00 | Challenge 3 – Hypothesis generation: why does Trim55 matter?      | Ranked hypotheses + test plan    |
| 14:00 | Challenge 4 – Improve the workflow and interpretation             | Corrected workflow               |
| 15:00 | Challenge 5 – Design a teaching activity                          | Mini lesson plan                 |
| 15:45 | Team presentations                                                | 5-minute pitch                   |
| 16:30 | Awards and discussion                                             | Reflection                       |

---

# Challenge 1 – Reproduce the Analysis

## Goal

Verify that the reported variant-extraction and annotation results can be reproduced.

Participants should:

- confirm the VCF contains 52 samples
- extract the *Trim55* region (`3:19639519-19697415`) and confirm 2,711 variants
- query CSQ annotations at `3:19671000` and `3:19694085`, and explain what the comma inside the CSQ field represents
- tabulate `Consequence|Impact|Symbol` combinations and confirm the total of 4,659 predictions
- isolate missense variants in *Trim55* and confirm 11 distinct genomic positions / 12 alleles, correctly identifying the multiallelic site
- reproduce the genotype matrix showing which of the 52 strains carry alternative alleles
- compare their results with the human and AI solutions and document any discrepancies

Deliverable:

A short reproducibility report.

---

# Challenge 2 – Audit the AI Solution

Treat the AI-generated solution as if reviewing a manuscript.

For every task, determine:

- Is the answer scientifically correct?
- Is the command correct?
- Are assumptions explained?
- Does it correctly explain the comma-separated CSQ predictions, rather than miscounting transcripts as separate variants?
- Does it explicitly resolve the multiallelic site at `3:19672870` (two alleles, one position), or does it blur this distinction?
- Can another researcher reproduce it?
- Would you trust this result?
- Does it correctly frame the *Trim55* missense variants as candidates associated with the HrS1 QTL, or does it overstate them as confirmed causal mutations?

Record all issues with supporting evidence.

Deliverable:

Annotated AI solution, including a causal-inference caution score.

---

# Challenge 3 – Hypothesis Generation: Why Does Trim55 Matter?

## Goal

Both candidate solutions agree that CAST/EiJ — the most SARS-CoV-susceptible strain — carries 6 of the 11 missense variants in *Trim55*, and that *Trim55*-knockout mice phenocopy CAST/EiJ's reduced perivascular cuffing. The strongest solution uses this to argue the CAST allele behaves as a natural loss-of-function/hypomorph. That's a compelling correlational story, but it is still an inference across strains rather than a directly tested mechanism — exactly the kind of claim this challenge asks teams to stress-test.

## Task

1. As a team, list the available evidence: which of the 52 strains carry which of the 11 missense positions, the SIFT scores (all borderline "tolerated," 0.08–0.13), the exon distribution of the variants (7 of 11 cluster in exon 8), and which other genes sit in the same extracted region (e.g. *Crh*).
2. Use an AI hypothesis-generation tool (e.g. prompt an AI assistant such as Google Antigravity/Gemini, or another available coding agent, to act as a hypothesis generator) to produce **at least three competing hypotheses** for why this locus is associated with the resistance phenotype. Candidates to prompt for, or generate independently, include:
   - **Domain-specific disruption**: the exon 8 cluster sits on a functionally critical protein domain (e.g. a TRIM-protein substrate-recognition domain), so the clustered mutations plausibly disrupt substrate binding rather than overall folding.
   - **Confounded-locus hypothesis**: the phenotype could be driven by *Crh* or another linked gene in the same extracted region, co-inherited with *Trim55* in these wild-derived strains, rather than by *Trim55* itself.
   - **Missed-consequence-class hypothesis**: the missense-only tabulation may have missed a splice-site, stop-gain, or frameshift variant elsewhere in *Trim55* in one or more strains — a much stronger loss-of-function candidate than 6 missense changes.
3. For each hypothesis, specify a **discriminating check that can be run on existing data** — no new wet-lab work required. For example: mapping the exon 8 positions onto a structural prediction (AlphaFold) or domain database (Pfam/InterPro); checking whether every strain carrying the Trim55 variants also carries the *Crh* variant (co-inheritance check); or re-querying the CSQ field for *all* consequence classes (not just missense) across all 52 strains.
4. Run at least one discriminating check on the provided data, or clearly specify how you would run it if tooling access is limited.
5. Score each hypothesis for plausibility given the evidence, and state which one your team currently favours — and what result would change your mind.

Deliverable:

A short hypothesis-generation worksheet: the list of hypotheses (AI-generated and team-reviewed), the discriminating check(s) chosen, results if run, and a ranked conclusion with justification.

**Facilitator note:** the goal is not to force a single "correct" answer — the value of this challenge is watching teams design a check that could actually distinguish the hypotheses using data already in hand, rather than accepting the most narratively satisfying explanation (loss-of-function hypomorph) without testing it against the alternatives.

---

# Challenge 4 – Improve the Workflow

Using evidence from the audit and the hypothesis-generation exercise, produce an improved workflow and interpretation.

Teams should:

- correct any miscounted variants or mis-parsed CSQ fields
- explicitly resolve the multiallelic site and any other ambiguous annotation
- document assumptions
- improve reproducibility
- revise the biological interpretation so that causal language is proportionate to the evidence — candidate/associated vs. confirmed causal — and states clearly which of the Challenge 3 hypotheses the team favours and why
- recommend concrete next steps (e.g. functional validation, fine-mapping) to move from candidate to confirmed

Deliverable:

A revised workflow and interpretation.

---

# Challenge 5 – Teach the AI

Imagine you are delivering this project to future students.

Design a 15-minute classroom activity that teaches learners how to critically evaluate AI-generated variant annotation and AI-generated genotype-to-phenotype claims.

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
2. What errors were identified, including any silent miscounts in the CSQ field?
3. Which issues would affect the scientific and interpretive conclusions?
4. Why does Trim55 matter — what did your team conclude, and what check drove that conclusion?
5. How did your team improve the workflow and interpretation?
6. How would you teach responsible AI use using this example?

---

# Judging Criteria

| Category                                   | Points  |
| -------------------------------------------- | ------- |
| Scientific accuracy                          | 20      |
| Reproducibility assessment                   | 15      |
| Quality of AI audit                          | 15      |
| Hypothesis generation & test design          | 20      |
| Workflow and interpretation improvements     | 15      |
| Teaching activity                            | 5       |
| Presentation                                 | 10      |
| **Total**                                    | **100** |

---

# Awards

Suggested awards:

- Best Scientific Audit
- Best Reproducibility Champion
- Best Hypothesis Detective (Trim55-mechanism reasoning)
- Best Workflow Improvement
- Best Teaching Activity
- Best Presentation
- People's Choice Award

---

# Reflection Session

Conclude the hackathon with a facilitated discussion.

Suggested questions:

- When should researchers trust AI?
- What kinds of mistakes are easy to overlook inside a dense annotation field like CSQ?
- How can AI improve productivity without reducing scientific rigour?
- Which tasks still require human expertise — was distinguishing "associated with" from "causes" one of them?
- How should we teach responsible AI use in genome sequence analysis, including AI-assisted hypothesis generation?

---

# Expected Outputs

Each team submits:

- AI audit report
- Reproducibility notes
- Hypothesis-generation worksheet
- Corrected workflow and revised interpretation
- Mini teaching activity
- Presentation slides (optional)

---

# Key Message

The purpose of this hackathon is **not** to determine whether AI is faster than humans.

Instead, participants learn that modern researchers must be able to:

- verify AI-generated analyses, including annotation fields that are easy to miscount,
- generate and test competing explanations for a candidate locus rather than accepting the first plausible story,
- understand the underlying science,
- recognise the difference between a genetic association and a confirmed causal mechanism,
- improve reproducibility, and
- teach others how to use AI responsibly in genome sequence analysis.

The goal is to develop researchers who can work **with AI**, while maintaining scientific rigour, critical thinking and reproducible research practices — including when AI is used not just to annotate variants, but to help generate the hypotheses that explain what they mean.
