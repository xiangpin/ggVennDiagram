`ggVennDiagram` 尝试使用符合 ggplot 的语法绘制韦恩图。

安装软件包。

``` r
devtools::install_github("gaospecial/ggVennDiagram")
```

目前仅支持 4 sets 韦恩图。参考下面的例子：

``` r
library(ggVennDiagram)
genes <- paste("gene",1:1000,sep="")
set.seed(20190708)
x <- list(A=sample(genes,300),B=sample(genes,525),C=sample(genes,440),D=sample(genes,350))
ggVennDiagram(x)
```

![](README_files/figure-markdown_github/unnamed-chunk-2-1.png)

`ggVennDiagram` 返回一个 `ggplot` 对象。这个对象是可以使用 `ggplot`
的语法修改的。

``` r
library(ggplot2)
ggVennDiagram(x) + scale_fill_gradient(low="white",high = "red")
```

![](README_files/figure-markdown_github/unnamed-chunk-3-1.png)

`ggVennDiagram` 当前仅包含少数几个参数。

-   label：设置是否显示数据标签。
-   n.sides：相当于设置椭圆的分辨率，值越大，椭圆越平滑。

``` r
ggVennDiagram(x,label="count") + scale_fill_gradient(low="white",high = "red")
```

![](README_files/figure-markdown_github/unnamed-chunk-4-1.png)

不过，椭圆的线型、颜色等也可以使用 `ggplot` 通用方法设定（作用于 polygon
图层）。

``` r
ggVennDiagram(x,label="count",lty="dashed",color="grey") + scale_fill_gradient(low="white",high = "red")
```

![](README_files/figure-markdown_github/unnamed-chunk-5-1.png)

致谢
====

-   `VennDiagram`(<a href="https://github.com/cran/VennDiagram" class="uri">https://github.com/cran/VennDiagram</a>)
-   `sf`(<a href="https://github.com/r-spatial/sf" class="uri">https://github.com/r-spatial/sf</a>)
-   `ggtree`(<a href="https://github.com/GuangchuangYu/ggtree" class="uri">https://github.com/GuangchuangYu/ggtree</a>)
-   FigureYa112venn（作者：李誉辉<四川大学在读研究生>；出品：小丫画图<微信 epigenomics>）
