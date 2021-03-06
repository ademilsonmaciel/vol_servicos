# vol_servicos
\documentclass[11pt,a4paper]{article}

\usepackage{amsmath}
\usepackage[T1]{fontenc}
\usepackage[portuguese]{babel}
\usepackage{amsfonts}
\usepackage{amssymb}
\usepackage{graphicx}
\usepackage{caption}
\usepackage{subcaption}
\usepackage{epstopdf}
\usepackage{float}
\usepackage{booktabs}
\usepackage{dcolumn}
\usepackage{hyperref}
\usepackage{color}
\usepackage{cite}
\usepackage{makeidx}


\usepackage[left=2cm,right=2cm,top=1.5cm,bottom=1.5cm]{geometry}

\author{Ademilson de Souza Maciel}
\title{\textbf{} \\  \bigskip \emph{GGplot} \\ \bigskip \emph{autoplot}}
\date{\today}


\begin{document}
\SweaveOpts{concordance=TRUE}

\maketitle

\bigskip






\begin{figure}[h!]
\begin{center}
<<teste, echo=F, fig=TRUE,eval=TRUE, results=tex, width=7.5,height=4.2, warning=FALSE, message=FALSE, size='footnotesize'>>=
library(forecast)
library(ggplot2)
library(ggthemes)
library(easyGgplot2)
library(xtable)
library(TStools)
library(png)
library(grid)
library(ggfortify)
library(stargazer)
setwd("C:/Users/Ademilson/Desktop/Curso - Análise Macro/Diversos")
servicos<-ts(read.csv2("vol_servicos.csv", header=T,sep=";",dec=","),start=c(2012,1),freq=12)[,-1]
vmensal_servicos<-round((servicos/lag(servicos,-1)-1)*100,1)
colnames(vmensal_servicos)<-c("BRASIL","PARANÁ")
autoplot(vmensal_servicos)+
  scale_color_manual(values=c("blue", "orange"))+
  geom_line(size=1)+
  xlab("")+ylab("% a.m.")+
  ggtitle("Índice de Volume de Serviços (mês anterior com ajuste sazonal)")+
  annotate("text", x = 2013, y = 7, label = "Acumulado no ano (igual período do ano anterior):\nBrasil: -4,4%\nParaná: 2,6%",
           hjust=0,color="red",fontface =3)+
  theme_economist()
@
\end{center}
\end{figure}



\end{document}
