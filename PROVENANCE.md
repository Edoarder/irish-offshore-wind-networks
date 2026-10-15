# Provenance and preparation

Prepared on 15 October 2026 from the local research workspace. The source notebooks are the files with the same names immediately outside this folder, except that the prepared `winner_analysis_louvain_thr14.ipynb` comes from `winner_analysis_louvain_thr14 copy 3.ipynb`. The distinct original file already named `winner_analysis_louvain_thr14.ipynb` was not used for this copy. The checksums below identify the exact snapshots; filesystem dates were not treated as evidence of authorship or analytical finality.

## Attribution and selection

Edoardo Maggioni stated that the notebooks were generally made by him, while scripts were often made with Codex and sometimes by him. This supports attribution of the notebook work at project level, without establishing the origin of every cell or excluding earlier AI assistance. No selected cell is independently identified as a collaborator's or Codex's contribution. This uncertainty is documented rather than turned into a claim of wholly unaided authorship.

The analysis workspace has no Git repository covering these notebooks. The nested manuscript repository contains an Overleaf import and no tracked Python scripts or notebooks, so its commit authorship cannot establish notebook provenance. Exact cell overlaps with other local notebook variants corroborate reuse within the workflow, not personal authorship.

`seed_nodes` and `bipartite` provide shorter introductions. At Edoardo's request the selection was expanded, still on 15 October 2026, with three unchanged source snapshots: `categories2` for category-level networks and matrices, `bipartite2` for projection alternatives and structural summaries, and `winner_analysis_louvain_thr14 copy 3` for the threshold sweep, common-node comparisons and threshold-4/14 analyses. The last source file covers both thresholds, so separate near-duplicate threshold notebooks were not added. At Edoardo's request its prepared copy was subsequently renamed to `winner_analysis_louvain_thr14.ipynb`; only the filename and documentation references changed, and its prepared-file checksum below remains valid.

The selected `categories2` snapshot retains the weight column used by its weighted branches; the `copy 2` variant drops that column and later references it. The later `bipartite3` variants were not selected because they contain a syntax error and internal collaborator revision notes in the retained cells. No such cells were removed or corrected to make that version publishable. Consequently, community composition in discovered-node projections remains a documented coverage gap. The extended comparison file does contain experimental cartography and PCA alongside the analysis families relevant to the paper; no claim is made that all its cells generated published results.

The larger `net_analysis` snapshot substantially overlaps the shorter examples. Other notebook variants, virtual environments, data, manuscript files, figures and external papers were not copied. Omitting a notebook does not imply it was written by Codex. No external model or library implementation is included or attributed to Edoardo. The manuscript comparison uses the locally submitted `Project_OWE_submitted/Draft.tex` snapshot only to identify analysis families; correspondence with individual reported values or figures has not been validated.

## Changes and checks

Only the copies in this folder were sanitized. All notebook-level and cell-level metadata were cleared, code outputs removed, and execution counts reset to null. JSON formatting changed. Every cell, including empty cells, retains its original type, position and exact `source` field. No source text, logic, comments, headings or stance assignments were edited. None of the selected notebooks contained attachments.

Codex performed the current selection, documentation and packaging. The README and this provenance note are new, as is the `.gitignore` intended to reduce accidental inclusion of inputs and generated files. No license, dependency lockfile, new analysis, tests or results were introduced.

Verification compared each copied notebook with its source, checked Python syntax without executing cells, checked removal of outputs and metadata, and inspected the retained source for credentials, personal paths, contact details and embedded data. No credentials, personal paths, contact details or embedded datasets were identified in the selected sources; hard-coded numeric stance assignments remain disclosed in the README. No research data were executed or redistributed. Syntax checks do not validate methods or reproducibility. Runtime and methodological limitations are listed in the README, including the community-method naming mismatch in the expanded comparison file. All five notebooks passed static syntax checks; no threshold sweep, community fit or other research calculation was executed.

## Snapshot checksums

SHA-256 of the complete files (outputs and metadata explain the difference):

### `seed_nodes.ipynb`

43 cells (41 code cells); 10 saved output objects removed.

- Original file: `c645de7269219712cc90b7762720364e59578d6d9b532a35023b6b20e84f7ac6`
- Prepared file: `b6d35825abf1777708021f7675e2d0e2f3d3778674c349bf3fc644a79cea3a0d`
- Ordered cell type/source signature, identical before and after: `743d0cfe5b8b5b66d197dfe0c92ce4a9887e6bb2c3c8c06408cc5f8ecb345546`

### `bipartite.ipynb`

104 cells (100 code cells); 83 saved output objects removed.

- Original file: `9429f0e1590b485867b703783af047da3c2a6aa23fe70d695a9d29779ddefc49`
- Prepared file: `ea20a370bff7d49857dbdf570228eb9af457295c2cc2891f71fc666fa330f4b6`
- Ordered cell type/source signature, identical before and after: `940e7bba47d223e2b7420fda2132bd985994bda1811b3786535e01c38104afbc`

### `categories2.ipynb`

78 cells (73 code cells); 53 saved output objects removed.

- Original file: `d4db677d6b35898895ee639010dd1fb4a0898334f121ecc02e5343664ef185f3`
- Prepared file: `2530e07c4b7c2f68c45995f9da2e5fc8ea93f63294799d440ba33b1a8eedd84d`
- Ordered cell type/source signature, identical before and after: `687c5a82a813b83247388680ed8ca52022850d43c883ef91879b868f2cc7679b`

### `bipartite2.ipynb`

161 cells (157 code cells); 128 saved output objects removed.

- Original file: `b47cffbc501d40044fd7cdad838b4cff5a8b445a464178dbeefc91a5b880f7a4`
- Prepared file: `2d24967b5eb22cd98f1e6518f7031c958bb7c18d715ed5fc63efb2c68aef7938`
- Ordered cell type/source signature, identical before and after: `081c75493998b96c38f071fcf1b8516709e2833e077ee00f685d769330b70acb`

### `winner_analysis_louvain_thr14.ipynb`

Source: `winner_analysis_louvain_thr14 copy 3.ipynb` (not the distinct original with the shorter name).

39 cells (36 code cells); 62 saved output objects removed.

- Original file: `6844a68d7d04700c701b402bf37120133f72bf48a10550d5948a6a0db872619b`
- Prepared file: `d17a0e3359527e56ff3151926cf45dad663eea5a09ceeb96eced0b9886e49494`
- Ordered cell type/source signature, identical before and after: `f08e309dbbc4502de754723b68dc624b3461e4be0e4a3af62db7bfd514e8a410`

The cell signature is SHA-256 of UTF-8 JSON containing the ordered `(cell_type, source)` pairs, with `ensure_ascii=False` and separators `(",", ":")`. It includes all cell types and preserves the original representation of each source field.
