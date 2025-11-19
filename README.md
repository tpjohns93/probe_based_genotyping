---
title: "Probe_based_genotyping.md"
author: "Taylor Johnson"
date: "2025-11-10"
output: github_document
---
# Probe-based Genotyping
## Background/Overview
This repository contains scripts for deriving genotype for a cohort given SNP-specific allele count or concentrations as output from a probe-based quantitative assay platform (ex. BioRad QX200 ddPCR). This script (probe_based_genotyping.Rmd) is designed to clean and format data to derive a ratio of allele occurance per participant for a given SNP. Given the human diploid genome, ratios surrounding 0, 1, or 2+ can be interpreted in the context of the given probe-set(s) to provide heterozygous or homozygousity for a given participant.

Adjunct scripts provide the option for specific APOE genotyping (probe_based_apoe_adjunct.Rmd) as necessary, and demographic (demo_genotyping.Rmd) assessment for a quick and simple interpretation of genotype distribution accross the cohort, and figure generation. 

Assumptions
This script may be generalized per user discretion, however is currently dependent on the following experiment design parameters:
- Each well contains probes for (i) commmon and (ii) alternative alleles for a given SNP (please see data/example_raw_data.csv for clarification)
- The data is derived from human biospecimen, or other diploid genome
- Data is organized in rows defined by each well - target combination (Well ID, Sample ID, SNP target, SNP target channel, Sample concentration or counts. Example:
          A01 Sample_A common_target
          A01 Sample_A alternative_target
          A02 Sample_B common_target
          A02 Sample_B alternative_target
- User-defined parameters:
     (i)   Prope-specific allele targets
     (ii)  Genotype reference table
     (iii) Demographic table input
     (iv)  Biomarker data input
      (v)  SNP ID's

## Project Aims
Aim 1: Generate genotype base calls for each participant in a given cohort

Aim 2: Interpret relevance of each genotype grouping based on cohort demographics and biomarker data

## Analysis Plan

#### Data Preprocessing
* Step 1A: probe_based_genotyping.Rmd
* Step 1B: probe_based_apoe_adjunct.Rmd 
* Step 2: demo_genotyping.Rmd

#### Aim 1
* Analysis 1A: We will use this script: probe_based_genotyping.Rmd to generate genotype base calls for each participant in a given cohort.
* Analysis 1B: If necessary, we will use this script: probe_based_apoe_adjunct.Rmd to assign APOE ID for each participant in a given cohort after probe_based_genotyping.Rmd

#### Aim 2
* Analysis 1: We will use this script: demo_genotyping.Rmd to assist in the interpretation of genotype relevance in association with demographic data for the given cohort.

#### Interpretation
* Data visualization: We will use ggplot in R to make plots per demo_genotyping.Rmd scripts

## Data Structure
Project directory: 
```bash
probe_based_genotyping
└── scripts 
│   ├── probe_based_genotyping.Rmd
│   ├── probe_based_apoe_adjunct.Rmd
│   ├── demo_genotyping.Rmd
│   └── ignore.R
├── data
│   ├── raw_data.csv (user input)
│   ├── example_raw_data_format.csv
│   └── demographic_data.csv (user input)
└── R_output (user-generated)
    ├── Alternate_ID_coding.csv
    ├── demo_table.csv
    ├── ratio_data.csv
    ├── ratio_gene_data.csv
    ├── diagnosis_allele_age_boxplot.pdf
    └── Summary_statistics
        ├── cusp_flag_check.csv
        ├── hist_ratio_plot.pdf
        ├── ratio_0_hist_plot.pdf
        ├── ratio_1_hist_plot.pdf
        ├── ratio_2_hist_plot.pdf
        └──summary_by_bin.csv       
```
## Expected Results
This script will convert raw concentration or count data from BioRad QX200 ddPCR or other probe-based genotyping assay output to genotype. Expected results will be dependent on specific experiment question and design. 

## Responsibilities and Acknowledgements
Taylor Johnson is responsible for all scripts and information associated with this repository
