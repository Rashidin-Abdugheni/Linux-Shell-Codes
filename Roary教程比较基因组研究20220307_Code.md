* 参考：https://github.com/microgenomics/tutorials/blob/master/pangenome.md

1. 安装好了Roary后，将prokka注释出来的gff文件保存到某个路径下。
2. 进入到gff文件夹路径，然后运行以下代码，这个过程会很慢，在demo下面会产生多个文件夹。

```
	roary -f ./demo -e -n -v *.gff
```



3. summary_statistics.txt 文件夹下面会看到基因组结果，类似以下结果：

```
Genes 	Number
Core genes (99% <= strains <= 100%) 	2010
Soft core genes (95% <= strains < 99%) 	0
Shell genes (15% <= strains < 95%) 	2454
Cloud genes (0% <= strains < 15%) 	0
Total genes 	4464
```

以及会看到这个文件夹：gene_presence_absence.csv

When you analyze your own data, you will need a phylogeny that  represents the evolutionary history of your isolates. The inference of a phylogenetic tree is not part of roary's functions, but you can use the core gene alignment (file: `core_gene_alignment.aln`) as input to infer a tree.



---

----

* mcl的安装: 安装的是最新版本，不然报错！

* 参考：https://www.jianshu.com/p/11b9d76babba
* 参考：http://www.360doc.com/content/21/0714/12/76149697_986500299.shtml

```
wget http://www.micans.org/mcl/src/mcl-latest.tar.gz
```

```
tar xf mcl-latest.tar.gz
```

```
cd mcl-14-137
```

```
./configure --prefix=/home/rxd2018/sftwr/mcl/
```

```
make install
```

```
export PATH=/home/rxd2018/sftwr/mcl/bin/:$PATH
```

```
mcl -h
```

---

```shell
export PATH=/home/rxd2018/sftwr/mcl-14-137/src/alien/oxygen/src/:$PATH
```

* linux 环境变量的设置，参考：https://www.cnblogs.com/youyoui/p/10680329.html