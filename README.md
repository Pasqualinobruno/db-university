<!-- 
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.
Utilizzare https://www.diagrams.net/ per la creazione dello schema.
Esportare quindi il diagramma in png e caricarlo nella repo in un file html come visto a lezione.
 -->


 ### Dipartimenti
 - id INT AUTO_INCREMENT
 - Corso di laurea VARCHAR(100) NOT NULL

 ### Corsi di laure
 - id INT AUTO_INCREMENT
 - Materia VARCHAR(100) NOT NULL
 - Durata TINYNT
 - Sede TINYNT
 - Presidente VARCHAR(60) NOT NULL
 - Insegnante VARCHAR(60) NOT NULL

 ### Materie
 - id
 - Materia
 - Insegnante

 ### Insegnanti
 - id INT AUTO_INCREMENT
 - Nome VARCHAR(30) NOT NULL
 - Cognome VARCHAR(30) NOT NULL
 - Età TINYNT
 - Materia VARCHAR(100) NOT NULL

 ### Appelli di esame
 - id INT AUTO_INCREMENT
 - Materia VARCHAR(100) NOT NULL
 - Voto TINYNT NOT NULL
 - Data DATETIME NOT NULL
 - Insegnante VARCHAR(60) NOT NULL

 ### Studenti
 - id INT AUTO_INCREMENT
 - Nome VARCHAR(30) NOT NULL
 - Cognome VARCHAR(30) NOT NULL
 - Età TINYNT
 - Corso VARCHAR(100) NOT NULL
 - Data di inserimento DATE
 - Anno universitario TINYNT
 - Appello di esame DATETIME NOT NULL

 ### Esami conclusi
 - id INT AUTO_INCREMENT
 - Appello
 - Studente
