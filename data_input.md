
# Data needed to reproduce the code

This document provides the data sources used to run the provided code. 
As it's main aim is to provide a workflow for future applications, it also and mainly explains requirements for the input data. 

The code is designed to take all input files from an `input` folder in the project directory. 
With the repository also test data is provided for the region of Aachen (planning region), which allows for the analysis of the accessibility of vacant lots. 


## Regions

* Polygon layer with a field containing a region name indicating the regions to be analysed. This can be municipalities with the shared field that the layer will be grouped by. This can also be a layer with 1 polygon per region and the grouping step can be skipped.
  * Provide the name of the region field as parameter `region`
* Choose an appropriate buffer around this region for the `umkreis` parameter so population outside the area also gets included in calculating the accessibility of locations near the borders.

* Source: [BKG, 2023: Verwaltungsgebiete 1:5 000 000, Stand 01.01. (VG5000 01.01.)](https://gdz.bkg.bund.de/index.php/default/verwaltungsgebiete-1-5-000-000-stand-01-01-vg5000-01-01.html)
© BKG (2023) dl-de/by-2-0, Datenquellen: https://sgx.geodatenzentrum.de/web_public/gdz/datenquellen/Datenquellen_vg_nuts.pdf

## Population data

As input for script 01:

* Polygon, point or raster layer with population per grid cell.
* Provide name of field containing population information as parameter `ew_field`.
* Source: Output from script 00.

Script 00 provides a pre-processing option to create a point layer from a census csv file with coordinate columns. 

* Source:  [Statistische Ämter des Bundes und der Länder, 2024: Ergebnisse des Zensus 2022. Bevölkerungszahlen in Gitterzellen.](https://www.destatis.de/DE/Themen/Gesellschaft-Umwelt/Bevoelkerung/Zensus2022/_inhalt.html#sprg1403932)

## Urban structures

* Polygon layer with Urban structures of interest. Here: Vacant lots.
* The workflow creates a point grid with centrality values and in the last step the point values can be assigned to each features of this layer.

* Source: Vacant lot structures extracted using approach by [Ehrhardt et al. (2023)](https://doi.org/10.5334/bc.295) using data from [ALKIS, 2021, accessed via OpenGeodata.NRW](https://www.opengeodata.nrw.de/produkte/geobasis/lk/hist/hist_gru_xml/2021/)
