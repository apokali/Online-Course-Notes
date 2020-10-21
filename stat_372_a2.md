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
#### (i)
```{r beta_hat_4}
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

#### (ii)
```{r}
mean(beta_hat_4)
```

#### (iii)
```{r}
sd(beta_hat_4)
```

#### (iv)
```{r}
X <- model.matrix(A1sim.lm) #yields the X matrix of the fitted model
XtXinv = solve(t(X)%*%X) #yields the (XtX)-1 matrix
beta_4 <- Beta[5]
beta_4
sd <- sqrt(15000^2*XtXinv[5,5])
sd
```
sample mean = 198679.5
sample standard deviation = 68703.77
From the distribution we have mean = 20000 and sd = 71351.91.
We can conclude that they are close.

### (b)
```{r}
#obtained from the data
beta_hat_2 = beta[3,]
beta_hat_3 = beta[4,]
cov(beta_hat_2, beta_hat_3)

#from the real dsitribution we have
15000^2*XtXinv[3,4]
```

