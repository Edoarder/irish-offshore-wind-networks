# Irish Offshore Wind Communication Networks

How are stakeholders in Irish offshore wind connected through organizational websites and Twitter interactions? These notebooks explore two communication networks: hyperlinks between websites and interactions between Twitter accounts. They distinguish an initial set of stakeholder organizations (seeds) from additional nodes reached through their connections.

This selection shows my exploratory Python work on graph construction, tabular data preparation, network measures, bipartite projections, category-level networks, cross-layer similarity and visualization. It contains five exploratory notebook snapshots from the research project, with their original cell contents and order preserved. It is a code sample from the exploratory workflow, rather than a release of the complete analysis used in the submitted manuscript. The exact source snapshots and preparation steps are recorded in [PROVENANCE.md](PROVENANCE.md).

## My contribution and external methods

I developed the research notebooks to turn the project tables into graphs, separate stakeholder groups, explore their connectivity, and prepare plots and tables. This attribution follows my account of the notebook work; it is not a line-by-line authorship audit. The underlying research and datasets belong to a collaborative project, and this selection does not claim sole authorship of that work.

The notebooks use pandas and NumPy for table and matrix operations, NetworkX for graph construction and network measures, and Matplotlib and Seaborn for plots. The expanded comparison notebook also uses igraph/Leiden community methods, scikit-learn metrics and exploratory PCA, and Plotly Sankey diagrams. These are applications of existing methods, not implementations of new graph or machine-learning algorithms. Imports and exploratory cells should not be read as evidence that every method was used in the manuscript. In particular, some functions labeled “Louvain” actually call Leiden or fall back to greedy modularity; see the limitations below.

## Guide to the files

| Notebook | Content | Suggested reading |
| --- | --- | --- |
| [seed_nodes.ipynb](seed_nodes.ipynb) | Builds directed hyperlink and Twitter graphs; separates seed-to-seed connections; computes degree, clustering and triangle measures; prepares category plots and LaTeX tables. | Start here for the shorter example of moving from tables to network measures. |
| [bipartite.ipynb](bipartite.ipynb) | Explores seed–discovered connections, unweighted and weighted projections, edge thresholds, graph comparisons and retweet subnetworks. | Read second for the projection and filtering workflow and its limitations. |
| [categories2.ipynb](categories2.ipynb) | Category counts, networks between categories, normalized mixing matrices, heatmaps and tables for the hyperlink and Twitter layers. | Category-level results and data composition. Binary and frequency-weighted Twitter alternatives occur in the same notebook. |
| [bipartite2.ipynb](bipartite2.ipynb) | Extends the projection work with aggregated Twitter weights, binary and weighted co-occurrence matrices, degree/strength distributions and structural summaries. | Seed and discovered projection analyses; extends the shorter `bipartite` example. |
| [winner_analysis_louvain_thr14.ipynb](winner_analysis_louvain_thr14.ipynb) | Common-node comparison, thresholds 0–40, edge overlap, degree correlations, community similarity, explicit threshold-4 and threshold-14 cells, structural tables and Sankey plots. | The broadest cross-layer analysis; the publication filename is shortened from `winner_analysis_louvain_thr14 copy 3.ipynb`; it includes both thresholds and additional exploratory analyses. |

The notebooks are independent exploratory documents with repeated setup and plotting cells. Original filenames are retained except for the shortened comparison-notebook name, whose source mapping is recorded in the provenance note. Saved outputs have been removed, so GitHub will show code and headings without the original tables or figures.

## Relation to the manuscript

The selection includes code addressing the main analysis families in the locally submitted manuscript snapshot (`Project_OWE_submitted/Draft.tex`): category networks, seed–seed and seed–discovered structure, discovered-node projections, and cross-layer backbone filtering and similarity. This is broader analytical coverage than the two shorter examples alone. It is not a figure-by-figure or numerical reproduction of that manuscript.

Coverage remains partial for communities in the discovered–discovered projections: `bipartite2` provides projection construction and structural metrics, but not the later community-composition analysis. The expanded comparison notebook's community plots concern the common-node layer graphs, which are a different analysis. Collection of the original data and the complete manuscript workflow are also outside this selection.

The notebooks retain alternative calculations, repeated plots and exploratory material, including multiplex cartography and PCA, which should not be assumed to correspond to reported manuscript results. No exact correspondence of outputs, random seeds or final parameter settings has been verified.


## Execution conditions

The input workbooks are **not included**. Their redistribution rights have not been established for this preparation, and the Twitter tables may contain account or interaction data. No replacement or synthetic dataset is supplied.

