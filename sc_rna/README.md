# Single cell RNA-seq (10X platform)

[Slides - artemov_scRNAseq.pdf](artemov_scRNAseq.pdf)

[Single cell RNA-seq with Seurat - scRNAseq.ipynb](scRNAseq.ipynb)


## Run in google colab
 * To run R in google colab, use this link: https://colab.research.google.com/notebook#create=true&language=r
 * [Single cell RNA-seq with Seurat - scRNAseq.ipynb](scRNAseq.ipynb)

Package installation takes 23 minutes. You can run it 15-20 minutes before we start, if you have time.

```{r}
install.packages('Seurat')
```

## Run locally:
Do not run the first cell (with package installation)  [Single cell RNA-seq with Seurat - scRNAseq.ipynb](scRNAseq.ipynb)

Use the following conda environment: ```environment.yml```

```{bash}
# do not download from git with wget, use git clone or wget from 'raw'
# git clone https://github.com/artem-artemov/teaching/blob/main/sc_rna/environment.yml
# (or)
# wget https://raw.githubusercontent.com/artem-artemov/teaching/main/sc_rna/environment.yml

conda env create -f environment.yml

conda activate bulkRNA
```


environment.yml:
```yaml
name: scRNA
channels:
  - conda-forge
  - bioconda
dependencies:
  - python
  - r-essentials
  - r-base
  - r-curl
  - jupyterlab
  - r-hdf5r
  - r-seurat
  - r-pheatmap
  - r-ggplot2

```

# Further reading
 * Tutorials
   * Official Seurat tutorial: https://satijalab.org/seurat/v3.1/pbmc3k_tutorial.html
   * Workshop -- Broad institute: https://broadinstitute.github.io/2019_scWorkshop/
 * Doublets in 10X data, doublet filtering
   * Scrublet tool: https://github.com/AllonKleinLab/scrublet
 * Other packages:
   * scanpy: https://scanpy.readthedocs.io/en/stable/
   * scvelo -- RNA velocity: https://scvelo.readthedocs.io/
   * pagoda2: https://github.com/kharchenkolab/pagoda2 
