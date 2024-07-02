1. Selezionare tutti gli studenti nati nel 1990 (160)
SELECT
    *
FROM
    `students`
WHERE
    `date_of_birth` BETWEEN '1990-01-01' AND '1990-12-31'
  
//YEAR(La funzione YEAR restituisce la parte dell'anno per una data specificata.)
SELECT
    *
FROM
    `students`
WHERE
    YEAR(`date_of_birth`) = 1990
************************** 
2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
SELECT
    *
FROM
    `courses`
WHERE
    `cfu`> 10
************************** 
3. Selezionare tutti gli studenti che hanno più di 30 anni
//TIMEDIFF: Restituisce la differenza tra due valori di tempo o datetime.
//CURDATE: Restituisce la data corrente del server nel formato 'YYYY-MM-DD'.
//TIMESTAMP: Restituisce un valore datetime combinando una data e un'ora specificate.
SELECT
    *
FROM
    `students`
WHERE
    TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) > 30
************************** 
4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
SELECT
    *
FROM
    `courses`
WHERE
    `year` = 1 AND `period` = 'I semestre'
************************** 
5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
SELECT
    *
FROM
    `exams`
WHERE
    `date` = '2020-06-20' AND `hour` > '14.00.00'

//HOUR: Restituisce la parte dell'ora per un valore di data o datetime, con un intervallo da 0 a 23.
SELECT
    *
FROM
    `exams`
WHERE
    `date` = '2020-06-20' AND HOUR(`hour`)>=14
************************** 
6. Selezionare tutti i corsi di laurea magistrale (38)
SELECT
    *
FROM
    `degrees`
WHERE
    `level` = 'magistrale'
************************** 
7. Da quanti dipartimenti è composta l'università? (12)
//COUNT(*): Conta tutte le righe in una tabella.
SELECT
    COUNT(`id`) AS`numero_dipartimenti`
FROM
    `departments`
************************** 
8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
//FUNZIONE
SELECT
    COUNT(*) AS `nophone_teachers`
FROM
    `teachers`
WHERE
    `phone` IS NULL
************************** 
9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo
degree_id, inserire un valore casuale)
INSERT INTO `students`(
    `degree_id`,
    `name`,
    `surname`,
    `date_of_birth`,
    `fiscal_code`,
    `enrolment_date`,
    `registration_number`,
    `email`    
)
VALUES(
    '1',
    'nicola',
    'lippo',
    '1998-05-27',
    'LPPNCL98E27D883P',
    '2024-03-13',
    '12345',
    'nicola@lippo.com'
)
************************** 
10. Cambiare il numero dell’ufficio del professor Artemide Rizzi in 126
//L'operatore LIKE è utilizzato nelle istruzioni SELECT per cercare un modello specifico nelle colonne che contengono dati di tipo testo.
UPDATE `teachers`
SET `office_number` = '126'
WHERE `name` = 'Artemide' AND `surname` = 'Rizzi'
************************** 
11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9
DELETE FROM `students`
WHERE `id` LIKE '5002'