# About scPagwas

**scPagwas** employing the polygenic regression model to uncover
trait-relevant cell subpopulations by incorporating pathway activity
transformed scRNA-seq data with genome-wide association studies (GWAS)
data.

``` r
knitr::include_graphics(here::here("img", "Figures_1.jpg"))
```

<img src="./img/Figures_1.jpg" width="80%" style="display: block; margin: auto;" />

The methodology and benchmarking performance are described in:

Polygenic regression identifies trait-relevant cell subpopulations
through pathway activity transformed single-cell RNA sequencing
data.(2022)

Code for reproducing the analysis from the paper is available
[here](https://github.com/dengchunyu/scPagwas_reproduce).

For further usage on the scPagwas package, please refer to the
[tutorials](https://dengchunyu.github.io/scPagwas/). A vignette for
using also can be accessed using browseVignettes(“scPagwas”)

## Installation

You can install the released version of scPagwas from
[github](https://github.com/dengchunyu/scPagwas) with:

``` r
#install some dependence packages
install.packages("SeuratObject")
install.packages("Seurat")
install.packages("ggpubr")
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("GenomicRanges")
BiocManager::install("IRanges")

devtools::install_github("dengchunyu/scPagwas",build_vignettes = TRUE)
```

## Usage

quick-start example:

``` r
 library(scPagwas)
 #library(Seurat)
 #1.start to run the wrapper functions for example.
 Pagwas_data<-scPagwas_main(Pagwas = NULL,
                     gwas_data =system.file("extdata", "GWAS_summ_example.txt", package = "scPagwas"), # The GWAS Summary statistics files 
                     Single_data =system.file("extdata", "scRNAexample.rds", package = "scPagwas"),# scRNA-seq data in seruat format with "RNA" assays and normalized.
                     output.prefix="test", # the prefix name for output files
                     output.dirs="scPagwastest_output",# the directory file's name for output
                     block_annotation = block_annotation,# gene position in chromosome is provided by package.
                     assay="RNA", # the assays for scRNA-seq data to use.
                     Pathway_list=Genes_by_pathway_kegg,# pathway list is provided by package, including gene symbols.
                     chrom_ld = chrom_ld,# The LD data is provided by package.
                     singlecell=T, # Whether to run the singlecell process.
                     celltype=T,# Whether to run the celltype process.
                     seruat_return=T,#Whether to return seruat format result.
                     ncores = 1 ) #The numbers of cores to run.
```

## Tutorials

scPagwas provides a number of tutorials for various situation. Please
also visit the documentation.

-   The
    [Data_input_preproccess_for_scPagwas](https://dengchunyu.github.io/scPagwas/articles/Data_input_preproccess_for_scPagwas.html)
    tutorial provides the methods of data-input preproccess for
    scPagwas.

-   The
    [Bmmc_monocytecount_singlecell_celltype_vignette](https://dengchunyu.github.io/scPagwas/articles/Bmmc_monocytecount_singlecell_celltype_vignette.html)
    tutorial provides the usual procedure for scPagwas including the
    result interpretation are discussed, and visualizing their
    characteristics.

-   The
    [Running_scPagwas_steps_by_SubFunctions](https://dengchunyu.github.io/scPagwas/articles/Running_scPagwas_steps_by_SubFunctions.html)
    tutorial provides the procedure for only cell types or single cell
    functions; Otherwise, a step by step introduction for scPgawas
    sub-functions are provided.

-   The
    [Multi_TraitFiles_for_one_SingleData_running](https://dengchunyu.github.io/scPagwas/articles/Multi_TraitFiles_for_one_SingleData_running.html)
    tutorial provides

-   The
    [Split_big_scRNAseqData_and_integrate_result](https://dengchunyu.github.io/scPagwas/articles/Split_big_scRNAseqData_and_integrate_result.html)
    tutorial provides
