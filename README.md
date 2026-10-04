# SAALONOVA

**SAALONOVA** is a browser-based statistical analysis tool developed by the **Sustainable Agronomy & Agrogeochemistry Lab (SAAL), Agricultural & Food Engineering Department, Indian Institute of Technology Kharagpur**.

It is designed for analysis of balanced agricultural field experiments conducted under common experimental designs, with particular attention to the correct error strata and mean separation procedures required for factorial, split-plot, strip-plot and split-split-plot experiments.

**Version:** 3.1  
**Author:** Prof. Prithwiraj Dey  
**Institution:** Indian Institute of Technology Kharagpur, India  
**Web application:** https://www.saalkgp.in/saalonova

---

## 1. Overview

SAALONOVA provides a self-contained web interface for entering or importing experimental data and obtaining:

- year-wise ANOVA;
- tests of homogeneity of error variances across years;
- pooled ANOVA across years;
- treatment and interaction mean tables;
- standard errors and critical differences;
- mean separation using LSD/CD, DMRT or Tukey HSD;
- letter groupings for significant mean comparisons;
- coefficients of variation;
- dispersion estimates as SD or SE;
- copyable tables for Excel or Word;
- downloadable `.xls` analysis reports;
- export of entered data in long format.

The software supports the following experimental designs:

1. Completely randomised design (CRD)
2. Randomised block design (RBD/RCBD)
3. Split-plot design, with main plots in RBD
4. Strip-plot design
5. Split-split-plot design

For CRD and RBD, one to three treatment factors can be analysed. Split-plot and strip-plot designs use two factors, while split-split-plot design uses three factors.

The implementation is intended primarily for agricultural and biological field experiments in which the design is balanced and observations are available for all required treatment combinations and replications.

---

## 2. Access

The current web version is available at:

**https://www.saalkgp.in/saalonova**

The HTML application can also be downloaded from this repository and opened directly in a modern web browser.

No installation of R, Python, MATLAB or another statistical package is required to use the web application.

---

## 3. Key features

### Experimental design

Users specify:

- experimental design;
- number of treatment factors where applicable;
- number of replications/blocks;
- number of levels for each factor;
- factor names;
- level labels;
- number of years;
- year labels;
- response-variable name;
- significance level;
- mean-separation method;
- dispersion measure;
- decimal places;
- presentation style for significance letters.

### Data entry

Two data-entry modes are provided.

#### A. Wide grid

A treatment-by-replication grid is generated automatically after the design is specified.

Data can be pasted directly from Excel. The interface detects and skips a leading treatment-label column when appropriate.

#### B. Long format

Long-format data can be pasted or imported from CSV/TXT/TSV files.

The expected structure is:

```text
Year,Rep,Factor1[,Factor2,Factor3],Value
```

Example:

```text
2010-11,R1,W1,N1,10.24
2010-11,R1,W1,N2,8.70
2010-11,R1,W2,N1,11.15
```

The number of factor columns must correspond to the selected experimental design.

---

## 4. Statistical analyses

### 4.1 Year-wise ANOVA

ANOVA is performed separately for each year.

The software uses the appropriate error stratum for each experimental design. In split-plot, strip-plot and split-split-plot experiments, treatment effects are therefore not all tested against a single residual error term.

The implemented strata include:

- **CRD:** treatment effects and residual error;
- **RBD:** replication, treatment effects and residual error;
- **Split plot:** main-plot factor against Error(a), sub-plot factor and interaction against Error(b);
- **Strip plot:** horizontal-strip factor against Error(a), vertical-strip factor against Error(b), interaction against Error(c);
- **Split-split plot:** main-plot factor against Error(a), sub-plot effects against Error(b), and sub-sub-plot effects against Error(c).

This follows the design-specific error structure documented within the software. fileciteturn0file0L430-L505

### 4.2 Homogeneity across years

For multi-year analyses, error mean squares are compared across years before pooled interpretation.

