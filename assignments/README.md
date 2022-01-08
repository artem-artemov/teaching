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
Загрузка данных и создание матрицы каунтов (убираем мервые 2 столбца -- идентификаторы генов, столбцы, начиная с третьего -- матрица каунтов.
```{r}
#Загрузка таблицы каунтов. Разделитель - таб (\t)
tab = read.table('raw_counts.tab', header=T, sep='\t')
tab

#удаляем дупликаты
tab = tab[!duplicated(tab[,2]),]
#таблица каунтов
M = tab[,3:ncol(tab)]
#название рядов - имена генов
rownames(M) = tab[,2]
M
```

Загружаем таблицу с метаданными, упорядочиваем её в том порядке, в котором колонки в матрице каунтов.
```{r}
design = read.table('design.tab', sep='\t', header=T)
rownames(design) = design[,1]
design = design[colnames(M),]
design
```

## 2. Single cell RNA-seq
Проанализируйте датасет GSM4654673: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM4654673

Постройте UMAP embedding для клеток, определите кластеры, найдите маркерные гены, определяющие кластеры.

Нарисуйте:
* UMAP embedding, раскраска по кластерам
* Экспрессия генов на UMAP embedding: MKI67, COL1A1, CD3D, CD8A, CHGA и другие гены, которые покажутся вам интересными.
* dotplot c генами-маркерами кластеров

barcodes (cells):
https://adameykolab.srv.meduniwien.ac.at/share/teaching/scRNAseq/neuroblastoma/GSM4654673/barcodes.tsv.gz

Features (genes):
https://adameykolab.srv.meduniwien.ac.at/share/teaching/scRNAseq/neuroblastoma/GSM4654673/features.tsv.gz

Count matrix:
https://adameykolab.srv.meduniwien.ac.at/share/teaching/scRNAseq/neuroblastoma/GSM4654673/matrix.mtx.gz
