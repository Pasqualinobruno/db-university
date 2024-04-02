Dopo aver creato un nuovo database nel vostro phpMyAdmin e aver importato lo schema allegato, eseguite le query del file allegato.

### 1. Selezionare tutti gli studenti nati nel 1990 (160)
- SELECT * FROM `students` WHERE YEAR(date_of_birth) = 1990;

### 2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
- SELECT * FROM `courses` WHERE `cfu` > 10;

### 3. Selezionare tutti gli studenti che hanno più di 30 anni
- SELECT * FROM `students` WHERE YEAR(date_of_birth) < 1994;

### 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
- SELECT * FROM `courses` WHERE `period` = 'I semestre' AND Year = 1;

### 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
- SELECT * FROM `exams` WHERE `hour` > '14:00:00' AND `date` = '2020-06-20';

### 6. Selezionare tutti i corsi di laurea magistrale (38)
- SELECT * FROM `degrees` WHERE `level` = 'magistrale';

### 7. Da quanti dipartimenti è composta l'università? (12)
- SELECT COUNT(*) AS `Dipartimenti` FROM `departments`;

### 8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
- SELECT * FROM `teachers` WHERE `phone` IS NULL;

Cosa consegnare?
Dopo aver testato le vostre query con phpMyAdmin, riportatele in un file txt e caricatelo nella vostra repo.


Group by:
### 1. Contare quanti iscritti ci sono stati ogni anno
Data completa
- SELECT `enrolment_date`, COUNT(`enrolment_date`) AS `students_enrolment`
- FROM `students`
- GROUP BY `enrolment_date`;

Solo per anno
- SELECT COUNT(*) AS `number_students`, YEAR(`enrolment_date`) AS `year_enrolment`
- FROM `students`
- GROUP BY YEAR(`enrolment_date`);


### 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
- SELECT COUNT(*) AS `number_teachers`, `office_address`
- FROM `teachers`
- GROUP BY `office_address`;


### 3. Calcolare la media dei voti di ogni appello d'esame
- SELECT AVG(`vote`) , `exam_id`
- FROM `exam_student`
- GROUP BY `exam_id`;

### 4. Contare quanti corsi di laurea ci sono per ogni dipartimento
- SELECT COUNT(`name`) AS `cors`, `department_id` AS `departments`
- FROM`degrees`
- GROUP BY `department_id`;



Joins:
### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
- SELECT `students`.`*`, `degrees`.`address`, `degrees`.`email`, `degrees`.`website`
- FROM `students`
- JOIN `degrees`
- ON `students`.`degree_id` = `degrees`.`id`
- WHERE `degrees`.`name` = "Corso di Laurea in Economia";



### 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
- SELECT `degrees`.`*`, `degrees`.`name` AS `name_degrees` 
- FROM `degrees`
- JOIN `departments`
- ON `degrees`.`department_id` = `departments`.`id`
- WHERE `degrees`.`level` = "magistrale" AND `departments`.`name` = "Dipartimento di Neuroscienze";


### 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
- SELECT *
- FROM `course_teacher`
- WHERE `teacher_id` = 44;


### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.