```shell
 cd /home/rxd2018/ubcg/
 for i in /home/rxd2018/rosegnm/*.fasta; do java -jar UBCG.jar extract -bcg_dir /home/rxd2018/ubcg/bcg/ -i $i -label $i -acc "" -taxon "" -strain ""-type; done
```

```shell
 java -jar UBCG.jar align -bcg_dir bcg -prefix Roseburia_Phylogenomic_tree
```

```swift
# 比如nsj-9 的基因组进化树的构建：
cd /home/rxd2018/ubcg/
 
 for i in /home/rxd2018/novelgenomes/nsj-9genomes/*.fna; do java -jar UBCG.jar extract -bcg_dir /home/rxd2018/ubcg/bcg-nsj-9/ -i $i -label $i -acc "" -taxon "" -strain ""-type; done
```

```css
 java -jar UBCG.jar align -bcg_dir /home/rxd2018/ubcg/bcg-nsj-9 -prefix NSJ-9_PhylogenomicTree20220113
```



* 安装fastANI

  ```
  git clone https://github.com/ParBLiSS/FastANI.git
  
  ```

  ![image-20220108154159100]_C:\Users\Rashidin Abdugheni\AppData\Roaming\Typora\typora-user-images\image-20220108154159100.png
  
  

```
conda install -c bioconda fastani  
```

https://anaconda.org/bioconda/fastani



fastANI 的用法：

```
cd /home/rxd2018/FASTANI/
```



1. 一对一

```
fastANI -q genome1.fasta -r genome2.fasta -o output.txt
```

2. 1对多：

```
fastANI -q NSJ-176genome. --rl /home/rxd2018/novelgenomes/nsj-176genomes/NSJ-176GenomeName_List01.txt -o /home/rxd2018/novelANI/NSJ-176-ANI_pairwiseYiDuiDuo.txt
```

3. 多对多：

```
fastANI --ql NSJ-141-GenomeName_List01.txt --rl NSJ-141-GenomeName_List02.txt -o NSJ-141-ANI_pairwise1-2.txt

fastANI --ql /home/rxd2018/novelgenomes/nsj-176genomes/NSJ-176GenomeName_List02.txt --rl /home/rxd2018/novelgenomes/nsj-176genomes/NSJ-176GenomeName_List01.txt -o /home/rxd2018/novelANI/NSJ-176-ANI_pairwise2-1.txt

```



fastANI --ql result.txt --rl result.txt -o output3.txt

fastANI --ql MERG1.txt --rl MERG2.txt -o ANI.out 

fastANI --ql MERG1.txt --rl MERG2.txt -o ANI_pairwise.out

* 合并多个文件：

```
 cat /home/rxd2018/FASTANI/query.list/*.fna > /home/rxd2018/FASTANI/query.list.txt
```

```css
 fastANI --ql NSJ-141-GenomeName_List01.txt --rl NSJ-141-GenomeName_List02.txt --matrix -o output.file -t 20
```



fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Roseburia_porci_DSM_107448T_GCF_009695765.1__.fna -o output.txt1

```css
fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__1.fasta -r Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fasta -o output1.txt

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Roseburia_inulinivorans_DSM_16841T_GCF_000174195.1__.fna -o output.txt2

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Roseburia_intestinalis_L1-82T_GCF_900537995.1__.fna -o output.txt3

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Roseburia_hominis_A2-183T_GCF_000225345.1__.fna -o output.txt4

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Roseburia_faecis_strain_M72T_GCF_001406815.1__.fna -o output.txt5

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Pseudobutyrivibrio_xylanivorans_MZ_5T_GCF_900141825.1__.fna -o output.txt6

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Pseudobutyrivibrio_ruminis_DSM_9787T_GCF_900218035.1__.fna -o output.txt7

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Lactonifactor_longoviformis_ED-Mt61_PYG-s6T_GCF_900129135.1__.fna -o output.txt8

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Lacrimispora_sphenoides_JCM_1415T_GCF_900461315.1__.fna -o output.txt9

        fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Lacrimispora_celerecrescens.fna -o output.txt10

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Lachnospira_pectinoschiza_150_1T_GCF_900103815.1__.fna -o output.txt11

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Faecalicatena_fissicatena_KCTC_15010T_GCF_016900595.1__.fna -o output.txt12

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Faecalicatena_contorta_DSM_3982T_GCF_902375555.1__.fna -o output.txt13

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Blautia_stercoris_GAM6-1T_GCF_014385405.1__.fna -o output.txt14

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Blautia_faecicola_KGMB01111T_GCF_004123145.1__.fna -o output.txt15

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r Anaerosacchariphilus_polymeriproducens_MCWD5T_GCF_003363435.1__.fna -o output.txt16

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r _Ruminococcus___gauvreauii_CCRI-16110T_GCF_902377395.1__.fna -o output.txt17

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r _Ruminococcus___gnavus_ATCC_29149T_GCF_009831375.1__.fna -o output.txt18

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r _Eubacterium___ventriosum_ATCC_27560T_GCF_003475105.1__.fna -o output.txt19

fastANI -q Roseburia_lenta_NSJ-9T_GCF_014287435.1__.fna -r _Clostridium___nexile_DSM_1787T_GCF_013300945.1__.fna -o output.txt20


```

Roseburia_hominis_A2-183T_GCF_000225345.1__.fa

```css
fastANI -q genome1.fas -r genome2.fas -o outputFinal.txt
```

