# ARTIBIOME

Code and processed data for the paper **“Impact of HIV Infection, Immune Status, and Integrase Inhibitor-Based Antiretroviral Therapy on the Gut Microbiota in Men Who Have Sex with Men With and Without HIV.”**

## 📄 Paper information

**Title:** Impact of HIV Infection, Immune Status, and Integrase Inhibitor-Based Antiretroviral Therapy on the Gut Microbiota in Men Who Have Sex with Men With and Without HIV

**Authors:** Marta Rosas Cancio-Suárez\*, Jorge Díaz-Álvarez\*, Claudio Díaz-García, Luis Miguel Nieto-Salas, Matilde Sánchez-Conde, Elena Moreno, Alejandro G. García-Ruiz de Morales, Laura Martín-Pedraza, Clara Crespillo-Andújar, María Fons-Contreras, Raquel Ron, Ana del Amo-de Palacios, Marta González-Sanz, Santiago Moreno, and Sergio Serrano-Villar

\* Equal contribution.

## 📌 Overview

**Background:** HIV infection and antiretroviral therapy (ART) influence the gut microbiota, affecting immune function and systemic inflammation. However, isolating the effects of integrase strand transfer inhibitor (INSTI)-based ART is challenging because of confounding by HIV status, immunosuppression, and behavioral factors.

**Methods:** We examined three cohorts of men who have sex with men (MSM; n = 62): HIV-negative individuals using post-exposure prophylaxis (PEP), people with HIV (PWH) with fewer than 350 CD4 cells/µL sampled before and 48 weeks after ART initiation, and PWH receiving long-term INSTI-based ART with immune recovery. Microbiota composition was analyzed by 16S rRNA sequencing, functional profiles were inferred with PICRUSt2, and differential abundance was assessed with ANCOM-BC2.

**Results:** HIV-negative participants showed significantly lower alpha diversity than PWH, and beta diversity differed according to HIV status. Short-term INSTI-based ART in PEP users was associated with limited microbiota changes. Pro-inflammatory taxa, including *Prevotellaceae*, were enriched in PWH. Predicted functional profiles showed enrichment of functions related to cell-envelope structure, membrane transport, and stress response. Long-term ART was associated with modest taxonomic and functional shifts, including enrichment of *Barnesiella* in participants with immune recovery.

**Conclusions:** HIV infection and immune suppression were the principal drivers of gut microbiota alterations in MSM, whereas INSTI-based ART was associated with comparatively modest changes.

**Keywords:** HIV; ART; gut microbiome; dysbiosis; 16S rRNA sequencing

## 📂 Repository structure

```text
├── ARTIBIOME_analysis_code.qmd   # Complete analysis as a Quarto document
├── ARTIBIOME_analysis_code.html  # Rendered analysis and results
├── data/
│   ├── README.md
│   ├── sample_metadata.tsv
│   ├── alpha_observed_features.tsv
│   ├── alpha_shannon.tsv
│   ├── qiime2_phyloseq.rds
│   ├── phylogenetic_tree.nwk
│   ├── genus_absolute_abundance.tsv
│   ├── genus_relative_abundance.tsv
│   ├── picrust2_ko_abundance.tsv
│   └── picrust2_ec_abundance.tsv
├── LICENSE
└── README.md
```

The Quarto document contains the complete analysis, identifies the corresponding manuscript figures and supplementary tables, and reports the software environment used to produce the supplied HTML.

## Data availability

Raw 16S rRNA gene sequencing reads are available from the European Nucleotide Archive under project accession [PRJEB84358](https://www.ebi.ac.uk/ena/browser/view/PRJEB84358) and are not duplicated in this repository.

The `data/` directory contains the processed inputs needed to reproduce the statistical analyses. Their contents and formats are documented in [`data/README.md`](data/README.md).

## Raw-read processing

Raw reads were processed with nf-core/ampliseq version 2.9.0 using the SILVA 138 reference taxonomy and PICRUSt2 functional prediction. The complete Nextflow command, primer sequences, filtering options, and rarefaction depth are recorded in the **Raw-read processing** section of `ARTIBIOME_analysis_code.qmd`.

Reproducing the raw-read processing requires Nextflow and a supported container engine. The statistical analysis can be reproduced directly from the processed files distributed in `data/`.

## Reproducing the analysis

Install [R](https://www.r-project.org/) and [Quarto](https://quarto.org/), clone or download this repository, and open a terminal in the repository root. The analysis uses the following R packages:

- ANCOMBC
- SummarizedExperiment
- TreeSummarizedExperiment
- ggpubr
- ggrepel
- phyloseq
- vegan
- ape
- rstatix
- tidyverse

Render the document with:

```bash
quarto render ARTIBIOME_analysis_code.qmd
```

All paths in the analysis are relative to the repository root. Keep the QMD file and the `data/` directory in the locations shown above. The exact R, platform, and package versions used for the supplied HTML are reported by `sessionInfo()` at the end of the rendered document.

The commands for exporting complete statistical tables and publication figures are included but commented out. The principal results are displayed directly in the rendered HTML.

## Analysis outline

The Quarto document performs the following steps:

1. Records the nf-core/ampliseq command used for raw-read processing.
2. Defines sample groups, display labels, and plotting helpers.
3. Compares observed ASVs and Shannon diversity across cross-sectional and longitudinal groups.
4. Calculates weighted UniFrac ordinations and PERMANOVA tests.
5. Performs genus-level differential-abundance analyses with ANCOM-BC2.
6. Performs ANCOM-BC2 analyses of PICRUSt2-predicted KEGG ortholog and Enzyme Classification profiles.
7. Reports the software environment used to render the analysis.

## Citation

If you use these data or this analysis code, please cite the accompanying ARTIBIOME article and the ENA sequencing project PRJEB84358. The final journal citation and DOI should be added here when available.

## 📜 License

Reuse is governed by the terms in [`LICENSE`](LICENSE). Third-party software, databases, and raw sequencing records remain subject to their respective terms.

## 📬 Contact

For questions about the study, data, or analysis, please contact:

- Marta Rosas Cancio Suárez ([mrcancio.3@gmail.com](mailto:mrcancio.3@gmail.com) / [marta.rosas@salud.madrid.org](mailto:marta.rosas@salud.madrid.org))
- Jorge Díaz Álvarez ([jolohinodam@gmail.com](mailto:jolohinodam@gmail.com) / [jorge.diaz@salud.madrid.org](mailto:jorge.diaz@salud.madrid.org))
- Claudio Díaz García ([claudio.digar@gmail.com](mailto:claudio.digar@gmail.com) / [claudio.diaz@salud.madrid.org](mailto:claudio.diaz@salud.madrid.org))
- Sergio Serrano Villar ([serranovillar@gmail.com](mailto:serranovillar@gmail.com) / [sergio.serrano@salud.madrid.org](mailto:sergio.serrano@salud.madrid.org))
