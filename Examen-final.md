Examen final
================

# importar la base de datos

``` r
library(readxl)
datos<- read_excel("D:/disco c/Documents/motosR.xlsx")
```

# TIPIFICACION O ESTANDARIZACION DE VARIABLES

``` r
datost<-datos

datost<-scale(datost, center = T, scale = T)
datost<-as.data.frame(datost)
```

# NORMALIDAD MULTIVARIANTE

H0: Normalidad Multivariante  
H1: No Normalidad multivariante  
Confianza=95%  
Alfa=5% = 0.05  
P value &gt; alfa no se rechaza la H0(Normalidad)  
P value &lt; alfa se rechaza la H0( No normalidad)

``` r
library(MVN)
```

    ## Registered S3 method overwritten by 'GGally':
    ##   method from   
    ##   +.gg   ggplot2

    ## sROC 0.1-2 loaded

``` r
mvn(datost[2:7])
```

    ## $multivariateNormality
    ##              Test         Statistic            p value Result
    ## 1 Mardia Skewness  83.0835982368508 0.0108644293609543     NO
    ## 2 Mardia Kurtosis 0.339569993261373  0.734180378625108    YES
    ## 3             MVN              <NA>               <NA>     NO
    ## 
    ## $univariateNormality
    ##           Test                   Variable Statistic   p value Normality
    ## 1 Shapiro-Wilk       Tipo de motor           0.6366  <0.001      NO    
    ## 2 Shapiro-Wilk        Pentencia Hp           0.9196  0.0262      NO    
    ## 3 Shapiro-Wilk      Cilindraje(C.C)          0.8180   1e-04      NO    
    ## 4 Shapiro-Wilk       Par motor (Nm)          0.9521  0.1926      YES   
    ## 5 Shapiro-Wilk    Velocidad max (Kmh)        0.9536   0.211      YES   
    ## 6 Shapiro-Wilk Precio   (Libra esterlina)    0.8328   3e-04      NO    
    ## 
    ## $Descriptives
    ##                             n          Mean Std.Dev      Median        Min
    ## Tipo de motor              30 -2.072380e-16       1  0.91969198 -1.0510765
    ## Pentencia Hp               30  1.619798e-17       1  0.00603799 -1.4301411
    ## Cilindraje(C.C)            30  1.179612e-16       1  0.07996228 -1.1390919
    ## Par motor (Nm)             30 -9.990200e-17       1  0.20484564 -1.7376561
    ## Velocidad max (Kmh)        30 -1.554240e-16       1 -0.11796712 -1.4733341
    ## Precio   (Libra esterlina) 30 -3.912163e-17       1 -0.35328833 -0.9904712
    ##                                 Max       25th      75th       Skew   Kurtosis
    ## Tipo de motor              0.919692 -1.0510765 0.9196920 -0.1270051 -2.0488690
    ## Pentencia Hp               2.710195 -0.6214817 0.4394794  0.9079486  0.6739137
    ## Cilindraje(C.C)            3.232238 -0.7741605 0.3481019  1.5211244  2.7457384
    ## Par motor (Nm)             1.829483 -0.8635303 0.5845164  0.1648813 -1.1131261
    ## Velocidad max (Kmh)        2.291574 -0.8747137 0.6613689  0.4136638 -0.8396717
    ## Precio   (Libra esterlina) 3.545874 -0.8028233 0.6557548  1.5323743  2.8045814