SAALONOVA reports:

- Bartlett's test;
- Fmax, calculated as the largest divided by the smallest error mean square;
- chi-square statistic;
- critical chi-square value;
- P value;
- a homogeneous/heterogeneous verdict.

When error variances are heterogeneous, the software explicitly cautions against uncritical interpretation of the pooled ANOVA and recommends attention to year-wise results or a weighted analysis. fileciteturn0file0L430-L505

### 4.3 Pooled ANOVA

When more than one year is available, pooled analysis is performed with years treated as fixed.

Treatment terms and their interactions with year are tested against the pooled error associated with their experimental stratum. The treatment error components are pooled from the corresponding yearly error sums of squares and degrees of freedom. fileciteturn0file0L430-L505

### 4.4 Standard errors and critical differences

The software derives comparison-specific standard errors from the appropriate error strata.

It reports:

- SEm(±);
- SEd;
- critical difference (CD);
- the relevant t or weighted t′ statistic.

For comparisons involving two error terms, weighted t′ procedures are implemented. The software also uses Satterthwaite-type degrees of freedom where required. fileciteturn0file0L430-L505

### 4.5 Mean separation

Three options are available:

- LSD / CD, Fisher;
- DMRT, Duncan's multiple range test;
- Tukey HSD.

Significance letters are assigned so that means sharing a letter are not significantly different under the selected procedure. Interaction tables can be presented with letters across all cells or separately within rows and columns.

The implementation includes an insert-and-absorb approach for letter assignment, following the method described in the software documentation. fileciteturn0file0L430-L505

### 4.6 Dispersion and CV

Means may be displayed with:

- SD of replicates;
- SD of all plots contributing to the mean;
- SE of replicates;
- mean only.

Coefficients of variation are calculated for the relevant error strata. fileciteturn0file0L430-L505

---

## 5. Data requirements and important assumptions

SAALONOVA expects a **complete, balanced data set** for the selected design.

The software checks for empty or non-numeric cells before analysis. Missing observations are not automatically estimated or imputed. If cells are missing, the analysis is stopped and the incomplete cells are highlighted. fileciteturn0file0L430-L505

Therefore, users should not use SAALONOVA as a substitute for an analysis specifically designed for:

- unbalanced experiments;
- missing-plot estimation;
- repeated-measures models;
- split-plot experiments with incomplete observations;
- generalised linear models;
- mixed-effects models with random treatment structures;
- spatially correlated field observations.

The user remains responsible for confirming that the selected design and statistical model correspond to the actual field experiment.

---

## 6. Typical workflow

A recommended workflow is:

1. Select the experimental design.
2. Specify the number of factors, levels, replications and years.
3. Enter meaningful factor and level labels.
4. Select the response variable.
5. Select significance level and mean-separation procedure.
6. Build the data grid.
7. Paste observations from Excel or import long-format data.
8. Check that all cells contain valid numeric observations.
9. Run the analysis.
10. Examine year-wise ANOVA.
11. For multi-year data, inspect the homogeneity test before relying on pooled results.
12. Examine pooled ANOVA where appropriate.
13. Inspect mean tables, interaction tables, SEm, SEd and CD.
14. Copy tables to Excel/Word or download the `.xls` report.
15. Cite SAALONOVA in any thesis, report, article or other scholarly work using its output.

---

## 7. Example data

The application includes built-in examples for each supported experimental design.

The examples are intended for demonstration and checking the workflow. They should **not** be treated as experimental observations.

The split-plot example uses a two-year weed-management × nutrient data set, while other design examples contain simulated demonstration data. fileciteturn0file0L611-L728

---

## 8. Reproducibility and reporting

For publication-quality work, the following should be retained along with the final tables:

- raw experimental data;
- experimental design and treatment structure;
- number of replications;
- year labels;
- factor and treatment labels;
- selected significance level;
- selected mean-separation method;
- SAALONOVA version;
- the resulting analysis report;
- the software citation.

