* 百分比饼图的绘制

  ```
  Classes<-c("#F3CECE","#F78181","#FF0000","#8A0808","#3B0B0B",
               "#F5BCA9","#F7BE81","#FF8000","#B45F04","#8A4B08",
               "#F2F5A9","#FFFF00","#AEB404","#868A08","#BEF781",
               "#80FF00","#5FB404","#58FAAC","#01DFA5")
               
               
  pie <- ggplot(df, aes(x="", y="Number of Strains", fill="Genus Name")) +
      +     geom_bar(width = 1, stat = "identity") +
      +     coord_polar("y", start=0) +
      +     geom_text(aes(y = value/2 + c(0, cumsum(value)[-length(value)]),
                          +                   label = percent(value/353 )), size=5)
  pie
  
  p <- ggplot(data = df, mapping = aes(x = 'Content', y = df$`Number of Strains`, fill = df$`Genus Name`)) + geom_bar(stat = 'identity', position = 'stack')
  p
  p <- ggplot(data = df, mapping = aes(x = 'Content', y = `Number of Strains`, fill = Classes)) + geom_bar(stat = 'identity', position = 'stack')
  p
  p + coord_polar(theta = 'y')
  p + coord_polar(theta = 'y') + labs(x = '', y = '', title = '') + theme(axis.text = element_blank())
  label_value <- paste('(', round(df$`Number of Strains`/sum(df$`Number of Strains`) * 100, 1), '%)', sep = '')
  label_value
  
  Strain_nmbr148<-read.delim("clipboard",header = TRUE, row.names = 1,check.names = FALSE)
  
  
  label <- paste(df$`Genus Name`, label_value, sep = '')
  label
  
  p + coord_polar(theta = 'y') + labs(x = '', y = '', title = '') + theme(axis.text = element_blank()) + theme(axis.ticks = element_blank()) + scale_fill_discrete(labels = label)
  p + coord_polar(theta = 'y') + labs(x = '', y = '', title = '') + theme(axis.text = element_blank()) + theme(axis.ticks = element_blank()) + theme(legend.position = "none") 
  
  
  p + coord_polar(theta = 'y') + labs(x = '', y = '', title = '') + theme(axis.text = element_blank()) + theme(axis.ticks = element_blank()) + scale_fill_discrete(labels = label)
  
  ```

  