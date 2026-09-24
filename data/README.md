# ARTIBIOME processed data

This directory contains the processed inputs required by `ARTIBIOME_analysis_code.qmd`. Raw sequencing reads are not included because they are publicly available from the European Nucleotide Archive under project accession [PRJEB84358](https://www.ebi.ac.uk/ena/browser/view/PRJEB84358).

The files were derived from the nf-core/ampliseq 2.9.0 workflow and its PICRUSt2 output, followed by the preparation steps recorded in the Quarto analysis. Sample identifiers are consistent across the metadata, diversity results, phyloseq object, taxonomic abundance tables, and predicted functional tables.

## Files

| File | Description | Structure used by the analysis |
|---|---|---|
| `sample_metadata.tsv` | Deidentified sample metadata used to define study groups and paired observations | One row per sample, includes `ID`, `pid`, `timepoint`, `group`, and `group_label` |
| `alpha_observed_features.tsv` | Observed features alpha diversity from nf-core/ampliseq | One row per sample, sample identifier in `id` and diversity estimate in `observed_features` |
| `alpha_shannon.tsv` | Shannon alpha diversity from nf-core/ampliseq | One row per sample, sample identifier in `id` and diversity estimate in `shannon_entropy` |
| `qiime2_phyloseq.rds` | R phyloseq object used for beta-diversity analysis | Contains the ASV table, taxonomic assignments, and embedded sample metadata |
| `phylogenetic_tree.nwk` | Phylogenetic tree used to calculate weighted UniFrac distances | Newick-formatted tree with tip identifiers matching the taxa in the phyloseq object |
| `genus_absolute_abundance.tsv` | Genus-level absolute-abundance table | Genus/taxon identifier in `#OTU ID`, remaining columns are samples |
| `genus_relative_abundance.tsv` | Genus-level relative-abundance table | Genus/taxon identifier in `#OTU ID`, remaining columns are samples and are ordered to match the absolute-abundance table |
| `picrust2_ko_abundance.tsv` | PICRUSt2-predicted KEGG ortholog abundances | `function` contains the KO identifier, `description` contains its annotation, and remaining columns are samples |
| `picrust2_ec_abundance.tsv` | PICRUSt2-predicted Enzyme Classification abundances | `function` contains the EC identifier, `description` contains its annotation, and remaining columns are samples |

## Sample metadata

The analysis uses the following metadata fields:

| Column | Meaning |
|---|---|
| `ID` | Unique sample identifier |
| `pid` | Pseudonymized participant identifier used to match longitudinal samples |
| `timepoint` | Sampling period (`pre` or `post`) |
| `group` | Analysis group code |
| `group_label` | Human-readable group label used in figures |

The group codes and manuscript-facing labels are:

| `group` | `group_label` |
|---|---|
| `prePEP_HIV-` | `prePEP` |
| `postPEP_HIV-` | `postPEP` |
| `naive_HIV+` | `HIV+ lowCD4 preART` |
| `shortART_HIV+` | `HIV+ lowCD4 postART` |
| `longART_HIV+` | `HIV+ highCD4 postART` |
