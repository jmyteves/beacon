# BEACON: a model-based tool that predicts copy-number co-drivers of compact bidirectional promoters across cancers

**Running title:** Pan-cancer co-driver prediction at compact bidirectional promoters

**Tool:** BEACON — *Bidirectional-promoter Expression And Copy-number Output Navigator*
**Companion resource** to the compact-BDP atlas and the PLAGL2–POFUT1 locus study (Paper 1).
**Deployment:** static, client-side GitHub Pages app — https://github.com/jmyteves/beacon

---

## One-sentence pitch
- We turn a mechanism established at a single colorectal-cancer locus into a genome-wide, cross-cancer prediction tool: for any compact bidirectional promoter in any of 14 cancers, BEACON predicts whether copy-number amplification is a coherent-feedforward **co-driver** of the promoter's coordinated output, and returns four properties the user can test in their own cohort.

## What this is (and is not)
- **It is:** a *model-based prediction resource*. The model is the coherent-feedforward co-driver logic we characterised mechanistically at PLAGL2–POFUT1 in Caco-2 / CRC (Paper 1); BEACON deploys that logic as a predictive template, per cancer, over an architecture-defined universe of compact bidirectional promoters.
- **It is not:** a first pan-cancer survey of bidirectional promoters (descriptive pan-cancer BDP analyses precede us; see Discussion), nor a re-fitted dose-response classifier. Predictions are **measured** per-cancer associations reported with effect size — hypotheses to test, not black-box scores.

---

## Abstract (~200 words)
- Compact bidirectional promoters (BDPs; two protein-coding genes in a head-to-head pair ≤1 kb apart) place two genes under one shared regulatory element. At the PLAGL2–POFUT1 locus in colorectal cancer, we previously showed the two arms are the most tightly co-expressed of tested BDP pairs, that the coupling is a constitutive architectural property, and that 20q copy-number amplification acts as a coherent-feedforward driver of their shared output.
- Whether this locus is a template for BDP behaviour genome-wide, and across cancers, was untested. Here we build BEACON, a model-based prediction tool that applies the PLAGL2–POFUT1 logic to **792** compact BDPs defined by architecture alone across **14** TCGA cancer types.
- We show: (i) compact BDPs are broadly coordinated in CRC and PLAGL2–POFUT1 ranks first, reproducing the founding locus; (ii) an architecture-defined universe — including 287 promoters silent in the discovery cell line — recovers co-drivers a cell-line-conditioned list would miss; (iii) per-cancer co-driver burden tracks each cancer's amplification landscape (ρ=0.99), and PLAGL2–POFUT1's coordinated output scales with 20q dosage across cancers.
- BEACON is released as a client-side interactive resource for hypothesis generation.

---

## Introduction (beats)
- **Compact BDPs are a distinct regulatory unit.** Two protein-coding TSSs ≤1 kb apart share one nucleosome-depleted regulatory region; their expression is often coordinated, and the arrangement is deeply conserved.
- **The founding observation (Paper 1).** At 20q11.21, PLAGL2 (a Wnt driver) and POFUT1 (a Notch modifier) sit at a 108-bp head-to-head BDP. In CRC they are the most tightly co-expressed of the BDP pairs tested (r≈0.91), the coupling is constitutive and transcription-independent (~90% of BDP-anchored contacts stable), and 20q copy-number amplification drives their shared output as a coherent feedforward — copy number *co-drives* alongside the fixed promoter architecture.
- **The open question.** Is this a one-locus curiosity, or a template? Two generalisation axes: genome-wide (do other compact BDPs behave the same way?) and across cancers (does dosage co-driving extend beyond CRC?).
- **The honesty constraint.** Hi-C and nascent RNA (the transcription-independent-architecture evidence) exist for Caco-2 only. The cross-cancer axis is carried by the readouts TCGA supports — copy-number-coupled coordinated expression — never by 3D architecture across cancers.
- **This work.** We package the generalisation as a prediction tool, BEACON, and report what it reveals.

