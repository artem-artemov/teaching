# Задачи
Ожидаемый формат ответа - jupyter или rmd notebook, в формате ipynb или html.

## 1. Bulk RNA-seq
Найдите дифференциально экспрессирующиеся гены в датасете E-GEOD-139813.
https://www.ebi.ac.uk/gxa/experiments/E-GEOD-139813/Downloads

Raw counts: https://www.ebi.ac.uk/gxa/experiments-content/E-GEOD-139813/resources/DifferentialSecondaryDataFiles.RnaSeq/raw-counts

Experiment design: https://www.ebi.ac.uk/gxa/experiments-content/E-GEOD-139813/resources/ExperimentDesignFile.RnaSeq/experiment-design

В таблице counts есть две колонки, отображающие называния генов (аннотации ENSEMBL и имя гена) - можно использовать любую из них.

Подсказки в R, которые могут понадобиться:
```{r}
# вытащить колонки с 2 по 10
m = m[,2:10]

# вытащить только колонки 1 и с 3 по 10
m = m[,c(1, 3:10)]
```

## 2. Single cell RNA-seq
Проанализируйте датасет GSM4654673: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM4654673

barcodes (cells):
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_barcodes.tsv.gz

Features (genes):
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_features.tsv.gz

Count matrix:
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_matrix.mtx.gz