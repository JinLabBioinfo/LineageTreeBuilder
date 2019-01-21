local directory: /mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/Esdrived_DGE/AttemptFrom17.8.28/TreCCAtree

### Loading packages
```
library(EZsinglecell)
```


### To check if we can combine S6 data all together
```
S6.KO1.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6KO1_N704_1/S6KO19212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.KO1.dge[,1]<-gsub("-",".",S6.KO1.dge[,1])

S6.KO2.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6KO2_N701_1/S6KO29212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.KO2.dge[,1]<-gsub("-",".",S6.KO2.dge[,1])

S6.D.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6wt_N702_1/S6wt9212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.D.dge[,1]<-gsub("-",".",S6.D.dge[,1])

s6.A.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/7.31.17_Nova/C101HW17070085/raw_data/S_17_7_5_lib_CW/N704_5.19_S6/17_5_19_S6.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s6.A.dge[,1]<-gsub("-",".",s6.A.dge[,1])

s6.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S6_9.8.17.N705/9.8.S6.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s6.B.dge[,1]<-gsub("-",".",s6.B.dge[,1])

s6.C.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S6_11_30_17_N704/S6_11_30_17.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s6.C.dge[,1]<-gsub("-",".",s6.C.dge[,1])

AllS6.ob<-docluster.multi(Number=500,txcutoff=500,sets=list(S6.KO1=S6.KO1.dge,S6.KO2=S6.KO2.dge,s6.A=s6.A.dge,s6.B=s6.B.dge,s6.C=s6.C.dge,S6.D=S6.D.dge),nms=c("S6.KO1","S6.KO2","s6.A","s6.B","s6.C","S6.D"),israw=T)

AllS6.half.ob<-docluster.multi(Number=500,txcutoff=500,sets=list(S6.KO1=S6.KO1.dge,S6.KO2=S6.KO2.dge,s6.A=s6.A.dge,S6.D=S6.D.dge),nms=c("S6.KO1","S6.KO2","s6.A","S6.D"),israw=T)
saveRDS(AllS6.half.ob,"/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/Esdrived_DGE/AttemptFrom17.8.28/RDS/AllS6.half.ob.rds")
Fullplot_v2(AllS6.half.ob,"./localPDF/AllS6.half.ob.pdf",topgene=NULL,resolusion="res.0.6",signiture=c("INS","GCG","SST","PPY","KRT19","COL1A2","REG1A","DNAJB1","GHRL"))


AllS6.AD.ob<-docluster.multi(Number=500,txcutoff=500,sets=list(s6.A=s6.A.dge,S6.D=S6.D.dge),nms=c("s6.A","S6.D"),israw=T)
Fullplot_v2(AllS6.AD.ob,"./localPDF/AllS6.AD.ob.pdf",topgene=NULL,resolusion="res.0.6",signiture=c("INS","GCG","SST","PPY","KRT19","COL1A2","REG1A","DNAJB1","GHRL"),Pheatmap=F)

Fullplot_v2(AllS6.ob,"./localPDF/AllS6.ob.pdf",topgene=NULL,resolusion="res.0.6",signiture=c("INS","GCG","SST","PPY","KRT19","COL1A2","REG1A","DNAJB1","GHRL"))
```


