* 参考：https://nmdc.cn/analyze/details?id=60063a780b38496ee0c908b0
* https://nmdc.cn/static/pdf/web/viewer.html?file=/static/file/analysis/CheckM.pdf

首先在服务器安装好对应的程序后，再：

```
conda activate checkm_python2.7


```

* **如果报错的话，则：**

````
IMPORTANT: You may need to close and restart your shell after running 'conda init'.

看到这个处于一脸懵逼的状态，几经探索，解决方法如下：

1  首先终端输入 source activate

2 然后终端输入 source deactivate

3 再输入你要激活的虚拟环境指令 conda activate checkm_python2.7
这样就不报错了
````


#注意：文件格式必须为fna，不然会报错找不到bin
对于多个基因组进行检测，则：（耗时长，需要等）
checkm lineage_wf /home/rxd2018/chekM/L.eligens_Genomes_bin/ /home/rxd2018/chekM/L.eligens_Genomes_bin-rslt/

比如把fna基因组文件放在某个位置，然后进行：

1. 创建bin和outfile文件夹，并把基因组放到bin**文件夹**内，再运行以下代码，<u>**运行会比较慢**</u>，但是得安心等待：

```
checkm tree /home/rxd2018/chekM/bin/ /home/rxd2018/chekM/outfile/
```

2. 检查树，进行下一步代码的运行:会比较快，然后文件夹下面

```
checkm tree_qa /home/rxd2018/chekM/outfile/ 
```

3. 生成marker文件：这个文件包含用于评估基因组的lingeage-sepecific标记位点，请注意，它是个没有后缀的文件！ 不是文件夹！这一步比较快！

   ```
   checkm lineage_set /home/rxd2018/chekM/outfile/ /home/rxd2018/chekM/marker 
   ```

4. 鉴定marker基因和评估基因组完整度和污染, 这一步会比较慢！

```
checkm analyze /home/rxd2018/chekM/marker /home/rxd2018/chekM/bin/ /home/rxd2018/chekM/outfile/
```



1. 对基因组质量进行总结

   ```
   checkm qa /home/rxd2018/chekM/marker /home/rxd2018/chekM/outfile/
   ```

   这时候，完整的计算结果就出来了：

   ![image-20220302162635803](C:\Users\Rashidin Abdugheni\AppData\Roaming\Typora\typora-user-images\image-20220302162635803.png)
