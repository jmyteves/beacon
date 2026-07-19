# BEACON pan-cancer — literature novelty scan
*Run 2026-07-19, before GitHub publication. Purpose: know the prior art and where BEACON's defensible novelty sits.*

## Verdict in one line
This is **not** a first-of-kind "pan-cancer bidirectional-promoter" study, and **not** a first copy-number-driver prediction tool. The defensible novelty is the **combination** — compact-BDP architecture as the unit, a transcription-independent-architecture layer (Hi-C + nascent RNA, our unique asset), a per-cancer dosage **co-driver** call, and a deployable Navigator with an architecture-defined "expansion pack." Position accordingly; do not over-claim priority.

## Closest prior art (must cite + differentiate)

**1. Thompson, Christensen & Marsit 2018 — *IJMS* 19:2296 (doi:10.3390/ijms19082296)**
"Pan-Cancer Analysis Reveals Differential Susceptibility of Bidirectional Gene Promoters to DNA Methylation, Somatic Mutations, and Copy Number Alterations."
- **Overlap (high, surface-level):** same TCGA pan-cancer frame, 14 cancer types, BDPs + DNA methylation + copy number.
- **Difference (our wedge):** their question is *susceptibility* — they find BDPs are relatively **protected** (less copy-number alteration and less methylation change than single promoters; selected against). BEACON asks the complementary question: *given* amplification, do the two arms behave as a coordinated dosage **co-driver**? Their axis = protection/selection; ours = dosage-coupled output + a deployable per-cancer prediction. This is the paper a reviewer will name first — cite it explicitly and frame BEACON as the actionable, architecture-plus-3D counterpart.

**2. Chen et al. 2021 — *Front. Genet.* 11:560997**
"Pan-Cancer Analysis of Head-to-Head Gene Pairs in Terms of Transcriptional Activity, Co-expression and Regulation."
- **Overlap:** pan-cancer head-to-head (=bidirectional) gene-pair co-expression.
- **Difference:** descriptive co-expression/regulation catalog; no copy-number dosage co-driver call, no 3D/nascent layer, no tool.

**3. Li et al. 2019 — *eBioMedicine* 45:124–138 (PMC6642334)**
"PLAGL2 and POFUT1 are regulated by an evolutionarily conserved bidirectional promoter and are collaboratively involved in colorectal cancer by maintaining stemness."
- **Critical:** already published the exact PLAGL2–POFUT1 finding we anchor on — **co-expression r = 0.91 in CRC**, copy-number-amplification-driven, Wnt/Notch stemness. Our `coord_rho = 0.905` **reproduces their published value**.
- **Action:** the F1 "ranks first / reproduces the locus" framing must **cite Li 2019** (and it is the antecedent to Paper 1). Present PLAGL2–POFUT1 as a *validated anchor from the literature*, not a new discovery.

## Prediction-tool prior art (BEACON is not first here either)
- **iEDGE** (Montilab; github.com/montilab/iEDGE) — predicts SCNA-associated *cis* drivers across 19 TCGA cancers via trans-gene mediation. Generic driver prediction; not BDP-specific, no architecture layer.
- **Yuan et al. 2012** (sparse regulatory network of copy-number-driven expression, breast cancer oncogenes) — genome-wide CN→expression driver framework.
- Earlier: **Yang, Koehly & Elnitski 2007** (*PLoS Comput Biol*) — BDP co-regulation enriched among breast/ovarian cancer genes.

## Novelty that survives the scan (safe to claim)
1. **Architecture-defined universe + "expansion pack."** Defining the BDP set by compact bidirectional architecture alone (792), independent of any one cell line's expression, and showing the 287 Caco-2-silent BDPs recover co-drivers a cell-line-conditioned list would miss. Not done in the prior work.
2. **Transcription-independent architecture layer.** Hi-C + nascent RNA before/after transcription blockade (DRB) in Caco-2 — establishes that compact-BDP coupling is a constitutive architectural property. No pan-cancer BDP study carries a 3D/nascent readout. This is the genuinely unique asset (Caco-2 only — state the single-cell-type limit).
3. **Per-cancer dosage co-driver call + deployable Navigator.** A concrete, testable (BDP, cancer) → co-driver-X prediction with four falsifiable properties, released as an interactive resource. Prior work is descriptive or generic-driver; none ships this specific artifact.

## Framing guardrails for the manuscript
- Do **not** write "first pan-cancer analysis of bidirectional promoters" (Thompson 2018, Chen 2021 precede it).
- Do **not** present PLAGL2–POFUT1 r≈0.9 as novel (Li 2019 published it).
- **Do** claim: architecture-defined universe, the transcription-independent-architecture asset, the co-driver-prediction Navigator, and the expansion-pack demonstration.
- Cite Thompson 2018 as the complementary "susceptibility/protection" pan-cancer BDP study and state the axis difference in the Discussion.
