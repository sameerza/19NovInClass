    #trying plotting using data published from our lab (Brown Lab) (Stokes et. al. 2017)

    data.stokes <- read.csv("book1.csv")

    head(data.stokes)

    ##                       Compound    R1    R2
    ## 1                   ARTEMETHER 0.001 0.001
    ## 2                CHLOROXYLENOL 0.000 0.001
    ## 3     DESVENLAFAXINE SUCCINATE 0.001 0.001
    ## 4 CHLORPHENIRAMINE (S) MALEATE 0.000 0.001
    ## 5                CYCLAMIC ACID 0.000 0.000
    ## 6               CHLORPROMAZINE 0.001 0.001

    str(data.stokes)

    ## 'data.frame':    1440 obs. of  3 variables:
    ##  $ Compound: Factor w/ 1440 levels "2-THIOURACIL",..: 112 313 432 314 386 315 1212 316 819 319 ...
    ##  $ R1      : num  0.001 0 0.001 0 0 0.001 0.001 0.001 0.001 0.006 ...
    ##  $ R2      : num  0.001 0.001 0.001 0.001 0 0.001 0.001 0 0.001 0.001 ...

    # plotting data, making hits red, adding text to the hits to label them using the Compound variable


    plot(data.stokes$R1,data.stokes$R2,
         pch = 20, # symbol
         cex = 1.2, # size of symbol
         col = "black", # symbol colour
         xlim = c(0, 0.5),
         ylim = c(0, 0.5),
         xlab = "Optical Density Replicate 2",
         ylab = "Optical Density Replicate 1",
         main = "Screening 1440 Compounds for Growth Rescue",
         bty="n")
    indexgrowth <- which(data.stokes$R1 > 0.05)

    points(data.stokes$R1[indexgrowth], data.stokes$R2[indexgrowth], col = "red", pch = 20, cex = 1.2)

    text(
      data.stokes$R1[indexgrowth], 
      data.stokes$R2[indexgrowth], 
      data.stokes$Compound[indexgrowth], 
      adj = -0.2,
      cex = 0.5,
      font = 4)

![](Untitled_files/figure-markdown_strict/unnamed-chunk-1-1.png)
