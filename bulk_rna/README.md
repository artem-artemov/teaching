# Bulk RNA-seq

## Run locally:
 * [Alignment and read counts](bulkRNAseq_STAR.ipynb)
 * [Differentially expressed genes - R DESeq2](bulkRNAseq_DESeq2.ipynb)

## Run in google colab
 * colab.google.com
 * To run R in google colab, use this link: https://colab.research.google.com/notebook#create=true&language=r
 * [Alignment and read counts - for google colab](bulkRNAseq_STAR_colab.ipynb)

Для практикума 15.12. про bulk RNA-seq есть два варианта:

 * установить у себя на компьютере conda environment (yml файл во вложении).
Предпочтительно нужно иметь 1-2 Гб свободной оперативной памяти. Установка занимает довольно много времени (около получаса), так что лучше установить заранее.

```
conda env create -f environment.yml

conda activate bulkRNA
```

 * Если есть сомнения, что хватит оперативной памяти, то можно считать в google colab. Минус в том, что работает он довольно нестабильно (приходится перезапускать).
Нам потребуется и питон, и R. Ссылка, чтобы создать R ноутбук в google colab:
https://colab.research.google.com/notebook#create=true&language=r
Само собой, понадобится аккаунт в Google.


environment.yml:
```yaml
name: bulkRNA
channels:
  - conda-forge
  - bioconda
dependencies:
  - python
  - r-essentials
  - r-base
  - star
  - htseq
  - pip
  - r-curl
  - samtools
  - jupyterlab
  - bioconductor-deseq2
  - r-pheatmap
  - r-ggplot2
```

