# A Guide to Germany's Regional Data

This version: December 17, 2024. 
_Additions, comments and edits are very welcome!_


### Table of Contents 

1. Statistical Offices of the Länder
2. German census
3. Federal Office for Building and Regional Planning
4. Other Government Data Providers
5. Data about Cities 
6. Independent Data Collections 






### Statistical Offices of the Länder

Germany is a federal state with sixteen constituent states (Länder). Most regional data collection and dissemination is done by the statistical offices which maintain websites and web services to download regional data. The website [regionalstatistik.de](https://www.regionalstatistik.de/genesis/online/) provides access to a common pool of data made available by all statistical offices in a GENESIS database instance. A similar website, [bildungsmonitoring.de](https://www.bildungsmonitoring.de/bildung/online/), provides data related to education (Kinder- und Jugendhilfestatistik, Schulstatistik, Berufsbildungsstatistik und Hochschulstatistik). 

For both websites, users can query and download data through their browser or via an API. The R package [wiesbaden](https://sumtxt.github.io/wiesbaden/) is a client for to the API of a GENESIS database instances allowing users to load available data directly from a GENESIS database into R. The package and documentation as well as links to other clients are available at: [sumtxt.github.io/wiesbaden](https://sumtxt.github.io/wiesbaden/).

Many statistical offices have more data available than what is available through [regionalstatistik.de](https://www.regionalstatistik.de/genesis/online/) or [bildungsmonitoring.de](https://www.bildungsmonitoring.de/bildung/online/). The following statistical offices make their data available via a GENESIS database instance: 

* Bavaria: https://www.statistikdaten.bayern.de/genesis/online/ 
* North Rhine-Westphalia: https://www.landesdatenbank.nrw.de/ldbnrw/online/
* Saxony: https://www.statistik.sachsen.de/genonline/online
* Saxony-Anhalt: https://genesis.sachsen-anhalt.de/genesis/online/

Except for Saxony (which disabled the API access), users can use available GENESIS client software to retrieve data from these databases. 

The following statistical offices provide users with the option to query data through their own web services but do not provide any API access: 

* Berlin/Brandenburg: [Statistisches Informationssystem Berlin Brandenburg, StatIS-BBB](https://statis.statistik-berlin-brandenburg.de/webapi/) 
* Hesse: [Hessisches Statistisches Informationssystem, Datenbank Hesis](https://statistik.hessen.de/hesis)
* Baden-Württemberg: [Struktur- und Regionaldatenbank, SRDB](https://www.statistik-bw.de/SRDB/?E=GS) 
* Bremen: [Bremen Kleinräumig](https://www.statistik-bremen.de/soev/statwizard_step1.cfm) 
* Lower Saxony: [LSN-Online](https://www1.nls.niedersachsen.de/statistik/default.asp)
* Thuringia: [Tabellen des TLS](https://statistik.thueringen.de/datenbank/default2.asp) 
* Hamburg/Schleswig-Holstein (Statistikamt Nord): [Freie Datenauswahl für Hamburg](https://region.statistik-nord.de/compare/selection/2) and [Freie Datenauswahl für Schleswig-Holstein](https://region.statistik-nord.de/compare/selection/1)

The following statistical offices do not provide query tools but only publish regional data as reports or Excel tables: 

* Rhineland-Palatinate: https://www.statistik.rlp.de/de/regional/
* Saarland: https://www.saarland.de/stat/DE/themen/themen_node.html
* Mecklenburg-Vorpommern: https://www.laiv-mv.de/Statistik/Zahlen-und-Fakten/

Since the statistical offices tend to not publish all data online, it is often useful to contact them with specific data requests. There is a catalog of available data (PDF: [Regionalstatistischer Datenkatalog des Bundes und der Länder 2021](https://www.destatis.de/DE/Themen/Laender-Regionen/Regionales/Publikationen/Downloads/regiostatkatalog-2021.pdf?__blob=publicationFile)).

Available data on [regionalstatistik.de](https://www.regionalstatistik.de/genesis/online/) goes back as far as the mid-1990s, but some statistical offices provide longer time series. Another source of historic regional data are the publications of the statistical offices in Germany (and the German Reich). They are partially available as (scanned) PDFs through a digital library: [statistischebibliothek.de](https://www.statistischebibliothek.de/).

The statistical offices publish the [municipality directory](https://www.destatis.de/DE/Themen/Laender-Regionen/Regionales/Gemeindeverzeichnis/_inhalt.html) at least once each year (but recently every quarter and month). The directory provides basic information about each municipality (e.g., size, postal code) as well as how the municipality is related to higher-level administrative and statistical units. The directory also includes similar information for higher-level administrative units (e.g., districts). There are versions available as Excel files (since 1975) and fixed-width files (since 1993). The latter can be easily loaded in R using the function `read_gv100()` in the [wiesbaden](https://sumtxt.github.io/wiesbaden/) package.  The files in fixed-width format typically include more information. 


### German census

The German Census, known as "Zensus" in Germany, is a comprehensive statistical survey conducted periodically (so far: 2011 and 2022) to gather fundamental data about the population, households, and housing stock across the country. Based on EU law it is conducted decennially and included around 10 million people in Germany in the past. A particularly valuable aspect of these censuses is the availability of data at a highly granular, grid-level resolution, offering insights beyond traditional administrative boundaries. Data is available at a 100m² and 1km² resolution as well as 10km² in 2022. This standardized spatial reference facilitates consistent comparisons across different regions and over time. The primary data source for these grid-level statistics is the Federal Statistical Office of Germany (Statistisches Bundesamt) and the statistical offices of the Länder. The data can be explored and loaded using the [z22](https://jslth.github.io/z22) R package. It is also available in a non-processed format [here](https://www.zensus2022.de/EN/Census_results/_inhalt.html).



### Federal Office for Building and Regional Planning

The Federal Office for Building and Regional Planning (Bundesinstitut für Bau-, Stadt- und Raumforschung , BBSR) mains the database [INKAR](https://www.inkar.de/) ("Indikatoren und Karten zur Raum- und Stadtentwicklung“) with regional data going back to the mid-1990s. The data can be queried using the R package [bonn](https://github.com/sumtxt/bonn). The data comes from the statistical offices and other data providers. 

A major advantage of the INKAR database is that data is spatially harmonized. Changes over time in administrative boundaries are handled by combining the affected geographic units to create larger, temporally stable units comprised of two or more districts. There is only some public documentation on this harmonization, but see: 

* Milbert, A. (2010). [Gebietsreformen - politische Entscheidungen und Folgen für die Statistik](https://www.bbsr.bund.de/BBSR/DE/veroeffentlichungen/berichte-kompakt/2010/DL_6_2010.pdf?__blob=publicationFile&v=2). *BBSR-Berichte kompakt*. Hrsg. Bundesinsitut für Bau-, Stadt-und Raumfoschung. Bonn, 6/2010. 

The BBSR crosswalks form the backbon of the R package [ags](https://sumtxt.github.io/ags/) which helps to construct geography-harmonized time series of statistics not included in the INKAR database. 

The predessor of the INKAR database is a series of reports published by BBSR presenting district data across Germany: 

* Gatzweiler, Hans-Peter and Runge, Ludwig. 1984. Aktuelle Daten zur Entwicklung der Städte, Kreise und Gemeinden 1984. Laufende Raumbeobachtung. Bundesforschungsanstalt für Landeskunde und Raumordnung. [Table of Contents](./files/TOC/Aktuelle_Daten_zur_Entwicklung_der_Städte_Kreise_und_Gemeinden_1984.pdf)
* Bundesforschungsanstalt für Landeskunde und Raumordnung (Hg.) 1992. Materialien zur Raumentwicklung. Laufende Raumbeobachtung. Aktuelle Daten zur Entwicklung der Städte, Kreise und Gemeinden: 1989/90. Heft 47, Bonn. [Table of Contents](./files/TOC/Aktuelle_Daten_zur_Entwicklung_der_Städte_Kreise_und_Gemeinden_1989-90.pdf)
* Bundesforschungsanstalt für Landeskunde und Raumordnung (Hg.) 1995. Materialien zur Raumentwicklung. Laufende Raumbeobachtung. Aktuelle Daten zur Entwicklung der Städte, Kreise und Gemeinden 1992/93. Heft 67, Bonn. [Table of Contents]
* Bundesamtes für Bauwesen und Raumordnung (Hg.) 1998. Aktuelle Daten zur Entwicklung der Städte, Kreis und Gemeinden. Ausgabe 1998. Band 1, Bonn. [Table of Contents](./files/TOC/Aktuelle_Daten_zur_Entwicklung_der_Städte_Kreise_und_Gemeinden_Ausgabe_1998.pdf)
* Bundesamtes für Bauwesen und Raumordnung (Hg.) 1999.  Aktuelle Daten zur Entwicklung der Städte, Kreise und Gemeinden. Ausgabe 1999. Band 3, Bonn. [Table of Contents]

Copies of these reports are available in many university libraries, including for the library of the Humbolt University (HU Bibliothek, ZwB Naturwissenschaften in Adlershof). 

 


### Other Government Data Providers 

* The Federal Criminal Police Office provides regional data on crime in their annual reports: [Polizeiliche Kriminalstatistik (PKS)](https://www.bka.de/DE/AktuelleInformationen/StatistikenLagebilder/PolizeilicheKriminalstatistik/pks_node.html)

* The Federal Agency for Cartography and Geodesy (BKG) provides geodata, inkl. shapefiles for administrative units ([Verwaltungsgebiete](https://gdz.bkg.bund.de/index.php/default/digitale-geodaten/verwaltungsgebiete.html)) such as districts and municipalities

* The Deutscher Wetterdienst (DWD) provides data on the weather for geo-referenced weather stations or gridded data. The data can be queried through the [Climate Data Center Portal](https://cdc.dwd.de/portal/) or downloaded in bulk from an [FTP](https://opendata.dwd.de/climate_environment/CDC/) server. 

* Federal election results for all parties/candidates and down to the electoral ward is available from the [Federal Returning Officer (Bundeswahlleiter)](https://www.bundeswahlleiter.de/). The statistical offices typically only publish data for the major parties and aggregate to the municipality or district level. 

  

### Data about Cities 

Most major cities form their own district (these districts are called Stadtkreise). A little over a quarter of all districts are cities. Data on these cities is readily available from the above data sources. In addition there are a few other data providers: 

- Eurostat, the statistical office of the European Union, maintains the [City Database](https://ec.europa.eu/eurostat/web/cities/data/database) which includes data from about 125 cities in Germany. These cities include major cities that form their own district (Stadtkreise) but also a few smaller cities. 
- Many cities make neighorhood data available through their open data portals or the website of the local statistical office. Example from Cologne: [Offene Daten Köln](https://www.offenedaten-koeln.de/), [Geoportal Köln](https://www.stadt-koeln.de/politik-und-verwaltung/geoportal/) and [Statistikatlas Köln](https://www.stadt-koeln.de/politik-und-verwaltung/statistik/statistikatlas-koeln) 
- The Association of German Cities (Deutscher Städtetag) used to compile the annual Statistical Yearbook of German Municipalities (Statistisches Jahrbuch Deutscher Gemeinden) providing data on the largest municipalities. The last yearbook was published in 2013. Scans for all editions are available from the TU Braunschweig: https://doi.org/10.24355/dbbs.084-202112171650-0



### Independent Data Collections 

- [Property price indices](https://github.com/Ahlfeldt/AHS2023-toolkit) by postcodes computed from listenings on Immoscout24 in [Ahlfeldt, Heblich, Seidel (2023)](https://www.sciencedirect.com/science/article/pii/S0166046222000746?via%3Dihub). The underlying micro-data and detailed 1km² raster level is available from the [RWI FDZ](https://www.rwi-essen.de/en/research-advice/further/research-data-center-ruhr-fdz/data-sets/rwi-geo-red/x-real-estate-data-and-price-indices). Socio-economic 1km² raster level data based on various sources by the microm Mikromarketing und Consult GmbH is also available from the [RWI FDZ](https://www.rwi-essen.de/en/research-advice/further/research-data-center-ruhr-fdz/data-sets/translate-to-english-rwi-geo-grid-socio-economic-data-on-grid-level). 
- Number of (registered) weapons by district in 2013 and 2019 collected by the newspaper DIE ZEIT. [Newspaper article "Waffen in Deutschland"](https://www.zeit.de/news/2021-02/23/private-schusswaffen-in-deutschland-am-wenigsten-in-berlin) and [Data (2019)](https://docs.google.com/spreadsheets/d/1wmiZJ8Akc9nUC8x6QL_AX0PnEYcPAjtMh9sFsyL3Fxs/edit#gid=0); [Newspaper article: "Waffenland Deutschland"](https://www.zeit.de/2014/04/waffen-deutschland) and [Data (2013)](https://www.zeit.de/gesellschaft/waffen/assets/krs-schusswaffen.csv)

