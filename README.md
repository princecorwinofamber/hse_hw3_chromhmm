| Метка | Файл |
|---:|:---|
| CTCF | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41CtcfAlnRep1.bam |
| EZH2 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41Ezh239875AlnRep1.bam |
| H4K20me1 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H4k20me1AlnRep1.bam |
| H3K27ac | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k27acAlnRep1.bam |
| H3K79me2 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k79me2AlnRep1.bam |
| H3K36me3 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k36me3AlnRep1.bam |
| H2AFZ | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H2azAlnRep1.bam |
| H3K27me3 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k27me3AlnRep1.bam |
| H3K04me3 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k04me3AlnRep1.bam |
| H3K04me1 | hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k04me1AlnRep1.bam |


[cellmarkfiletable](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/cellmarkfiletable.txt)


[google colab notebook](https://colab.research.google.com/drive/1EF1XlW3EW4-OmLiFUCZj-vro5173BEhs?usp=sharing)


[папка с выдачей ChromHMM](https://github.com/princecorwinofamber/hse_hw3_chromhmm/tree/main/learned_model)


Картинки из выдачи ChromHMM:


![](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/Dnd41_10_overlap.png)
![](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/Dnd41_10_RefSeqTSS_neighborhood.png)
![](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/Dnd41_10_RefSeqTES_neighborhood.png)


Таблица свойств:
| эпигенетический тип | характерные метки | категории | присвоенные названия |
|---:|:---|:---|:---|
| 1 | H3K36me3 | RefSeqExon, RefSeqGene, RefSeqTes | Экзон, transcriptional translation, Терминатор |
| 2 | H3K36me3 | RefSeqGene | transcriptional translation |
| 3 | H3K36me3, H4K20me1, H3K79me2 | RefSeqGene | transcriptional translation |
| 4 | H3K36me3, H4K20me1, H3K79me2, H3K04me1, K27ac, H3K04me3 | RefSeqGene, RefSeqTes | transcriptional translation, Терминатор |
| 5 | H3K04me1, K27ac | laminB1lads | Гетерохроматин |
| 6 | H3K79me2, H3K04me1, K27ac, H3K04me3, H2AFZ | CpGIsland, RefSeqExon, RefSeqTSS, RefSeqTSS2kb | Промотор, Экзон, Энхансер |
| 7 | | laminB1lads | Гетерохроматин |
| 8 | | laminB1lads | Гетерохроматин |
| 9 | H3K27me3 | laminB1lads | Гетерохроматин |
| 10 | CTCF | laminB1lads | Гетерохроматин |


![](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/uscs1.png)
![](https://github.com/princecorwinofamber/hse_hw3_chromhmm/blob/main/uscs2.png)


# Бонусное задание

tail -n +2 Dnd41_10_dense.bed > copy.bed  
Далее идёт код python  
import pandas as pd  
df = pd.read_csv("copy.bed", sep="\t")  
df.iloc[:, 3] = df.iloc[:, 3].replace({1: "1_terminator", 2: "2_translation", 3: "3_translation", 4: "4_terminator", 5: "5_heterochromatin", 6: "6_enhancer", 7: "7_heterochromatin", 8: "8_heterochromatin", 9: "9_heterochromatin", 10: "10_heterochromatin"}) # здесь для каждого эпигенетического типа был выбран наиболее заметное по данных из подходящих для него названий  
df.to_csv("modified.bed", sep="\t")  
Далее идут команды терминала  
cat <(head -n 1 Dnd41_10_dense.bed) modified.bed > renamed.bed  


Файл renamed.bed получился слишком большой, и github оказывается его принимать.
