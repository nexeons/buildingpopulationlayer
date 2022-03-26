**Disclaimer**  
The Canadian Open Building Population Layer is a personal project by Maxim Fortin. It is not an official Government of Canada data source for building footprints or population.

**Introduction**  
This dataset contains population estimates at the building level for all provinces and territories in Canada, calibrated using the most accurate census information available. This data, along with accompanying code, can be downloaded and used freely under the MIT License, provided the source is acknowledged.

**Why this layer was developed**  
Population density products have long been used to quantify demographic information and to assess relationships with hazards, ecosystems, human health and infrastructure. However, there is currently a gap for a fine-resolution population density product covering all provinces and territories in Canada.

While proprietary datasets presenting this type of information already exist, they can be expensive. The public availability of remote sensing and free open-source data has significantly increased in recent years, making it now easier than ever to develop good population estimates all the way down to the building level in the public domain.

**Example**  
A possible use of the Canadian Open Building Population Layer is to assess the exposure of population to flood hazard as part of risk or priority setting assessments. Flood inundation extent layers are combined with a building population layer to evaluate how many people may potentially be exposed to a particular flooding event.

**Data sources for the layer**  
The Canadian Open Building Population Layer is calculated using two data sources:  

-	[Microsoft Canadian Building Footprints layer](https://github.com/microsoft/CanadianBuildingFootprints): 11,842,186 computer-generated building footprints developed by Microsoft, freely available for download and use under the Open Data Commons Open Database License (ODbL).  
-	2016 Canada Census: population distribution at the smallest available census geographical unit, in this case dissemination areas with 56,590 units distributed across Canada. Geospatial information for dissemination areas is derived from “[Population and dwelling counts, for dissemination areas, 2016 Census](https://open.canada.ca/data/en/dataset/3cf36302-1060-444e-988a-d97b6db5ad24)” and “[Dissemination Areas, Cartographic Boundary File – 2016 Census](https://open.canada.ca/data/en/dataset/2dd7fed4-4e0f-406c-ab96-c29b6a9116b1)”.

**Creation details**  
Building population is estimated in four stages:  

1.	Extract centroid points from building footprints
2.	Calculate the number of centroid points for each census dissemination area
3.	Calculate an average population per building for each dissemination area using 2016 census estimates
4.	Assign the average population back to each building depending on its location within the census dissemination areas

The calculation process is automated in Python. The main packages used are Geopandas for geospatial analysis, along with Pyogrio for fast dataframe reading and writing to file.

The code is available [here](https://github.com/nexeons/cobpl/blob/main/Building-Pop-PT.py) in a Github repository.

**Building population files**  
The following files are available for download in zipped geopackage format (EPSG:3978 coordinate reference system).  

| Province/Territory        | Number of Buildings | Zipped MB |
|---------------------------|:-------------------:|:---------:|
| [Alberta](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_AB.zip)                    |      1,777,439      |    153    |
| [British Columbia](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_BC.zip)           |      1,359,628      |    119    |
| [Manitoba](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_MB.zip)                   |       632,982       |     55    |
| [New Brunswick](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_NB.zip)              |       350,989       |     30    |
| [Newfoundland and Labrador](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_NFL.zip) |       255,568       |     21    |
| [Northwest Territories](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_NWT.zip)     |        13,161       |     1     |
| [Nova Scotia](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_NS.zip)                |       402,358       |     35    |
| [Nunavut](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_NU.zip)                    |        2,875        |     1     |
| [Ontario](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_ON.zip)                    |      3,781,847      |    334    |
| [Prince Edward Island](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_PEI.zip)      |        76,590       |     6     |
| [Quebec](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_QC.zip)                     |      2,495,801      |    221    |
| [Saskatchewan](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_SK.zip)               |       681,553       |     59    |
| [Yukon](https://cobpl.s3.us-east-2.amazonaws.com/COBPLv1_YK.zip)                      |        11,395       |     1     |

**Limitations and potential areas of improvement**  
The dataset provides an overview of the population density within a census dissemination area, averaged over the buildings located within that dissemination area.
The building population layer can be used for high-level assessments, but should not be used as a tool to try and directly assess the number of people living in specific building units.

No differentiation is made with regards to the type of building (residential, commercial, industrial, institutional, etc.). As such, population is distributed evenly across all buildings, including non-residential buildings. Additional information related to zoning and land use could be integrated in the future to account for that aspect. Some researchers also investigated the use of additional parameters in the population distribution, such as developing a relationship between the surface area of the building footprint and the population.  

**Use constraints and citation**  
The Canadian Open Building Population Layer has been produced by Maxim Fortin as open and free data. Reuse is authorised under the MIT License, provided the source is acknowledged.

How to cite this dataset:  
*FORTIN, Maxim (2022): Canadian Open Building Population Layer, derived from open-source computer-generated footprints and census data (version 1.0), URL: http://www.maximfortin.com/projects/cobpl/*

**MIT License**
Copyright 2022 Maxim Fortin

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