### Full dataset clustering
```
H1.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/H1_N701_8.17/H1.8.17.17.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
H1.dge[,1]<-gsub("-",".",H1.dge[,1])

s0.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S0_N705_9.7/S0_9.7.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s0.dge[,1]<-gsub("-",".",s0.dge[,1])

s1.24.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S1.24h_11_30_17_N701/S1.24h_11_30_17.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s1.24.dge[,1]<-gsub("-",".",s1.24.dge[,1])

s1.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S1_9.8.17.N702/9.8.S1.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s1.dge[,1]<-gsub("-",".",s1.dge[,1])

s2.24.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S2.24h_11_30_17_N702/S2.24h_11_30_17.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s2.24.dge[,1]<-gsub("-",".",s2.24.dge[,1])

s2.48.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S2.48h_11_30_17_N703/S2.48h_11_30_17.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s2.48.dge[,1]<-gsub("-",".",s2.48.dge[,1])

s2.A.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S2_9.8.17.N703/9.8.S2.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s2.A.dge[,1]<-gsub("-",".",s2.A.dge[,1])

s2.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S2_N702_9.7/S2.9.12.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s2.B.dge[,1]<-gsub("-",".",s2.B.dge[,1])

s3.A.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S3_9.8.17.N706/9.8.S3.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s3.A.dge[,1]<-gsub("-",".",s3.A.dge[,1])

s3.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/S3_N703_9.15/S3_9.15.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s3.B.dge[,1]<-gsub("-",".",s3.B.dge[,1])

s4.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/7.31.17_Nova/C101HW17070085/raw_data/S_17_7_5_lib_CW/N706_6.2_S4/1706_02_S4.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s4.B.dge[,1]<-gsub("-",".",s4.B.dge[,1])

s5.A.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/N702_5.11_S5/17_5_11_S5.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s5.A.dge[,1]<-gsub("-",".",s5.A.dge[,1])    ### 2017-5-11

s5.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/N702_2017.7.9_S5/2017_7_9_S5.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s5.B.dge[,1]<-gsub("-",".",s5.B.dge[,1])

S6.KO1.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6KO1_N704_1/S6KO19212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.KO1.dge[,1]<-gsub("-",".",S6.KO1.dge[,1])

S6.KO2.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6KO2_N701_1/S6KO29212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.KO2.dge[,1]<-gsub("-",".",S6.KO2.dge[,1])

S6.D.dge<-read.table("/mnt/NFS/genetics01/JinLab/ksl9/dropseq9192018/hwftp.novogene.com/C101HW18071824/raw_data/S6wt_N702_1/S6wt9212018.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
S6.D.dge[,1]<-gsub("-",".",S6.D.dge[,1])

s6.A.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/7.31.17_Nova/C101HW17070085/raw_data/S_17_7_5_lib_CW/N704_5.19_S6/17_5_19_S6.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s6.A.dge[,1]<-gsub("-",".",s6.A.dge[,1])



s7.B.dge<-read.table("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/7.31.17_Nova/C101HW17070085/raw_data/S_17_7_5_lib_CW/N705_5.29_S7/17_5_29_S7.gene_exon_tagged.cleaned.dge.txt.gz",header=TRUE,stringsAsFactors=FALSE)
s7.B.dge[,1]<-gsub("-",".",s7.B.dge[,1])

# Do manual clustering
library(RColorBrewer)
library(dplyr)
library(EZsinglecell)
Allall.ob<-docluster.multi(Number=500, txcutoff = 500, sets=list(H1.dge,s0.dge,s1.24.dge,s1.dge,s2.24.dge,s2.48.dge,s2.A.dge,s2.B.dge,s3.A.dge,s3.B.dge,s4.B.dge,s5.A.dge,s5.B.dge,S6.KO1.dge,S6.KO2.dge,S6.D.dge,s6.A.dge,s7.B.dge),nms=c("H1","S0","S1_D1","S1_D2","S2_D1","S2_D2","S2_D3","S2_D3","S3","S3","S4","S5","S5","S6","S6","S6","S6","S7"), selected = NULL, filterstuff = NULL, reso = 0.6, israw = T, dofindcluster = T, dotsne = T, acphi = 2500)

Allall.ob<-readRDS("/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/Esdrived_DGE/AttemptFrom17.8.28/RDS/Allall.ob.rds")
Allall.tsnewithsample<-Tomerge_v2(Allall.ob@tsne.rot,Allall.ob@data.info)
Allall.tsnewithsample$Sample<-factor(Allall.tsnewithsample$Sample,levels=c("H1","S0","S1_D1","S1_D2","S2_D1","S2_D2","S2_D3","S3","S4","S5","S6","S7"))

p.tsne.sample<-ggplot(Allall.tsnewithsample)+aes(tSNE_1,tSNE_2,color=Sample)+geom_point(size=0.4)+scale_color_manual(values=colorRampPalette(brewer.pal(11, "Spectral"))(12))+guides(colour = guide_legend(override.aes = list(size=15)))

png("./png/Allall.tsne.png",height=1500,width=1500,res=120)
format2(p.tsne.sample,Allall.tsnewithsample,"tSNE_1","tSNE_2",nolegend=F)+theme(axis.text=element_blank(),axis.ticks=element_blank(),axis.title=element_blank(),legend.title=element_blank(),legend.key=element_blank(),legend.text=element_text(size=20))
dev.off()
allall.sig<-GettsnesignatureSuper(Allall.ob, Allall.ob, signiture = c("INS", "GCG","CHGA", "CHGB", "SOX2", "NANOG"), doPCA = F, dotSNE = T,usePC34 = F, extratitle = "", toreturn = T, dotsize = 0.3,buttomgrey = T, nolegend = T, highcolor = "red")

png("./png/allall.tsne.ins.png",height=500,width=500,res=100)
allall.sig[[1]]+theme(axis.text=element_blank(),axis.ticks=element_blank(),axis.title=element_blank(),legend.title=element_blank(),title=element_blank())
dev.off()

png("./png/allall.tsne.GCG.png",height=500,width=500,res=100)
allall.sig[[2]]+theme(axis.text=element_blank(),axis.ticks=element_blank(),axis.title=element_blank(),legend.title=element_blank(),title=element_blank())
dev.off()
png("./png/allall.tsne.sox2.png",height=500,width=500,res=100)
allall.sig[[5]]+theme(axis.text=element_blank(),axis.ticks=element_blank(),axis.title=element_blank(),legend.title=element_blank(),title=element_blank())
dev.off()

png("./png/allall.tsne.nanog.png",height=500,width=500,res=100)
allall.sig[[6]]+theme(axis.text=element_blank(),axis.ticks=element_blank(),axis.title=element_blank(),legend.title=element_blank(),title=element_blank())
dev.off()



ggplot(Allall.tsnewithsample)+aes(tSNE_1,tSNE_2,color=Sample)+geom_point()+scale_color_manual(values=colorRampPalette(brewer.pal(9, "Reds"))(12))

cbind(Allall.tsnewithsample,tag=ifelse(Allall.tsnewithsample$Sample=="S5","S5",NA)) %>% ggplot()+aes(tSNE_1,tSNE_2,color=tag)+geom_point()


Allall.pcaewithsample<-Tomerge_v2(Allall.ob@pca.rot,Allall.ob@data.info)
Allall.pcaewithsample$Sample<-factor(Allall.pcaewithsample$Sample,levels=c("H1","S0","S1_D1","S1_D2","S2_D1","S2_D2","S2_D3","S3","S4","S5","S6","S7"))
ggplot(Allall.pcaewithsample)+aes(PC1,PC2,color=Sample)+geom_point()+scale_color_manual(values=colorRampPalette(brewer.pal(9, "Reds"))(12))
ggplot(Allall.pcaewithsample)+aes(PC2,PC3,color=Sample)+geom_point()+scale_color_manual(values=colorRampPalette(brewer.pal(9, "Reds"))(12))

mytopgenes<-Gettopgenes(Allall.ob, 10)  # Sometimes, precalculated cluster gene signatures can save some time
Fullplot_v2(S7rock_1.ob,"S7rock_1.ob.pdf",topgene=NULL,resolusion="res.0.6",signiture=c("INS","GCG","SST","PPY","KRT19","COL1A2","REG1A","DNAJB1","GHRL"))
Fullplot_v2(Allall.ob,"Allall.ob.pdf",topgene=mytopgenes,resolusion="res.0.6",signiture=c("INS","GCG","PPY","SST","SOX2","NANOG","COL1A2","KRT19"))


GettsnesignatureSuper(Allall.ob, Allall.ob, signiture = c("INS", "GCG","CHGA", "CHGB", "SOX2", "NANOG"), doPCA = F, dotSNE = T,usePC34 = F, extratitle = "", toreturn = F, dotsize = 0.3,buttomgrey = T, nolegend = T, highcolor = "red")

allall.sig<-GettsnesignatureSuper(Allall.ob, Allall.ob, signiture = c("INS", "GCG","CHGA", "CHGB", "SOX2", "NANOG"), doPCA = F, dotSNE = T,usePC34 = F, extratitle = "", toreturn = F, dotsize = 0.3,buttomgrey = T, nolegend = T, highcolor = "red")



```



Allall.ob<-pbmc
saveRDS(Allall.ob,"/mnt/NFS/homeGene/JinLab/cxw486/Dropseq/Entrance/Esderived/Esdrived_DGE/AttemptFrom17.8.28/RDS/Allall.ob.rds")

Allall.ob <- PCA(Allall.ob, pc.genes = Allall.ob@var.genes, do.print = TRUE, pcs.print = 5, genes.print = 5)
Allall.ob <- ProjectPCA(Allall.ob)
Allall.ob <- RunTSNE(Allall.ob, dims.use = 1:10, do.fast = T)
Allall.ob <- FindClusters(Allall.ob, pc.use = 1:10, resolution = reso, print.output = 0, save.SNN = T)
