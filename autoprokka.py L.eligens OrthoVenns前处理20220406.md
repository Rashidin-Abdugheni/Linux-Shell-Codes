1. 首先安装autoprokka.py: 因为之前有人已经公布了这个工具，所以直接用就是！
   原先创建者：

```
https://github.com/stevenjdunn/autoprokka
```

![image.png](https://upload-images.jianshu.io/upload_images/23394760-c294c3b9f2603979.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* #### 使用前提是在服务器上安装过下面两个软件：

* Python 3

* PROKKA


1） 安装autoprokka：xshell登陆后,在xshell运行以下代码即可，就可以执行了：

```
git clone https://github.com/stevenjdunn/autoprokka.git
```

然后查看它的位置：

```
whereis autoprokka.py
```

![image.png](https://upload-images.jianshu.io/upload_images/23394760-dc026817c389584f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

所以，这时候，查看自己的工作目录，就发现已获得了：
![image.png](https://upload-images.jianshu.io/upload_images/23394760-8b462624ee2600b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2） 参数的更改：在原作者readme文件里提示要更改一个参数，即对subprocess.call搜索，然后将那行进行替换为：

```
    subprocess.call(['prokka', fastain, '-o', fastaout, '--prefix', pre, '--kingdom', 'Archaea', '--fast'])
```

也就是说，对原始的直接进行替换即可，用wincp查看，用notepad打开，大概74行左右，搜索发现原始为：
![image.png](https://upload-images.jianshu.io/upload_images/23394760-bb8b9f223be3c6de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 实现批量注释细菌基因组：

* 说明：下面代码的解读的话就是：用python启动我放在某个文件夹内的autoprokka.py，并将-i后面的文件夹中的fasta文件注释，输出到-o后面的test文件夹下面，并且以fasta文件的名称来输出。
* 具体代码： 只需要给定自己安装autoprokka.py的位置，原始fasta基因组所在位置和需要输出的位置即可！

```
python /home/rxd2018/autoprokka/autoprokka.py -i /home/rxd2018/Prokka/ -o /home/rxd2018/TEST/

```

这样就成功输出了注释好的文件，如：
1） 这是目标fasta基因组文件：
![image.png](https://upload-images.jianshu.io/upload_images/23394760-631562dca1eab31a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2） 这是注释结果文件：
![image.png](https://upload-images.jianshu.io/upload_images/23394760-6404a92013fd6a65.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3）查看其中一个的结果为：
![image.png](https://upload-images.jianshu.io/upload_images/23394760-8acc5f0cd1a9068f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

就这样搞定了！

4） 如果只需要得到gbk文件，那么可以将上面的代码更改为：

```
python /home/rxd2018/autoprokka/autoprokka.py -i /home/rxd2018/Prokka/ -o /home/rxd2018/TEST/ -gbk
```

---

* 以下为readme文件的内容,其中写了82行那个应该是写错了，改的是subprocess.call这行！！！

```
#A script that automatically invokes prokka on a directory of FASTA genomes and neatly organises the output.

## Quick Start

autoprokka.py -i < path to directory containing assemblies > -o < path to output annotations and renamed .gff's >

## Usage

        usage: autoprokka.py [-h] -i INPUT -o OUTPUT [-gbk]

        optional arguments:
          -h, --help            show this help message and exit
          -i INPUT, --input INPUT
                                Path to directory containing assemblies to be
                                annotated
          -o OUTPUT, --output OUTPUT
                                Path to output destination.
          -gbk, --genbank       Also copies and renames genbank files into output
                                directory.
                                
### Requirements
* Python 3
* PROKKA
               
### What?
This script automatically invokes [PROKKA](https://github.com/tseemann/prokka) on a directory of prokaryotic genomes to obtain gene annotations with as little hands on time as necessary. 

The output contains subfolders and annotation files that are named according to the input .fasta filename. By default, autoPROKKA also gathers all .gff files and optionally all .gbk files for downstream use. 

### Why?
Time! This is easily my most used script on a day to day basis. Sure, a for loop would do it. But I find this neater and quicker for my usage. Want to quickly see how many genes are conserved amongst that clade of bacteria? autoprokka.py -i directory/ -o output/ && roary *.gff - 5 minutes later you have an answer.

### Adding flags to prokka
Edit line 82: 

        subprocess.call(['prokka', fastain, '-o', fastaout, '--prefix', pre])
        
To include your flags inside quotation marks followed by a comma, spaces should be replaced with a comma and another quoted field. For example to add the kingdom "Archaea" and run in fast mode, line 82 would be replaced with:

        subprocess.call(['prokka', fastain, '-o', fastaout, '--prefix', pre, '--kingdom', 'Archaea', '--fast'])


```