---

## Results

### R1 · Compact BDPs are broadly coordinated in CRC, and the founding locus ranks first  → **Figure 1**
- Of **452** compact protein-coding BDPs analyzable in colorectal tumors (TCGA COAD+READ, n=590), **72%** are coordinated (arm–arm Spearman ρ>0.3).
- **PLAGL2–POFUT1 ranks 1 of 452** (coord ρ=0.905), independently reproducing Paper 1's rank-first, r≈0.91 finding (Li et al. 2019) and setting the tone that compact BDPs are a coherent regulatory class.
- Caco-2 nascent-RNA coupling concords with CRC tumor coordination only **weakly** at genome scale (ρ=0.12, p=0.026, n=346). We state this plainly: the strong validation is **locus-level reproduction**, not the genome-wide concordance — nascent coupling in one cell line and steady-state tumor coordination are different measurements.

### R2 · An architecture-defined universe removes cell-line bias and recovers hidden co-drivers  → **Figure 2**
- The discovery set (505 BDPs) is conditioned on Caco-2 expression — a cell-line ascertainment bias for a cross-cancer tool.
- We therefore define the BEACON universe by **architecture alone**: **792** compact protein-coding BDPs (≤1 kb), of which 505 are Caco-2-testable and **287** form an *expansion pack* (silent/untestable in Caco-2). 688/792 resolve on both arms in the pan-cancer data.
- **The payoff:** **102 of 287** expansion-pack BDPs (36%) are predicted co-drivers in at least one cancer — 14% of all co-driver calls — and are invisible to a Caco-2-conditioned list. Top hits include PLAG1–CHCHD7 (co-driver across 7 cancers; PLAG1 is a PLAGL2 paralog and known oncogene) and MBOAT7–TSEN34 (8 cancers).

### R3 · The co-driver landscape varies coherently across 14 cancers  → **Figure 3**
- Applying the model per cancer, the co-driver population (coordinated output + copy-number dosage coupling + recurrent amplification) is dense in amplification-prone cancers and sparse in copy-number-quiet ones.
- Co-driver counts range from **314/667 (bladder)** and **306 (lung)** down to **0 in AML and thyroid**, mirroring each cancer's aneuploidy.

### R4 · Co-driver burden tracks amplification, and PLAGL2–POFUT1 scales with 20q dosage  → **Figure 4**
- Per-cancer co-driver burden is near-perfectly correlated with that cancer's mean amplification prevalence (**ρ=0.99, p=1.2e-10, n=14**): the tool reflects real copy-number biology, not an artifact of the threshold.
- PLAGL2–POFUT1's own coordinated output **scales with 20q dosage across cancers** — highest in CRC (0.905) and stomach (0.75), lost where 20q is not amplified (kidney 0.28, thyroid 0.26). CRC is the reference anchor (owned by Paper 1); the cross-cancer scaling is the generalisation Paper 1 does not make.

### R5 · BEACON — the deployable tool
- A user picks a **compact BDP** and a **cancer**; BEACON returns the predicted copy-number **co-driver (X)** and four testable properties: (1) X identity + cytoband; (2) coordinated output (arm–arm ρ); (3) dosage coupling (CN→expression ρ); (4) amplification prevalence — plus a "how to test in your cohort" recipe with expected values.
- **Co-driver call:** dosage ρ ≥ 0.3 **and** amplification prevalence ≥ 0.15. Entirely client-side; the 792-BDP × 14-cancer grid (11,088 predictions) is embedded.

---

