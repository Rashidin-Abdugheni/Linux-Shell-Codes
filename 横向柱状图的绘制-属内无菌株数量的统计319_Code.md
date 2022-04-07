横向柱状图的绘制

```
getwd()

Strain_nmbr148<-read.delim("clipboard",header = TRUE, row.names = 1,check.names = FALSE)
head(Strain_nmbr148)
write.table(Strain_nmbr148,"Numbers of Strains Within Each Genus 20220319.csv",row.names=FALSE,col.names=TRUE,sep=",")

library(ggplot2)
p1<-ggplot(data=Strain_nmbr148,  aes(x=reorder(`Genus Name`, `Number of Strains`),  y=`Number of Strains`, fill=`Genus Name`)) +
  geom_bar(stat="identity", position=position_dodge())+
  ylab("Number Of Strains Within Each Genus") + xlab("Genus Name")+
  geom_text(aes(label=`Number of Strains`),
            family = "serif",size = 3,position = position_stack(vjust = 1.09))+ 
  theme(legend.position = "none")+ 
  scale_y_continuous( breaks=seq(0,40,5)) + 
  theme(
         #panel.grid.major = element_blank(),
         axis.text.y = element_text(face = "bold.italic", family = "serif",size = 7))+
  theme(axis.text.x = element_text(family = "serif",size = 6))+coord_flip()
p1

p3<-p1+theme(
  panel.grid.major = element_blank(),
  #panel.grid.minor = element_line
  )
p3 
p4<-p3+theme(#panel.grid.major = element_line( linetype = 2,size = 0.2),
             #panel.grid.major = element_blank(),
         panel.background = element_rect(fill = "transparent",colour = "black"),
         #plot.background = element_rect(fill = "transparent",colour = NA),
         )+theme(axis.title.x = element_text(size=8,face = "bold",family = "serif"), 
                 axis.title.y = element_text(size=8,face = "bold",family = "serif"))
p4

ggsave(p4, file='Numbers of Strains Within Each Genus 20220319.pdf', width=4, height=4)
getwd()
```

