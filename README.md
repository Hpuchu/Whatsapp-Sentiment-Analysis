# Whatsapp-Sentiment-Analysis

print(getwd())
setwd("C:/Users/Gaurav Arora/Documents")
library(syuzhet)
library(ggplot2)
library(tm)
library(wordcloud)
texts<-readLines("chat.txt")
print(texts)
sentiment
sentiment=get_nrc_sentiment(texts)
print(sentiment)
text=cbind(texts,sentiment)
Totalsentiment=data.frame(colSums(text[,c(2:11)]))
Totalsentiment
names(Totalsentiment)="count"
Totalsentiment=cbind("sentiment"=rownames(Totalsentiment),Totalsentiment)
rownames(Totalsentiment)=NULL
ggplot(data=Totalsentiment,aes(x=sentiment,y=count))+
  geom_bar(aes(fill=sentiment),stat="identity")+
  theme(legend.position="none")+xlab("sentiment")+ylab("sentiment")+ylab("Total Count")+ggtitle("Total sentiment Score")
