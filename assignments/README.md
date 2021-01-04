# Задачи
Ожидаемый формат ответа - jupyter или rmd notebook, в формате ipynb или html.

Мы понимаем, что у вас ещё не было курса по R, поэтому с ним возможны проблемы (например, загрузка data frames и манипуляция с ними). Если будут вопросы - не бойтесь спрашивать (на почту).

## 1. Bulk RNA-seq
Найдите дифференциально экспрессирующиеся гены в датасете E-GEOD-139813.
https://www.ebi.ac.uk/gxa/experiments/E-GEOD-139813/Downloads

Raw counts: https://www.ebi.ac.uk/gxa/experiments-content/E-GEOD-139813/resources/DifferentialSecondaryDataFiles.RnaSeq/raw-counts

Experiment design: https://www.ebi.ac.uk/gxa/experiments-content/E-GEOD-139813/resources/ExperimentDesignFile.RnaSeq/experiment-design

В таблице counts есть две колонки, отображающие называния генов (аннотации ENSEMBL и имя гена) - можно использовать любую из них.

Найдите дифференциально экспрессирующиеся гены между контрольными образцами и образцами, обработанными интерфероном.
Какие гены наиболее up- и downregulated? Назовите также p-value, FDR и fold change

Покажите таблицу с наиболее дифференциально экспрессируемыми генами (упорядочены по p-value).

Нарисуйте:
* Volcano plot
* Heatmap для 15 наиболее значимо дифференциально экспрессируемых генов


Подсказки в R, которые могут понадобиться:
```{r}
# вытащить колонки с 2 по 10
m = m[,2:10]

# вытащить только колонки 1 и с 3 по 10
m = m[,c(1, 3:10)]
```

## 2. Single cell RNA-seq
Проанализируйте датасет GSM4654673: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM4654673

Постройте UMAP embedding для клеток, определите кластеры, найдите маркерные гены, определяющие кластеры.

Нарисуйте:
* UMAP embedding, раскраска по кластерам
* Экспрессия генов на UMAP embedding: MKI67, COL1A1, CD3D, CD8A, CHGA и другие гены, которые покажутся вам интересными.
* dotplot c генами-маркерами кластеров

barcodes (cells):
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_barcodes.tsv.gz

Features (genes):
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_features.tsv.gz

Count matrix:
ftp://ftp.ncbi.nlm.nih.gov/geo/samples/GSM4654nnn/GSM4654673/suppl/GSM4654673_T214_matrix.mtx.gz
