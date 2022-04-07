环形图的绘制：

```
#count donut chart
library(lessR)
NUMBER <- c(91,	88,	78,73,	24,		19)
names(NUMBER) <- c("Acetic acid","Propanoic acid",
                 "Butanoic acid","Pentanoic acid","Isobutyric acid",
                 "Isovaleric acid")
pc(NUMBER,  values="input",main = NULL)
```

