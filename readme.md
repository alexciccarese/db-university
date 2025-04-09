## University

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## Table names: `Departments`
**columns**

- id (BIGINT) - primary key - auto_increment - NOT NULL
- name (VARCHAR(100)) - NOT NULL


## Table names: `Degree courses`
**columns**

- id (BIGINT) - primary key - auto_increment - NOT NULL
- name (VARCHAR(100)) - NOT NULL
- department_id (BIGINT) - foreign key - NOT NULL


## Table names: `Courses`
**columns**
- id (BIGINT) - primary key - auto_increment - NOT NULL
- name (VARCHAR(100)) - NOT NULL
- degree_course_id (BIGINT) - foreign key - NOT NULL


## Table names: `Teachers`
**columns**
- id (BIGINT) - primary key - auto_increment - NOT NULL
- name (VARCHAR(100)) - NOT NULL
- surname (VARCHAR(100)) - NOT NULL
- matter (VARCHAR(100)) - NOT NULL


## Table names: `Exams`
**columns**
- id (BIGINT) - primary key - auto_increment - NOT NULL
- course_id (BIGINT) - foreign key - NOT NULL
- date (DATE) - NOT NULL


## Table names: `Students`
**columns**
- id (BIGINT) - primary key - auto_increment - NOT NULL
- name (VARCHAR(100)) - NOT NULL
- surname (VARCHAR(100)) - NOT NULL
- code (INT) - NOT NULL
- degree_course_id (BIGINT) - foreign key - NOT NULL


## Table names: `Exam results`
**columns**
- id (BIGINT) - primary key - auto_increment - NOT NULL
- exame_id (BIGINT) - foreign key - NOT NULL
- student_id (BIGINT) - foreign key - NOT NULL
- vote (TINYINT) - NOT NULL
- result (VARCHAR(20)) - NOT NULL
