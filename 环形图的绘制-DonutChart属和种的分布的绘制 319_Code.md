* 绘制属的分布和种的分布

  ```
  #count donut chart
  library(lessR)
  NUMBER <- c(1,1,1,4,1,3,1,4,1,1,20,1,1,1,6,1,1,2,1,1,2,1,1,1,6,1,1,4,1,3,1,1,1)
  names(NUMBER) <- c("Agathobacter", "Anaerobutyricum", "Anaerosacchariphilus", "Coprococcus", "Cuneatibacter", "Dorea", "Eisenbergiella", "Enterocloster", "Faecalicatena", "Faecalimonas", "Blautia", "Lachnospiraceae sp.", "Jingyaoa", "Lachnospiraceae sp.", "Roseburia", "Extibacter", "Lachnospiraceae sp.", "Jutongia", "Muricomes", "Pararoseburia", "Simiaoa", "Qiania", "Lachnospiraceae sp.", "Lacrimispora", "Mediterraneibacter", "Sellimonas", "Sporofaciens", "Lachnospira", "Wansuia", "Anaerostipes", "Wujia", "Zhenhengia", "Lachnospiraceae sp.")
                    
  p1<-pc(NUMBER, values="input",main = NULL,
        #clockwise=FALSE,
        init_angle=-19
        
         #width=6, height=6#, 
         #pdf_file='Donut-Species Within Each Genus 20220319.pdf'
         )
  ```

  