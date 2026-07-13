# 🧫 Tutorial Demo: Klebsiella AMR & Virulence Screening using Antigravity

This demo showcases how a researcher who has attended the Genome Sequence Analysis (GSA) course can use **Antigravity** to automate clinical surveillance on 10 newly assembled *Klebsiella pneumoniae* genomes.

## 📂 Demo Files & Outputs
* **Genomes Directory:** [amr_demo/genomes/](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/amr_demo/genomes/)
* **Raw Tabulated Output:** [kleborate_results.txt](file:///Users/ma14/Documents/GitHub/GSA/Genome-Sequence-Analysis-Standardised-Resources/amr_demo/kleborate_results.txt)
* **Interactive Dashboard:** [amr_dashboard.html](file:///Users/ma14/.gemini/antigravity-cli/brain/ea27be8c-dc0b-4a78-b24a-bfdd5bc2ea6f/amr_dashboard.html)

---

## 💬 Scenario: The Researcher's Interaction with Antigravity

A researcher opens their workspace containing 10 FASTA assembly files (`genomes/KPN_*.fasta`) and starts a conversation with Antigravity:

### Step 1: The Request
> **Researcher:** *"I have 10 Klebsiella pneumoniae assemblies in `genomes/`. Please run a Kleborate AMR and virulence screening on all of them, parse the tab-separated results table, and generate a clean visual summary of the clinical clones, carbapenemases, and hypervirulent isolates."*

### Step 2: How Antigravity Executes the Task
Antigravity automatically executes the following steps in the background:
1. **Checks Tools:** It queries the environment to see if `kleborate` or similar command line tools are installed. If missing, it offers to install them via `conda` or compile them.
2. **Runs Screening:** It runs the batch job:
   ```bash
   kleborate --genomes genomes/ -o kleborate_results.txt
   ```
3. **Parses & Extracts Insights:** It reads the tabulated results to identify clinical profiles of interest (such as high-risk clones and hypervirulent strains).
4. **Builds a Visual Dashboard:** It writes an HTML/CSS interface [amr_dashboard.html](file:///Users/ma14/.gemini/antigravity-cli/brain/ea27be8c-dc0b-4a78-b24a-bfdd5bc2ea6f/amr_dashboard.html) summarizing the data for easy clinical evaluation.

---

## 🧬 Understanding the Clinical Findings (Surveillance Results)

The analysis reveals three distinct high-risk types of *K. pneumoniae* clones:

### 1. Carbapenem-Resistant Klebsiella pneumoniae (CRKP)
* **ST258 (`KPN_01`, `KPN_10`)**: The classic global epidemic clone harboring the `blaKPC-2` carbapenemase gene. Notably, `KPN_10` shows resistance to **colistin** (due to an *mgrB* inactivation mutation), making it a pan-drug resistant threat.
* **ST11 (`KPN_02`)**: A highly active East Asian epidemic clone carrying both `blaNDM-1` (New Delhi metallo-beta-lactamase) and `blaOXA-48` carbapenemase genes, plus the `blaCTX-M-15` ESBL gene.
* **ST147 (`KPN_05`)**: A high-risk clone carrying `blaNDM-5` and the plasmid-mediated colistin resistance gene **`mcr-1`**.

### 2. Hypervirulent Klebsiella pneumoniae (hvKP)
* **ST23 (`KPN_06`)**: A classic hypervirulent clone associated with community-acquired pyogenic liver abscesses. It carries **yersiniabactin** (`ybt`), **colibactin** (`clb`), and **aerobactin** (`iuc`). It has a Virulence Score of 5, but remains antibiotic-susceptible (only carrying intrinsic `blaSHV-1`).
* **ST86 (`KPN_07`)**: Another hypervirulent clone carrying the `iuc` aerobactin locus (Virulence Score 3) but susceptible to antibiotics.

### 3. ESBL Clones
* **ST307 (`KPN_03`)** and **ST15 (`KPN_04`)**: Epidemic clones producing the `blaCTX-M-15` Extended-Spectrum Beta-Lactamase, rendering them resistant to cephalosporins but susceptible to carbapenems.

---

## 🎨 Interactive Clinical Dashboard
Open the [amr_dashboard.html](file:///Users/ma14/.gemini/antigravity-cli/brain/ea27be8c-dc0b-4a78-b24a-bfdd5bc2ea6f/amr_dashboard.html) file directly in your browser. It renders:
* **MLST Clone Categories:** Easily identify high-risk ST258, ST11, and ST307.
* **AMR Heatmap Badges:** Color-coded clinical alarms highlighting carbapenem and colistin resistance.
* **Virulence Factor Scorecards:** Grouping isolates by their virulence marker levels (`ybt`, `clb`, `iuc`).
