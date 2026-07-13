# 🧬 Toy NGS QC & Alignment Pipeline Results

This report presents the execution results of the simulated bioinformatics pipeline running on a small custom dataset designed to teach Next-Generation Sequencing (NGS) analysis principles.

## 📊 Summary of Outputs

* **Dataset Directory:** [demo_pipeline/data/](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/demo_pipeline/data/)
* **Interactive Dashboard:** [pipeline_dashboard.html](file:///Users/ma14/.gemini/antigravity-cli/brain/ea27be8c-dc0b-4a78-b24a-bfdd5bc2ea6f/pipeline_dashboard.html)
* **QC Report:** [qc_report.txt](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/demo_pipeline/qc_report.txt)
* **Aligned SAM File:** [aligned_sorted.sam](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/demo_pipeline/aligned_sorted.sam)
* **Flagstat Metrics:** [flagstat.txt](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/demo_pipeline/flagstat.txt)

---

## 🔬 1. The Dataset Design
We created 5 paired-end reads (10 reads total) to represent different biological and technical scenarios:
1. **`read1`**: A perfect match representing a clean genomic read.
2. **`read2`**: A match containing a Single Nucleotide Polymorphism (SNP) at the end of the first read.
3. **`read3`**: A match with low-quality base scores at the tail, demonstrating the drop-off in sequencer reliability.
4. **`read4`**: An unmapped read (consisting of unknown `N` bases and low quality scores `!`).
5. **`read5`**: A read where the first mate maps perfectly, but the second mate is unmapped (singleton alignment).

---

## 📈 2. Quality Control Metrics (FastQC Simulation)
The QC phase analysed the base-by-base quality of the FASTQ files:

| Metric | `reads_R1.fastq` | `reads_R2.fastq` |
| :--- | :--- | :--- |
| **Total Reads** | 5 | 5 |
| **Avg Length** | 20.0 bp | 20.0 bp |
| **GC Content** | 39.0% | 44.0% |
| **Avg Phred Score** | 29.6 | 24.0 |

> [!NOTE]
> The lower average Phred score in `R2` reflects the standard sequencer behavior where second-read (reverse) quality scores tend to degrade faster than `R1`.

---

## 🗺️ 3. Alignment Results (Samtools Flagstat Simulation)
The alignment mapped the reads against a 500 bp reference sequence.

| Metric | Count | Percentage | Description |
| :--- | :--- | :--- | :--- |
| **Total Reads** | 10 | 100% | Total raw reads (R1 + R2) |
| **Mapped** | 7 | 70.0% | Reads successfully aligned to the reference |
| **Properly Paired** | 4 | 40.0% | Mates both mapped in correct orientation/distance |
| **Singletons** | 3 | 30.0% | Only one mate aligned (`read5/1` mapped, `read5/2` unmapped) |

---

## 🖥️ 4. Read Mapping Table
Below is the sorted SAM alignment table produced by the mapping engine:

| Read ID | Mapping Status | Position (chr1) | Strand | Mismatches | Sequence |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`read1/1`** | Mapped | 1 | `+` | 0 | `ATGCGTACGTATCGATCGAT` |
| **`read2/1`** | Mapped | 1 | `+` | 1 (SNP) | `ATGCGTACGTATCGATCGAC` |
| **`read1/2`** | Mapped | 51 | `-` | 0 | `GCTAGCTAGCCGATCGATCG` |
| **`read2/2`** | Mapped | 51 | `-` | 0 | `GCTAGCTAGCCGATCGATCG` |
| **`read3/1`** | Mapped | 141 | `+` | 0 | `TATATATATATATATATATA` |
| **`read3/2`** | Mapped | 211 | `-` | 0 | `CCGGCCGGCCGGCCGGCCGG` |
| **`read5/1`** | Mapped | 351 | `+` | 0 | `GGGGCCCCGGGGCCCCGGGG` |
| **`read4/1`** | Unmapped | - | `-` | - | `NNNNNNNNNNNNNNNNNNNN` |
| **`read4/2`** | Unmapped | - | `-` | - | `NNNNNNNNNNNNNNNNNNNN` |
| **`read5/2`** | Unmapped | - | `-` | - | `NNNNNNNNNNNNNNNNNNNN` |

---

## 🎨 5. Graphical Dashboard
You can open [pipeline_dashboard.html](file:///Users/ma14/.gemini/antigravity-cli/brain/ea27be8c-dc0b-4a78-b24a-bfdd5bc2ea6f/pipeline_dashboard.html) directly in your browser. It includes:
* **QC Summary Cards:** Color-coded status metrics.
* **Flagstat Progress Bars:** Visually displaying mapping ratios.
* **Read-to-Reference Stacking Map:** A visual block showing exactly where each read sits on the chromosome.
