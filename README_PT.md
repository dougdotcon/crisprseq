# CRISPRseq

[![Status CI GitHub Actions](https://github.com/nf-core/crisprseq/actions/workflows/ci.yml/badge.svg)](https://github.com/nf-core/crisprseq/actions/workflows/ci.yml) [![Status Linting GitHub Actions](https://github.com/nf-core/crisprseq/actions/workflows/linting.yml/badge.svg)](https://github.com/nf-core/crisprseq/actions/workflows/linting.yml) [![AWS CI](https://img.shields.io/badge/CI%20tests-full%20size-FF9900?labelColor=000000&logo=Amazon%20AWS)](https://nf-co.re/crisprseq/results) [![Citar com Zenodo](http://img.shields.io/badge/DOI-10.5281%2Fzenodo.7598496-1073c8?labelColor=000000)](https://doi.org/10.5281/zenodo.7598496)

[![Nextflow](https://img.shields.io/badge/nextflow%20DSL2-%E2%89%A524.04.2-23aa62.svg)](https://www.nextflow.io/) [![executar com conda](http://img.shields.io/badge/executar%20com-conda-3EB049?labelColor=000000&logo=anaconda)](https://docs.conda.io/en/latest/) [![executar com docker](https://img.shields.io/badge/executar%20com-docker-0db7ed?labelColor=000000&logo=docker)](https://www.docker.com/) [![executar com singularity](https://img.shields.io/badge/executar%20com-singularity-1d355c.svg?labelColor=000000)](https://sylabs.io/docs/)

## Introdução

O **CRISPRseq** é uma pipeline de bioinformática de "melhores práticas" para análise de dados editados por CRISPR. Ele permite a avaliação da qualidade de experimentos de edição gênica usando dados de sequenciamento de nova geração (NGS) direcionados (`targeted`) e a descoberta de genes importantes a partir de telas CRISPR de ativação ou knockout usando DNA agrupado (`screening`).

A pipeline suporta a análise de:
- Knockouts (KO) de genes via CRISPR
- Knock-ins (KI) via CRISPR
- Edição de base (BE) e edição de primeira (PE)
- Experimentos de triagem (KO, CRISPRa (ativação) ou CRISPRi (interferência))

Construída com [Nextflow](https://www.nextflow.io), ela executa tarefas em múltiplas infraestruturas de computação, suportando containerização via Docker, Singularity ou Conda para garantir reprodutibilidade.

## Início Rápido

1. **Instale o Nextflow**:
   bash
   curl -s https://get.nextflow.io | bash
   mv nextflow ~/bin
   

2. **Execute a Pipeline**:
   - **Modo Direcionado (Targeted)**:
     bash
     nextflow run nf-core/crisprseq -profile docker --mode targeted --input samplesheet.csv --genome GRCh38
     
   - **Modo Triagem (Screening)**:
     bash
     nextflow run nf-core/crisprseq -profile docker --mode screening --input samplesheet.csv --genome GRCh38
     

3. **Configuração**: Consulte a [documentação](https://nf-core.github.io/crisprseq/) para parâmetros completos e preparação da planilha de amostras (samplesheet).

## Visão Geral da Pipeline

### Modo Targeted (Direcionado)
1. **Processamento de Leituras**: Controle de qualidade com FastQC e limpeza com Trimmomatic/Trim Galore.
2. **Alinhamento**: Leituras alinhadas ao genoma de referência (BWA/Bowtie2).
3. **Chamada de Variantes**: Detecção de indels usando ferramentas como GATK ou VarScan.
4. **Eficiência de Edição**: Quantificação de edições e visualizações.

### Modo Screening (Triagem)
1. **Contagem de Leituras**: Geração de tabelas de contagem a partir de arquivos FASTQ.
2. **Normalização**: MAGeCK ou CRISPRCleanR para normalização.
3. **Análise Estatística**: Identificação de guias significativamente enriquecidos ou depletados.
4. **Ranking de Genes**: Geração de saídas MAGeCK RRA ou BAGEL.

## Contribuições & Suporte

- **Slack**: Participe do canal `#crisprseq` no [nf-core Slack](https://nfcore.slack.com/).
- **Issues**: Relate bugs e solicite novas funcionalidades na [página de Issues do GitHub](https://github.com/nf-core/crisprseq/issues).

## Citação

Se você utilizar esta pipeline, por favor cite:

> CRISPRseq [Internet]. Disponível em: https://github.com/nf-core/crisprseq
> 
> Ewels, P. A., et al. (2020). "nf-core: Community curated bioinformatics pipelines." bioRxiv. https://doi.org/10.1101/604637

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7598496.svg)](https://doi.org/10.5281/zenodo.7598496)