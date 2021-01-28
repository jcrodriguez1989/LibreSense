
# LibreSense

Sensory analysis application.

This is the first attempt at building open-source software for sensory
analysis. In this first step, we are trying to build an application for
Quantitative Descriptive Analysis (QDA).

We presented this project at LatinR 2018 in Buenos Aires, Argentina.

<http://47jaiio.sadio.org.ar/sites/default/files/LatinR_9.pdf> \[ES\]

<https://www.youtube.com/watch?v=DqrVVRA7riA&feature=youtu.be> \[ES\]

LibreSense contains two applications:

-   The application for capturing panelist data -`run_panel`- the leader
    of the sensory panel can modify the name and number of the samples
    and also the descriptors.
-   The results visualization application -`run_board`-.

In case you want to collaborate, check the issues.

## Installation

You can install the development version of `{libresense}` from
[GitHub](https://github.com/) with:

``` r
if (!require("remotes")) {
  install.packages("remotes")
}
remotes::install_github(
  "anibalacatania/LibreSense", subdir = "libresense", dependencies = TRUE
)
```

## Example

### Setting the Attributes to Evaluate

To set which attributes -and their type- to evaluate by the panelists,
this should be performed in a `csv` file, as exemplified in
[atributos.csv](atributos.csv).

    #>                Nombre Valores
    #> 1 Intensidad de color Numeric
    #> 2              Aromas    Text
    #> 3             Sabores    Text
    #> 4              Frutal Numeric
    #> 5              Floral Numeric
    #> 6            Herbáceo Numeric

This `csv` file should contain two columns:

-   Nombre: The names of the attribute to be evaluated.
-   Valores: The types of the attribute to be evaluated, must be one of
    `{"Numeric", "Text"}`

### Setting the Products to Evaluate

To set which products to evaluate by the panelists, this should be
performed in a `csv` file, as exemplified in
[productos.csv](productos.csv).

    #>       Copa
    #> 1 Herencia
    #> 2      Uno
    #> 3  Eredita
    #> 4    Nieto

This `csv` file should contain at least one column, the name of the
first column will be the name of the product to be evaluated, for
example `"Copa"`. The values of this first column, will be the products
to be evaluated. Additional columns will not be used by `{libresense}`,
but might be useful for the panel leader.

### Running the App

#### Running the Panel

Let’s assume we are using the two files presented above (download them
in the same folder as running the R session), to run the panel app, from
an R console type:

``` r
libresense::run_panel(
  products_file = "productos.csv",
  attributes_file = "atributos.csv",
  answers_dir = "Answers/"
)
```

#### Running the Board

Let’s assume we are using the two files presented above (download them
in the same folder as running the R session), to run the board app, from
an R console type:

``` r
libresense::run_board(answers_dir = "Answers/")
```
