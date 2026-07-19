# BEACON

**Bidirectional-promoter Expression And Copy-number Output Navigator**

A model-based tool that predicts, for any compact bidirectional promoter (BDP) in any of 14 cancers, whether copy-number amplification is a coherent-feedforward **co-driver** of the promoter's coordinated output — and returns four properties you can test in your own cohort.

**▶ Live tool:** https://jmyteves.github.io/beacon/

---

## What it does

Pick a **compact BDP** (two protein-coding genes ≤1 kb apart, head-to-head) and a **cancer type**. BEACON returns the predicted copy-number **co-driver (X)** and four measured properties:

1. **X identity + locus** — the shared cytoband where amplification acts
2. **Coordinated output** — arm–arm co-expression ρ across tumors
3. **Dosage coupling (Y)** — copy-number → expression ρ
4. **Amplification prevalence** — fraction of tumors with the locus gained

plus a **"how to test in your cohort"** recipe with expected values.

A BDP is called a **co-driver** when dosage ρ ≥ 0.3 **and** amplification prevalence ≥ 0.15.

> Predictions are **measured per-cancer associations** reported with effect size — hypotheses to test, not black-box scores. The tool deploys the coherent-feedforward logic characterised mechanistically at the PLAGL2–POFUT1 locus in colorectal cancer (companion study), applied as a predictive template.

## The universe

**792 compact protein-coding BDPs**, defined by *architecture alone* (≤1 kb head-to-head spacing, GENCODE v32) to avoid cell-line ascertainment bias:

- **505** testable in the Caco-2 discovery system
- **287** *expansion pack* — silent/untestable in Caco-2 but architecturally identical; 36% of these are co-drivers in ≥1 cancer, and would be invisible to a cell-line-conditioned list.

Across **14 TCGA PanCancer Atlas 2018** cohorts: COAD+READ, STAD, GBM, UCEC, BLCA, LGG, LUAD, PAAD, BRCA, LAML, HNSC, LIHC, KIRC, THCA → **11,088 predictions**.

## Repository layout

```
index.html                              the tool (self-contained, client-side)
data/
  beacon_pancancer.json                 embedded prediction grid (used by index.html)
  beacon_pancancer_precompute.csv       full table, 792 BDPs × 14 cancers (11,088 rows)
notebooks/
  BEACON_figures.ipynb                  reproduces all figures from the precompute
  data/                                 inputs for the notebook
```

The figures (PNG) and the manuscript are kept locally and are not part of this
published repository. The notebook regenerates the figures on demand from the
precompute in `data/`.

## Reproduce the figures

```bash
cd notebooks
jupyter lab BEACON_figures.ipynb    # run top to bottom
```

The notebook loads `data/beacon_pancancer_precompute.csv` and regenerates all four figures. Section 1b documents the optional cBioPortal re-fetch that rebuilds the precompute from scratch.

## Data provenance

- **Expression + copy number:** cBioPortal, TCGA PanCancer Atlas 2018 (RSEM expression, GISTIC gene-level copy number).
- **BDP definition:** compact-BDP census (GENCODE v32 head-to-head pairs ≤1 kb).
- **Caco-2 coupling layer:** total RNA-seq ± transcription blockade (DRB), from the companion compact-BDP atlas.

## Limitations

- 3D/nascent-RNA evidence (the transcription-independent-architecture basis) is **Caco-2 only**; cross-cancer predictions rest on copy-number-coupled expression, not architecture.
- Caco-2→CRC concordance is weak genome-wide (ρ≈0.12); validation is locus-level and by-cancer-coherence, not per-BDP predictive accuracy.
- Predictions are measured associations, **not** experimentally confirmed drivers.
- 104 architecturally-defined BDPs (clone-ID lncRNA arms) are not resolvable in the pan-cancer data.

## Citation

If you use BEACON, please cite the companion PLAGL2–POFUT1 locus study and the compact-BDP atlas (citations pending; see `manuscript/`).

## License

MIT — see [LICENSE](LICENSE).
