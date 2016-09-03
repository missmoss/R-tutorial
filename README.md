# 給初學者的 R 入門碎碎念
過去的學習經驗發現，學會基本指令後，直接找個題目實作，進步的速度會比跟著教學慢慢爬快多了，雖然痛苦指數會稍微高一點，不過收穫也相對多很多喔。
## 安裝
首先請先安裝以下軟體：
- [R](https://www.r-project.org/)
- [RStudio](https://www.rstudio.com/products/rstudio/download3/)

RStudio 是一個 IDE，提供圖形化介面，幫助我們更輕鬆地操作 R。
## 開始
在這裡會先很快的帶過會常常用到的函數們。

首先載入內建資料集 iris 鳶尾花

    # 我是柱姐，不對，註解
    data(iris)
接著看一下 data 的概述

    # 方法1：看資料型態
    str(iris)
    # 方法2：看數值欄位的資料分佈
    summary(iris)

也可以用各種方法看一下資料

    # 資料的頭
    head(iris)
    # 資料的尾巴
    tail(iris)
    # 資料某個欄位的的平均數、中位數、變異數
    mean(iris$Sepal.Length)
    median(iris$Petal.Length)
    var(iris$Petal.Length)

等等，中間 ````$```` 是做什麼的？！````$```` 用來表示我們要呼喚資料表（Data Frame）裡面的某一個欄位（Column），用法是 ````資料表$欄位名````。

### 畫個圖吧
同時我們也可以利用 R 內建的畫圖模組來看一下資料的長相，雖然有點醜，但是看分布快又有效(?)。

    # 散佈圖
    plot(iris$Sepal.Length, iris$Sepal.Width)
    # 長條圖
    plot(iris$Species)
    # 盒狀圖
    plot(iris$Species, iris$Sepal.Length)
    # 散佈圖矩陣
    plot(iris)

要一直打 ````iris$```` 好像有點煩QQ 讓我們偷懶一下，使用 ````attach()```` 先將 ````iris```` 設為我們的預設(?)資料表，這樣就不用一直重複打字了歐耶！

    attach(iris)
    # 散佈圖
    plot(Sepal.Length, Sepal.Width)
    # 長條圖
    plot(Species)
    # 盒狀圖
    plot(Species, Sepal.Length)
    # 散佈圖矩陣
    plot(iris)
    # 用完之後要記得 detach
    detach()
    
### 跑個回歸～
回歸的函數叫 ````lm````，用法是 ````lm(y~x)````

    lm1 = lm(Sepal.Length~Sepal.Width)
    
看一下我們的模型：

    lm1

好像資訊沒有很多，用 ````summary```` 來看看：

    summary(lm1)
    
同時我們也可以一次放入很多變項：

    lm3 = lm(Sepal.Length~Sepal.Width+Petal.Length+Petal.Width)

### 我講完惹！
基礎大概就這樣柳，現在大家一起找個題目來做做看吧！
#### 以下是指令小筆記
    train = read.csv("train.csv", stringsAsFactors=FALSE)
    cbind()
    rbind()
    library("dplyr")
    arrange(data, Sepal.Length)
    
