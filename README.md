# MAC6967-G6-NLP-juridico

Members:  
Fabio Yukio  
Pedro Almeida  
Ricardo Tanaka  
Thomas Ferraz  
Verena Saeta  

Stay tuned: this file has been updated throughout the project.

## Abstract

The main proposal of this project is to create an algorithm capable of extracting information from the records of a lawsuit in order to obtain knowledge and outcomes such as:
- Factors unrelated to the characteristics of the process that can affect judges' decisions:
  - Ethnic, racial and gender prejudices;
  - Judge's experience;
  - Judge's political opinions;
  - Judge' personal sports preferences;
  - Other bias.
- How to map the factors that may affect the outcome of the merit of the case and obtain a measure of impartiality from the Judiciary;
- Analysis of the existence of variance in decisions as a measure of legal uncertainty;
- Locate biases and preference that have consequences on the real world.

### Steps

1. ~~Get samples of lawsuit records~~;
2. ~~Extract administrative data from these procedures~~;
3. ~~Download the PDFs of the files of these procedures~~;
4. ~~Identify who attached each document to the procedure file~~;
5. ~~If the document was attached by a lawyer, identify which party is represented by this lawyer~~;
6. ~~Identify which of the documents are judicial sentences~~;
7. Identify which document(s) each decision quotes;
8. Identify (where possible) what is being decided;
9. Identify who is being affected by the judgment;
10. Define for each party of the lawsuit, whether each decision is favorable, unfavorable or neutral [-1, +1].

### Inputs  
- Structured data on the process, extracted from the São Paulo State Court of Justice (TJSP) system:
  1. Name of the judge;
  2. Names of the lawyers;
  3. Names of the parties to the proceedings;
  4. (...)
  
- PDFs of the case files:
  1. Petitions;
  2. Judicial decisions;
  3. (...)
  
### Outputs
- For each judicial decision in each case:
  1. Identify which parties the judgment refers to;
  2. Identify whether the decision is favorable or unfavorable to each of these parties;
  3. Identify the articles and laws that are cited in the decision;
  4. Identify the subject of the decision.

## Data

In this project we will work with data from lawsuits of the São Paulo Court of Justice (TJSP). All documents and various information from each proceeding that is currently being processed at the TJSP can be accessed through the court's electronic system, the [e-Saj](https://esaj.tjsp.jus.br/). 
Basic process information can be accessed by anyone, through the website [procedural consultation](https://esaj.tjsp.jus.br/cpopg/open.do), as long as you have the case number. In order to have access to [the complete file of the case](https://pt.wikipedia.org/wiki/Autos_processuais), containing all its documents, it is necessary to have attorney credentials and to authenticate on the website before accessing the procedural consultation page. 

The raw data for this project refer to bankruptcy and judicial recovery lawsuits. This data was collected using a list of all bankruptcy and judicial recovery proceedings initiated between 2008 and 2017, sent in early 2018 by the TJSP. From this list and the credentials of a lawyer collaborating on the project, an algorithm was created using [Selenium Library](https://robotframework.org/SeleniumLibrary/SeleniumLibrary.html) to access the e-Saj; perform authentication; extract the basic information of each case such as court, district, name of the judge, name of the parties, qualified lawyers, etc. (see Dataset 1); and download the PDF files of the case file (see Dataset 2).

### Dataset 1 - Proceedings Administrative Data

Each judicial process has a HTML page generated by the TJSP system, containing the main information of the process. The figure below shows an example, for the number process **1037133-31.2015.8.26.0100**.

Figure 1: A bankruptcy lawsuit page on e-Saj
![Figure 1](assets/fig1.png)

For each bankruptcy or judicial recovery number sent by the TJSP, the page corresponding to that case number was scrapped on the Court's website. The collected information was saved in .rds files. These .rds files are in the dataset1 folder in Google Drive.

### Dataset 2 - The file entire content of each procedure 
The previous figure refers to a 2015 lawsuit. The legal proceedings from 2013 onwards are digital (or electronic) cases, and their pages on the TJSP website contain the link that allows access to the full file of proceedings, in PDF format:

![Figure 2](assets/fig2.png)

Ao clicar neste link, uma nova janela se abre, com todas as páginas dos autos do processo em formato PDF.

Figure 3: Filings of a bankruptcy lawsuit in e-Saj
![Figure 3](assets/fig3.png)

Note that this process alone has more than 68 thousand pages in PDF. The page that is open is a judicial decision. All of these PDFs have been downloaded and they are on a public Dropbox link.