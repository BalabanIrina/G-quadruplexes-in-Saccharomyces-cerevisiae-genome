# G-quadruplexes-in-Saccharomyces-cerevisiae-genome
Распознавание G-квадруплексов в геноме Saccharomyces cerevisiae методами глубинного обучения

## Предобработка данных
В файле **chr.fa** находятся последоваетельности нуклеотидов 16 хромосом генома Saccharomyces cerevisiae.
В файлах **chr_plus.bed** и **chr_minus.bed** находятся интервалы последовательностей, в которых были обнаружены G-квадруплексы для положительного и отрицательного стренда соответственно.

Основные команды консоли для преобразования файлов: 

* **faidx chr.fa -i chromsizes > chr.genome** - преобразует форматы,
* **bedtools random -g chr.genome -n N -l L > randN.bed** - выделяет случайную последовательность генома в количестве **N** штук длины **L**,
* **bedtools subtract -a chr_plus_rand.bed -b chr_plus.bed -A > chr_plus_rand_test.bed** - проверка на непересечение последовательностей из **chr_plus_rand.bed** и **chr_plus.bed**, сохраняются только те последовательности, которые не пересеклись,
* **bedtools getfasta -fi chr.fa -bed chr_plus.bed -s > chr_plus_res_rev.fa** - сохраняем последовательности в буквенном формате, накладывая границы отрезков из **.bed** файла на последовательности хромосом в **chr.fa** файле.

Код на языке Python для предобработки последовательностей лежит в файле **data.ipynb**.


## Модели

Модели “BERT”, “RoBERTa”, “AlBERT”, “XLNet”, “XLM”, “FlauBERT”, “DistilBERT” и “CamemBERT” представленны с оптимальными параметрами в файле **models.ipynb**
