
# Research Group Analitycs Dashboard

Software for the analysis and bibliometric visualization of the scientific production of research groups in the Department of Cauca.

It has the following main features:
- Extracts data of researchers and research groups from CvLAC, GrupLAC and Scopus platforms, in bulk or on demand.
- Search and elimination of duplicate documents.
- Data preprocessing.
- Data matching between GrupLAC and Scopus.
- Different data visualization graphics.
- Collaboration networks.
- Graphical user interfaces.

Instructional video: https://youtu.be/tdp8FPcWMco

---

## Installation
> [!IMPORTANT]
> ***For the tool to work, it is mandatory to have the database manager installed. [PostgreSQL.](https://www.postgresql.org/download/)*** *If you want to use a graphical tool to manage PostgreSQL it is recommended to install [PgAdmin 4.](https://www.pgadmin.org/download/)*

To install the project, perform a clone of the latest version of the repository by running the following command git:
```bash
    git clone https://github.com/JarbyDaniel/ResearchGroupsDashboard.git
```
Inside the generated folder, run the following command to install the necessary libraries:

```bash
    pip install -r requierements.txt
```

---

## Content
- Database for CvLAC, GrupLAC and Scopus.
- GrupLAC and CvLAC data extractor.
- Scopus data extractor.
- Dashboard (Analysis board).

## Database for CvLAC, GrupLAC and Scopus.

The files generated in the extraction of data used in the dashboard are stored in the directory `dashboard/assets/data/`.


In addition, the databases of the information massively extracted for the Department of Cauca in Cvlac, GrupLAC and Scopus are available in the following directory `BD/`.

## GrupLAC and CvLAC data extractor.

This tool extracts data from the CvLAC and GrupLAC applications belonging to the Scienti system in Colombia. To use this tool, it is required to enter the link of the CvLAC or GrupLAC of interest and the platform will extract the public information available in the system.
It is recommended that any person using this tool carefully read the [privacy policy and terms of use](https://minciencias.gov.co/ciudadano/terminosycondiciones-datospersonales) defined by MinCiencias, which establishes guidelines and standards for the ethical use of data.

## Scopus data extractor.

This tool extracts data from the Scopus platform. This requires the registration of an Apikey provided by Scopus and a token endorsed by the institution.

## Dashboard

A section called "Explore data" is integrated with the objective of inspecting the data previously obtained and preprocessed by means of the extraction systems, additionally two sections are integrated for the analysis and visualization of the data coming from GrupLAC and Scopus. The dashboard is developed within the framework of the degree work entitled "Dashboard for bibliometric analysis and visualization within the scope of research groups in the department of Cauca" developed at the University of Cauca by students Jarby Daniel Salazar Galindez and Edison Alexander Mosquera Perdomo. The dashboard seeks to be an assistant for the actors of the Regional System of Science, Technology and Innovation of Cauca.

---

## Instructions for running the project

To extract data from CvLAC, Gruplac and Scopus in bulk (use for administrators), run the following command:

```bash
    python main.py    
```
After the extraction, the data preprocessing is executed with the following command:

```bash
    python preprocessing.py
```
To extract CvLAC, Gruplac and Scopus data on demand (with user interface), follow the steps below:

To run the CvLAC and Gruplac extractor user interface:
```bash
  python interface_extractor_scienti.py
```
Open the following link in the browser: `127.0.0.1:5006`.

To run the Scopus extractor user interface:
```bash
  python interface_extractor_scopus.py
```
Open the following link in the browser: `127.0.0.1:5005`.

To run the dashboard run the following command:
```bash
  python dashboard/index.py
```
Open the following link in the browser: `localhost:8051`.

---

To verify the consistency between the extracted data and the data registered in the CvLAC and GrupLAC platforms, run the following command :

```bash
  python testing_main.py
```
Note that the verification is done with respect to the CSV files that you must generate manually, for this replace and follow the structure of the files for [CvLAC](cvlac/testing/testing_cvlac)  and [GrupLAC.](cvlac/testing/testing_gruplac)

---

> [!NOTE]
> To expand the use of the project to other departments of Colombia, use the [search for groups by department](https://scienti.minciencias.gov.co/ciencia-war/BusquedaGrupoXDepartamento.do) of Minciencias to choose the department of interest and replace the url used in line 83 of main.py file

Example used for the Department of Cauca:
```python
[83] lista_gruplac=Extractor.get_gruplac_list('https://scienti.minciencias.gov.co/ciencia-war/busquedaGrupoXDepartamentoGrupo.do?codInst=&sglPais=COL&sgDepartamento=CA&maxRows=15&grupos_tr_=true&grupos_p_=1&grupos_mr_=130')    
```
---

> [!WARNING]
>*Due to the large volume of data used, to avoid cache problems it is recommended to deploy the project from a private browser.*

---

## Authors

- [Jarby Daniel Salazar Galindez](https://www.github.com/jarbydaniel)
- [Edison Alexander Mosquera Perdomo](https://www.github.com/alexper11)

## License

[MIT](https://choosealicense.com/licenses/mit/)