## Discussion (beats)
- **What is genuinely new.** Not the observation that BDPs exist pan-cancer (prior descriptive surveys precede us), nor copy-number-driver prediction in general (generic tools exist). The contribution is the **combination**: an architecture-defined BDP universe (with an expansion pack that removes cell-line bias), grounded in a **transcription-independent-architecture** mechanism we can only establish because of the Caco-2 Hi-C + nascent-RNA asset, deployed as a per-cancer co-driver prediction resource.
- **Relation to prior pan-cancer BDP work.** Thompson, Christensen & Marsit (2018) analysed BDP *susceptibility* to methylation, mutation, and copy-number alteration pan-cancer and found BDPs relatively protected. BEACON asks the complementary, actionable question: *given* amplification, do the arms behave as a coordinated dosage co-driver? Their axis is selection/protection; ours is dosage-coupled output and prediction.
- **The coherent-feedforward frame.** Copy number *co-drives* alongside fixed promoter architecture — it does not create the coupling (Paper 1). BEACON operationalises this as a prediction, not a fitted causal model.
- **Limits, stated plainly.** (i) 3D/nascent evidence is Caco-2 only; cross-cancer claims rest on copy-number-coupled expression, not architecture. (ii) The Caco-2→CRC concordance is weak genome-wide; the model's validation is locus-level and by-cancer-coherence, not a per-BDP predictive accuracy. (iii) Predictions are measured associations, not experimentally confirmed drivers. (iv) 104 architecturally-defined BDPs (clone-ID lncRNA arms) are not resolvable in the pan-cancer data.
- **Use.** A hypothesis-generation resource: identify a candidate dosage co-driver at a BDP of interest in a cancer of interest, then test the three expected correlations in the user's own cohort.

---

## Methods (condensed)
- **BDP universe.** Compact bidirectional promoters = head-to-head protein-coding gene pairs with TSS–TSS distance ≤1 kb (GENCODE v32), from the compact-BDP census. Universe defined by architecture alone: 792 pairs; each flagged Caco-2-testable (505) or expansion pack (287).
- **Pan-cancer data.** cBioPortal TCGA PanCancer Atlas 2018, 14 studies (COAD+READ, STAD, GBM, UCEC, BLCA, LGG, LUAD, PAAD, BRCA, LAML, HNSC, LIHC, KIRC, THCA). Per study: RSEM expression + GISTIC gene-level copy number; genes resolved HUGO→Entrez; large responses fetched in 500-gene chunks.
- **Per (BDP, cancer) measures.** Coordinated output = Spearman ρ between the two arms' expression across tumors. Dosage coupling = Spearman ρ between locus GISTIC copy number and expression, mean of arms. Amplification prevalence = fraction of tumors with GISTIC ≥ +1, mean of arms. Minimum 30 tumors with both values.
- **Co-driver call.** dosage ρ ≥ 0.3 AND amplification prevalence ≥ 0.15.
- **Caco-2 layer.** Nascent-RNA partial coupling from the compact-BDP atlas (Caco-2 total RNA-seq ± DRB), carried for the 505 testable BDPs.
- **Reproducibility.** All four figures reproduce from `beacon_pancancer_precompute.csv` via `notebooks/BEACON_figures.ipynb`; the optional cBioPortal re-fetch is documented in the notebook.

## Data & code availability
- Tool + data + notebook: https://github.com/jmyteves/beacon (GitHub Pages).
- Precompute: `beacon_pancancer_precompute.csv` (792 BDPs × 14 cancers = 11,088 rows).

## References to assemble (verify DOIs before submission)
- Li et al. 2019, *eBioMedicine* 45:124–138 — PLAGL2 & POFUT1 bidirectional promoter, CRC (the r≈0.91 anchor).
- Thompson, Christensen & Marsit 2018, *Int J Mol Sci* 19:2296 — pan-cancer BDP susceptibility (methylation/mutation/CNA).
- Chen et al. 2021, *Front Genet* 11:560997 — pan-cancer head-to-head gene pairs.
- [Paper 1] — PLAGL2–POFUT1 locus study (this group; title/citation pending).
- [Compact-BDP atlas] — genome-wide compact-BDP resource (this group; companion).
- Trinklein et al. 2004; Yang, Koehly & Elnitski 2007 — bidirectional promoter definition & cancer co-regulation.
