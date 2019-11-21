library(readr)

library(tidyverse)

library(DeSeq2)
>The library command is used before plotting to allow access to the packages with the tools needed to make our plots.

### Volcano Plot

ggplot() + 

  geom_point(data=res3, aes(x=log2FoldChange, y=-log10(padj)), color='blue') + 
  
  geom_point(data=res4, aes(x=log2FoldChange, y=-log10(padj)), color='red') +
  
  ggtitle("Mutant vs Control Differential Expression") +
  
  xlab("Log2 Fold Change") +
  
  ylab("-Log10 Adjusted P-value")
  >To create a volcano plot, the ggplot command is used, normally included in the parentheses is the name of the data file you wish plot, but because we are plotting data from two separate files the names of these files are specified after geom_point using data=.
  geom_point is used to specify that this plot will use points and aes, is used to state what column the X and Y axes will be and using color= can color points a specific color, in this case blue for control and red for the mutant.
  ggtitle is used to name the plot and xlab and ylab are to label the X and Y axes.
  
  
### Positive Fold Change Boxplot

plotCounts(dds, gene="Solyc11g028040.1.1", intgroup="dex", returnData=TRUE) %>%

  ggplot(aes(dex,count))+
  
  geom_boxplot(aes(fill=dex))+
  
  scale_y_log10() + 
  
  ggtitle("Solyc11g028040.1.1")+
  
  xlab("Treatment")+
  
  ylab("Log10 Expression")+
  
  theme(legend.position = "none")
  
### Negative Fold Change Boxplot

plotCounts(dds, gene="Solyc09g089500.2.1", intgroup="dex", returnData=TRUE) %>%
  
  ggplot(aes(dex,count))+
  
  geom_boxplot(aes(fill=dex))+
  
  scale_y_log10() + 
  
  ggtitle("Solyc09g089500.2.1")+
  
  xlab("Treatment")+
  
  ylab("Log10 Expression")+
  
  theme(legend.position = "none")
   >The plotCounts command allows you to plot the expression of a particular gene.
  For these plots we used the genes with highest positive and negative fold changes.
  intgroup specifies that we are using differential expression data and returnData=TRUE allows us to return to the raw data for our gene.
  As plotCounts alone does not make the best plots by using %>% we can combine plotCounts with ggplot.
  ggplot(aes(dex,count)) specifies that we want our x axis to show our mutant and control and our y axis to show their expression.
  We add scale_y_log10() so that our amount of expression can be more easily seen.
  geom_boxplot specifies that we want our data in the form of a box plot and using aes, that it's fill should be based on the gene's expression.
  As in the previous command ggtitle is used to the name the graph, xlab labels the x axis, and ylab labels the y axis.
  theme(legend.position = "none") specifies that we do not want a legend.
  
### MA Plot

ggplot() + 
  
  geom_point(data=res3, aes(x=log10(baseMean), y=log2FoldChange), color='blue') + 
  
  geom_point(data=res4, aes(x=log10(baseMean), y=log2FoldChange), color='red') +
  
  ggtitle("Mutant vs Control Mean Expression") +
  
  xlab("Log10 Base Mean") +
  
  ylab("Log2 Fold Change")
  >To make an MA plot, ggplot is also used. Similar to the volcano plot, because we are using two datasets, the first set of paratheses is left blank.
  Like our volcano plot we use two geom_point commands to specify there are two different point types. data= is used to specify the file from which we wish to pull our data and aes is used to specify the x axis, y axis, and point color.
  As this is an MA plot, which has log10 mean expression as the x-axis, and our data just includes the base mean, we need to make our x axis command log10(baseMean), which converts our base mean to log10 basemean.
  Just like our other plots, ggtitle is used to name the plot, xlab is used to label the x axis, and ylab is used to label the y-axis.
