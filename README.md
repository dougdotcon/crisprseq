# CRISPRseq

[![GitHub Actions CI Status](https://github.com/nf-core/crisprseq/actions/workflows/ci.yml/badge.svg)](https://github.com/nf-core/crisprseq/actions/workflows/ci.yml) [![GitHub Actions Linting Status](https://github.com/nf-core/crisprseq/actions/workflows/linting.yml/badge.svg)](https://github.com/nf-core/crisprseq/actions/workflows/linting.yml) [![AWS CI](https://img.shields.io/badge/CI%20tests-full%20size-FF9900?labelColor=000000&logo=Amazon%20AWS)](https://nf-co.re/crisprseq/results) [![Cite with Zenodo](http://img.shields.io/badge/DOI-10.5281%2Fzenodo.7598496-1073c8?labelColor=000000)](https://doi.org/10.5281/zenodo.7598496) [![nf-test](https://img.shields.io/badge/unit_tests-nf--test-337ab7.svg)](https://www.nf-test.com)

[![Nextflow](https://img.shields.io/badge/nextflow%20DSL2-%E2%89%A524.04.2-23aa62.svg)](https://www.nextflow.io/) [![run with conda](http://img.shields.io/badge/run%20with-conda-3EB049?labelColor=000000&logo=anaconda)](https://docs.conda.io/en/latest/) [![run with docker](https://img.shields.io/badge/run%20with-docker-0db7ed?labelColor=000000&logo=docker)](https://www.docker.com/) [![run with singularity](https://img.shields.io/badge/run%20with-singularity-1d355c.svg?labelColor=000000)](https://sylabs.io/docs/) [![Launch on Seqera Platform](https://img.shields.io/badge/Launch%20%F0%9F%9A%80-Seqera%20Platform-%234256e7)](https://cloud.seqera.io/launch?pipeline=https://github.com/nf-core/crisprseq)

[![Get help on Slack](http://img.shields.io/badge/slack-nf--core%20%23crisprseq-4A154B?labelColor=000000&logo=slack)](https://nfcore.slack.com/channels/crisprseq) [![Follow on Twitter](http://img.shields.io/badge/twitter-%40nf__core-1DA1F2?labelColor=000000&logo=twitter)](https://twitter.com/nf_core)

## Introduction

**CRISPRseq** is a bioinformatics best-practice analysis pipeline for CRISPR edited data. It evaluates the quality of gene editing experiments using targeted NGS data (`targeted`) and identifies important genes from CRISPR screens using pooled DNA (`screening`).

The pipeline supports the analysis of:
- CRISPR gene knockouts (KO)
- CRISPR knock-ins (KI)
- Base editing (BE) and prime editing (PE) experiments
- CRISPR screening experiments (KO, CRISPRa (activation), or CRISPRi (interference))

Built using [Nextflow](https://www.nextflow.io), it runs tasks across multiple compute infrastructures with ease, supporting containerization via Docker, Singularity, or Conda for reproducible results.

## Quick Start

1. **Install Nextflow**:
   bash
   curl -s https://get.nextflow.io | bash
   mv nextflow ~/bin
   

2. **Run the Pipeline**:
   - **Targeted Analysis**:
     bash
     nextflow run nf-core/crisprseq -profile docker --mode targeted --input samplesheet.csv --genome GRCh38
     
   - **Screening Analysis**:
     bash
     nextflow run nf-core/crisprseq -profile docker --mode screening --input samplesheet.csv --genome GRCh38
     

3. **Configuration**: Check the [documentation](https://nf-core.github.io/crisprseq/) for full parameters and samplesheet preparation.

## Documentation

The CRISPRseq pipeline comes with full documentation in the [nf-core/crisprseq GitHub repository](https://github.com/nf-core/crisprseq). Please refer to the [usage documentation](https://nf-core.github.io/crisprseq/usage/) for detailed instructions on input requirements and parameter configuration.

## Pipeline Overview

### Targeted Mode
1. **Read Processing**: Quality control with FastQC, trimming with Trimmomatic/Trim Galore.
2. **Alignment**: Reads aligned to reference genome (BWA/ Bowtie2).
3. **Variant Calling**: Indel detection using tools like GATK or VarScan.
4. **Editing Efficiency**: Quantification of edits and visualizations.

### Screening Mode
1. **Read Counting**: Generation of count tables from FASTQ files.
2. **Normalization**: MAGeCK or CRISPRCleanR for read count normalization.
3. **Statistical Analysis**: Identification of significantly enriched or depleted guides.
4. **Gene Ranking**: Generation of MAGeCK RRA or BAGEL output.

## Contributions & Support

- **Slack**: Join the `#crisprseq` channel on the [nf-core Slack](https://nfcore.slack.com/).
- **Issues**: Please report bugs and feature requests on the [GitHub Issues page](https://github.com/nf-core/crisprseq/issues).

## Citation

If you use this pipeline, please cite:

> CRISPRseq [Internet]. Available from: https://github.com/nf-core/crisprseq
> 
> Ewels, P. A., et al. (2020). "nf-core: Community curated bioinformatics pipelines." bioRxiv. https://doi.org/10.1101/604637

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7598496.svg)](https://doi.org/10.5281/zenodo.7598496)