## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```sql
SELECT `students`.*
FROM `stundents`
INNER JOIN `degrees`
ON `degrees`.`id` = `students`.`degree_id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia"
``` 

## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```sql
SELECT `degrees`.*
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments_id`
WHERE `departments`.`name` = "Dipertimento di Neuroscienze"
AND `degrees`.`level` = "magistrale"
``` 

## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```sql
SELECT `courses`.*
FROM `courses`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `course_teacher`.`teacher_id` = 44
``` 

## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```sql
SELECT 
-- rinomino le colonne (non serve scrivere AS)

    `students`.`id` `student_id`
    `students`.`name` `student_name`
    `students`.`surname` `student_surname`

    `degrees`.`id` `degree_id`
    `degrees`.`name` `degree_name`

    `departments`.`id` `department_id`
    `departments`.`name` `department_name`

FROM `students`

INNER JOIN `degrees`
ON `student`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

-- uso ORDER BY ... ASC per ordinare in ordine alfabetico
ORDER BY `student_name` ASC, `student_surname` ASC



``` 

## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```sql
SELECT
-- uso AS per leggibilità
	`degrees`.`name` AS `degree_name`,
    `courses`.`name` AS `course_name`,
    `teachers`.`name` AS `teacher_name`

FROM `degrees`

INNER JOIN `courses` 
ON `courses`.`degree_id` = `degrees`.`id`

INNER JOIN `course_teacher` 
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `teachers` 
ON `teachers`.`id` = `course_teacher`.`teacher_id`
``` 

## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
```sql
SELECT `teacher`.*
FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `courses`.`id` = `courses_teacher`.`course_id`

INNER JOIN `degrees`
ON `degrees`.`id` =`courses`.`degree_id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

WHERE `departments`.`name' = "Dipartimento di Matematica"

``` 

## 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
```sql

``` 