Do not report only the significance letters. The underlying ANOVA table, error term, degrees of freedom and comparison procedure should also be considered when interpreting results.

---

## 9. Methodological basis

The statistical implementation follows standard agricultural experimental-design procedures for balanced experiments. The software documentation specifically identifies the following methodological bases:

- Gomez and Gomez for analysis of agricultural experiments and pooled ANOVA;
- Panse and Sukhatme for agricultural statistical methods;
- Cochran and Cox for comparisons involving weighted t′ procedures;
- Satterthwaite-type degrees of freedom for comparisons involving different error terms;
- Piepho (2004) for compact letter display construction.

The detailed method and formulae are included in the application itself. fileciteturn0file0L430-L505

---

## 10. Technical implementation

SAALONOVA is implemented as a browser-based HTML application containing HTML, CSS and JavaScript.

The core statistical calculations, probability-distribution functions, ANOVA routines, mean comparisons, letter assignment and report generation are implemented within the application itself. The interface uses IBM Plex Sans, IBM Plex Mono and Source Serif 4, with browser/system fallbacks. fileciteturn0file0L1-L22

The application can therefore be deployed as a static web page.

### Suggested repository structure

```text
SAALONOVA/
├── index.html
├── README.md
├── CITATION.cff
├── LICENSE
├── CHANGELOG.md
└── docs/
    └── methodology.md
```

For the simplest release, the existing HTML file can be renamed to `index.html`.

---

## 11. Citation

Please cite SAALONOVA whenever its calculations, tables, outputs or methodology are used in academic work.

### APA 7th edition

> Dey, P. (2026). *SAALONOVA* (Version 3.1) [Computer software]. Sustainable Agronomy & Agrogeochemistry Lab, Agricultural & Food Engineering Department, Indian Institute of Technology Kharagpur. https://www.saalkgp.in/saalonova

### BibTeX

```bibtex
@software{dey_saalonova_2026,
  author       = {Dey, Prithwiraj},
  title        = {SAALONOVA},
  version      = {3.1},
  year         = {2026},
  institution  = {Sustainable Agronomy \& Agrogeochemistry Lab, Agricultural \& Food Engineering Department, Indian Institute of Technology Kharagpur},
  url          = {https://www.saalkgp.in/saalonova},
  note         = {Computer software}
}
```

### Citation in a manuscript

> Statistical analysis was performed using SAALONOVA v3.1 (Dey, 2026).

---

## 12. Contact

**Prof. Prithwiraj Dey**  
Sustainable Agronomy & Agrogeochemistry Lab (SAAL)  
Agricultural & Food Engineering Department  
Indian Institute of Technology Kharagpur  
West Bengal, India

Email: prithwi@agfe.iitkgp.ac.in

Web application: https://www.saalkgp.in/saalonova

---

## 13. Licence and use

The current application identifies the copyright as:

> © 2026 Prof. Prithwiraj Dey. All rights reserved.

Accordingly, the repository should not be labelled as MIT/GPL/Apache licensed unless an explicit open-source licence is subsequently chosen by the copyright holder.

If the intention is to make the source code freely reusable, a standard open-source licence can be added in a later release. Until then, the repository may be used as a public software record and source archive, subject to the copyright holder's permission for redistribution, modification or commercial use.

---

## 14. Disclaimer

SAALONOVA is a research and educational statistical software tool. Results should be checked against the experimental design, data structure and assumptions before being used in scientific publications or management decisions.

The software does not replace statistical judgement. In particular, researchers should verify the randomisation structure, error strata, independence assumptions, balance of the data and appropriateness of pooled analysis before drawing scientific conclusions.

---

## 15. Version

**SAALONOVA 3.1, 2026**

Developed by the Sustainable Agronomy & Agrogeochemistry Lab, IIT Kharagpur.
