---
title: "STAT 373 A2"
author: Xuntian Lin, 20763179
data: October 20, 2020
output: pdf_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## Question 1
```{r}
A1_variates=read.table("A1_variates.txt",header=T)
attach(A1_variates)
set.seed(20763179)
```

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
sample mean = 201651.2 sample standard deviation = 72489.42

From the distribution we have mean = 20000 and sd = 71351.91.We can conclude that they are close.

### (b)
```{r}
#obtained from the data
beta_hat_2 = beta[3,]
beta_hat_3 = beta[4,]
cov(beta_hat_2, beta_hat_3)

#from the real dsitribution we have
15000^2*XtXinv[3,4]
```
We can conclude that the difference between the real covariance and the theoretical covariace is relatively lagre.


## Question 2
```{r}
set.seed(20763179)
ceocomp=read.csv("ceocomp.csv",header=T)
my.dat = ceocomp[sample(nrow(ceocomp),75),]
```

### (a)
```{r}
plot(ceocomp)
```

* CEOs who are 50-70 tend to make more compensation than others.

* CEOs' education, background type, number of years employed, number of years as CEO, sales revenue do not make a large difference in compensation.

* CEOs with lower market value and lower percentage of firm's market value tend to have higher compensation.

* CEOs with profits of the firm of 500 make higher compensation than others.

### (b)
```{r}
ceocomp_new <- subset(my.dat, PROF>=0)
ceocomp_new.lm<-lm(COMP~AGE+EDUCATN+as.factor(BACKGRD)
                   +TENURE+EXPER+SALES+VAL+PCNTOWN+PROF, data=ceocomp_new)
summary(ceocomp_new.lm)

```
Based on the output, we can conclude that for the overall model, the R-square value of 0.6799 tells us 
that over 67% of the variation in compensation is explained by the remaining variavtes.

* The most insignificant factors are age, sales, and prof as their estimates are close to 0.

* Some strong factors include education, backgronds, number of years employed from the firm,
number of years as the frim CEO, market value of the CEO's stock.

### (c)
Based on the output above,after accounting for age, education, all backgrounds, tenure, exper, sales, val, pcntown,
prof factors, we are given a estimate of $\hat \beta_2=-64.46138$, this tells us that CEOs with background wih sales/marketing had a estimated 64.46 thounds of dollars lower change in mean compensation than CEOs with banking/financial background.

### (d)
Since the $p$-values for every background is higher than 0.05, so we can conlude that background has no significant 
impact on CEOs compensation since we do not reject null hypothesis.

### (e)
#### (i)
There might be strong linear correlations between compensation and the three explanatory variables (e.g. age, tenure and experience), and thus these variables might exhibit multicollinearity.

Multicollinearity leads to inflated (i.e. increased ) variance of the associated parameter estimators, and correspondingly, inflated standard errors. This in turn leads to wide confidence interval and inaccurate concludes from
hypothesis test, due to inflated $p$-values.

### (ii)
From the scatterplot, it does not reveal strong linear among some of the explanatory variables(e.g. age, tenure and experience). 

#### (iii)
By removeing the age variate
```{r}
ceocomp_new.age.lm <- lm(COMP~EDUCATN+as.factor(BACKGRD)
                         +TENURE+EXPER+SALES+VAL+PCNTOWN+PROF, data=ceocomp_new)
summary(ceocomp_new.age.lm)

```
VIF = $\dfrac{1}{1-0.6796}=3.121098$. Since the VIF is relatively small (< 5), we would say that multicollinearity is not a problem with age variable.


### (f)
```{r}
new_x = data.frame(AGE=65, EDUCATN=1, BACKGRD="2", TENURE=22, 
                   EXPER=8, SALES=3250, VAL=8.2, PCNTOWN=2, PROF=112)
predict(ceocomp_new.lm, new_x, interval='prediction', level=.95)
```
According to the output, 1.2 million is in the 95% confidence interval that we obtained, then we can conclude that 
this 1.2 million is consistent.

### (e)
```{r}
SS_Res = 542.4^2*45 #sigma^2*df
SS_Tot = SS_Res/(1-0.6799) #SS(Res)/(1-R^2)
SS_Reg = SS_Tot - SS_Res
MS_Reg = SS_Reg/12
MS_Res = SS_Res/45
F_stat = MS_Reg/MS_Res
F_stat

p_val = 1-pf(F_stat, 12, 45)
p_val

```
According to the output from part(b), the test statistics and $p$-value is the same.
