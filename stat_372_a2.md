---
title: "STAT 373 A2"
output: pdf_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Question 1
A1_variates=read.table("A1_variates.txt",header=T) 
attach(A1_variates)
set.seed(20763179)

### (a)
```{r beta_hat_4, echo=false}
epsilon <- rnorm(24, 0, 15000)
Beta <- c(-250000,50,-200,12000,200000) 
X <- as.matrix(cbind(rep(1,4),A1_variates)) 
y <- X%*%Beta + epsilon

beta = array(0,c(5,1000)) #creates an array to store sets of estimators

for (i in 1:1000){
  y<-X%*%Beta+rnorm(24,0,15000) #X and Beta as defined in 2a) of A1
  A1sim.lm<-lm(y~size+age+employees+col)
  beta[,i]<-coef(A1sim.lm) #yields the estimates for each iteration
}
#the resulting (5 x 1000) matrix contains the beta estimates for the 1000 repetitions. 

beta_hat_4 <- beta[5,]
hist(beta_hat_4)
```