The notebooks expect these filenames in the working directory:

| Workbook | Sheets | Fields used by this selection |
| --- | --- | --- |
| `Hyperlink_data_def.xlsx` | `nodes`, `edges` | Node fields include `ID`, `Label`, `Organization Name`, `STATUS`, `Category`, `Sub-category`; edges use `Source`, `Target`. |
| `twitter_data_def.xlsx` | `tw_nodes`, `tw_edges` | Node fields include `ID`, `Label`, `Organization Name`, `Category`, `Sub-category`, `Followers`; edges use `Source`, `Target`, `Relationship`, `Date`. Status is joined from the hyperlink node table by `ID`. |

The code uses `IN` and `DISCOVERED` status values and `Retweet` as an interaction label. Some cells assign a fixed list of 16 stance labels by row position, so their meaning depends on the original seed ordering. Those assignments are preserved, not independently validated here.

Attempting execution requires a Python Jupyter environment and the imported packages: pandas, NumPy, Matplotlib, NetworkX, python-igraph, Seaborn, SciPy, scikit-learn, Plotly and IPython. The expanded comparison notebook also attempts to use `leidenalg`; some branches fall back to other community methods when it is unavailable. Reading `.xlsx` files also requires an Excel engine such as openpyxl; pandas LaTeX export may require Jinja2 depending on the pandas version. The original dependency versions were not established, and no pinned environment is provided. Some `seed_nodes` cells write `.tex` files into the working directory.

## Known limitations

These notebooks have not been executed end to end during this preparation. Static checks confirmed valid Python syntax, which does not establish successful execution or numerical correctness.

- In `seed_nodes`, cell 39 selects `Stance` from `h_nodes`, although the preceding code does not create that column. Execution depends on an input column or previous interactive state.
- In `bipartite`, cells 28 and 42 inspect graphs before their definitions later in the notebook; cell 102 similarly inspects `node_colors_missing` before its later assignment. Filtering also leaves assumptions about pandas row indices.
- Bipartite partitions are inferred from edge endpoints. Their disjointness and consistency with stakeholder status are assumed rather than checked.
- In the two shorter notebooks, Twitter interactions are added to `DiGraph` objects, which retain one edge per ordered node pair. Repeated interactions are not aggregated as frequency weights there. The expanded notebooks also contain aggregation and weighted alternatives; their binary and weighted quantities should be distinguished. In binary projection variants, weights count shared neighbors.
- Some comparisons combine directed binary seed graphs with undirected weighted projections. The quantity labeled “Hamming Distance” is an absolute difference between their adjacency arrays and should not be read as a validated binary Hamming distance. Layouts are not consistently seeded, and several cells repeat or overwrite earlier work.

Additional points for the expanded selection:

- `categories2` contains both binary counts and frequency-weighted alternatives and overwrites intermediate variables. A plotted matrix's meaning depends on the preceding cells; this preparation does not choose one calculation as the definitive manuscript version.
- `bipartite2` includes binary, raw weighted and share-normalized projections. These are distinct constructions and should not be treated as interchangeable. Repeated helper definitions and interactive state remain.
- In `winner_analysis_louvain_thr14 copy 3`, the names and plot labels referring to “Directed Louvain” do not reliably identify the algorithm executed. `_run_directed_louvain` calls igraph's Leiden routine in some branches and falls back to greedy modularity; the separate NMI helper attempts Leiden through `leidenalg` before using a fallback. Availability and library compatibility can therefore change the method. This has not been reconciled with the manuscript's Louvain description.
- The comparison notebook sweeps thresholds from 0 to 40. Separate cells then set thresholds 4 and 14 in that order and overwrite shared graph and community variables, so later plots and tables use the state left by the most recently run cell. Several methods and layouts use varying random seeds. The sweep, repeated community fits and all-pairs path calculations were not run during packaging.

These limitations are retained in the code. Reproducing research results would require the authorized inputs, an appropriate environment and a separate review of execution order and analytical assumptions.

## Preparation and reuse

Codex assisted with selecting this sample, writing the documentation, removing outputs and notebook metadata, and checking that every cell's source remained unchanged. No analytical code, functions, tests, demonstration data or results were added in this preparation. Earlier AI assistance within the research workflow has not been resolved line by line.

No license has been assigned as part of this preparation. A reuse license can be chosen after ownership and permission to release the selected code have been confirmed. Library implementations, datasets, manuscript files and third-party papers are not bundled here.
