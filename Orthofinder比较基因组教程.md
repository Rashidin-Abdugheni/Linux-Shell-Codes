* 参考：OrthoFinder: phylogenetic orthology inference for comparative genomics

  [GitHub - davidemms/OrthoFinder: Phylogenetic orthology inference for comparative genomics](https://github.com/davidemms/OrthoFinder)

* 安装后进行激活

```
conda activate orthofinder
```

* 查看安装在哪了：

```
which orthofinder
```

* 显示是在/home/dell/miniconda3/envs/orthofinder/bin/orthofinder，所以用以下代码进行运算，但是需要先把faa蛋白质序列文件放在orthofinder_Lach_Data文件夹下面。

  ---

* 进行运算orthologs ，这个会耗时，然后会在orthofinder_Lach_Data里面带日期的文件里看到计算结果。

```
/home/dell/miniconda3/envs/orthofinder/bin/orthofinder -f /home/rxd2018/orthofinderData/orthofinder_Lach_Data
```

![image-20220406161550341](C:\Users\Rashidin Abdugheni\AppData\Roaming\Typora\typora-user-images\image-20220406161550341.png)

![image-20220406161725817](C:\Users\Rashidin Abdugheni\AppData\Roaming\Typora\typora-user-images\image-20220406161725817.png)