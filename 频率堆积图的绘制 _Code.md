* 频率堆积图的绘制

* ```
  
  data<-read.delim("clipboard",header = TRUE, 
                   row.names = 1,check.names = FALSE)
  data<-as.data.frame(data)
  
  
  library(ggplot2)
  
  library(RColorBrewer)
  
  ggplot(data=data,aes(Class,data$`Times Identified in Strains`,fill=data$Metabolites))+
    
    #如果是针对分组的柱形图，则position除了可以"identity"(不调整，组内前后重叠)、还包括“stack“（堆积，默认）；"fill"(按比例堆积)；“dodge“（分散开）
    
    geom_bar(stat="identity",position="stack", color="black", width=0.7,size=0.25)+
    
   # scale_fill_manual(values=c("red", "blue", "green","darkgreen","black"))+
    
    # 添加x，y轴名
    
    labs(x = "Class",y = "Number of Subclasses And Times Detected Among Entire 110 samples in total")+
    
    # 坐标轴延伸，确保图形元素覆盖至坐标
    
    scale_y_continuous(expand = c(0,0))  + 
    theme_classic()+scale_y_continuous(breaks=seq(0,1200,100))+
    
    # 设置主题
    
    theme(panel.background=element_rect(fill="white",colour="black",size=0.25), # 填充框内主题颜色，边框颜色和边框线条粗细
          
          axis.line=element_line(colour="black",size=0.25), # x,y轴颜色，粗细
          
          axis.title=element_text(size=6,color="black"), # x,y轴名设置
          
          axis.text = element_text(size=5,color="black"), # x,y轴文本设置
          
          legend.position= c(0.9,0.85) # 显示图例，c(x,y)这里指将轴默认为1，里面的数字为轴的占比
          
    )+theme(legend.position = "none")+ coord_flip()+   theme( panel.grid.minor = element_line(size = 0.25, linetype = 2,
                                      colour = "black"))
  
  ```

* 