# Dietro i dati: il ruolo dei metadati nella visibilità della conoscenza scientifica

## DOI

DOI del record su Zenodo

## Descrizione

Questo progetto consiste in un'**analisi esplorativa ed esplicativa di un dataset contenente dati bibliografici** relativi a pubblicazioni scientifiche di argomento biblioteconomico. 

L'obiettivo iniziale era osservare la distribuzione della produzione scientifica. Durante l'analisi, però, è emerso un secondo livello di lettura: la presenza stessa di un articolo nel dataset dipende anche dalla qualità dei suoi metadati. È facile pensare infatti che i dati siano una fotografia oggettiva del mondo, ma in realtà ogni dataset è anche il risultato di un processo fatto di selezione, descrizione e organizzazione dell'informazione.

Il progetto nasce proprio da questa domanda: **quanto la qualità dei metadati influenza ciò che possiamo osservare?** 

In un ambiente digitale, ciò che non è descritto correttamente rischia di diventare invisibile. Metadati completi e strutturati possono quindi svolgere un ruolo decisivo nel determinare la reperibilità di una pubblicazione all'interno di un sistema informativo.

**Il progetto si è trasformato quindi in una sorta di analisi dei dati sui dati: una meta analisi del dataset stesso, per capire non solo cosa vediamo, ma anche perché riusciamo a vederlo.**

## Contesto

Il progetto nasce come prova d'esame del corso di **Digital Humanities e Data Management per i Beni Culturali** per il corso di Laurea Magistrale in Scienze del Libro e del Documento dell'Alma Mater Studiorum Università di Bologna.

## Fonte dei dati

I **dati in input** sono costituiti da un file CSV scaricato dal repository GitHub del corso Digital Humanities e Data Management (https://raw.githubusercontent.com/dhdmch/2025-2026/refs/heads/main/data/lispod/data.csv).

| Variabile | Tipo |	Definizione | Esempio |
| :----- | :--- | :--------- | :------ |
|  id     |	str | URL Wikidata univoco | http://www.wikidata.org/entity/Q136384321	 |
|  titolo     |	str | Titolo del contributo | Un'idea di biblioteca, un'idea di professione	 |
|  autori     |	str | Autori del contributo e genere | Rosa Maiello (femmina), Lucia Sardo (femmina)	 |
|  data_pubblicazione     |	datetime | Data di pubblicazione del contributo | 2022	 |
|  argomenti     |	str | Tematiche principali del contributo, separate da ; | bibliografia; bibliotecario	 |
|  basi_dati     |	str | Basi dati in cui è indicizzato il contributo | Scopus; DOAJ	 |
|  doi_disponibili     |	str | DOI del contributo | 10.2426/AIBSTUDI-13398	 |
|  editori     |	str | Editori del contributo | Giornale di Sicilia Editoriale Poligrafica		 |
|  licenze_rivista     |	str | Licenza del contributo | Creative Commons Attribution-ShareAlike	 |
|  rivista     |	str | Rivista nella quale è stato pubblicato il contributo | Bibliothecae.it	 |
|  edizione     |	str | Fascicolo della rivista | 55	 |
|  volume     |	str | Annata della rivista | 23	 |
|  pagine     |	int | Numero di pagine | 19	 |

## Metodi e strumenti
Il progetto è stato sviluppato in un ambiente **Google Colab** utilizzando il linguaggio di programmazione **Python**. Lo strumento principale utilizzato per la manipolazione, l'analisi e la visualizzazione dei dati è la libreria Pandas.

Le operazioni includono:

* **Caricamento e ispezione dei dati** (pd.read_csv, df.info(), df.describe());
* **Bonifica e normalizzazione dei dati** (conversione delle date in tipo int, bonifica della colonna autori, individuazione dei DOI duplicati);
* **Arricchimento dei dati** della colonna autori attraverso l'interrogazione dell'**API di Wikidata**. Per i record privi di informazioni sugli autori è stato recuperato il valore della proprietà P2093 (author name string)
* **Analisi esplorativa** concentrata sull'analisi di compatibilità dei dati con due famose **leggi bibliometriche** (Lotka e Bradford) tramite aggregazioni (value_counts(), groupby()), ordinamenti .sort_index() e visualizzazioni tramite grafici a barre (plot.barh());
* **Analisi esplicativa** focalizzata sul calcolo di un **punteggio di completezza dei metadati** di ogni contributo scientifico, per dimostare che metadati completi e ben strutturati influenzano la visibilità dei dati della ricerca. In questa fase è stato analizzato il caso studio della **rivista Bibliothecae.it**.

## I risultati

L'analisi della distribuzione degli autori mostra un **andamento compatibile con la legge di Lotka**: la produzione scientifica è caratterizzata dalla presenza di molti autori occasionali e di un numero più limitato di autori maggiormente produttivi. La distribuzione degli articoli tra le riviste **conferma il principio alla base della legge di Bradford**.

L'analisi esplicativa evidenzia il ruolo della qualità descrittiva dei metadati nella rappresentazione della conoscenza scientifica. Il calcolo di un punteggio di completezza ha messo in luce che **i record associati alla rivista Bibliothecae.it si distinguono nettamente da quelli delle altre riviste presenti nel dataset**.
 
## Responsabili
- Meneguzzo, Anna - https://orcid.org/0009-0003-5356-1717

## Licenza
I dati di input e il codice di output (incluso in questo Notebook) sono rilasciati sotto licenza [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).
