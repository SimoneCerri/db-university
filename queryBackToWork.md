# !Quest! #

Run those query on phpMyAdmin.

## Group by
1. Contare quanti iscritti ci sono stati ogni anno
    - SELECT YEAR(enrolment_date) AS Anno, COUNT(*) AS Iscritti FROM students GROUP BY YEAR(enrolment_date);
2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    - SELECT office_number, COUNT(id) AS insegnanti FROM teachers GROUP BY office_number;
3. Calcolare la media dei voti di ogni appello d'esame
    - SELECT exam_id AS Appello, AVG(vote) AS Media_Voti FROM exam_student GROUP BY exam_id;
4. Contare quanti corsi di laurea ci sono per ogni dipartimento
    - SELECT department_id, COUNT(DISTINCT name) AS Numero_Corsi_Laurea FROM degrees GROUP BY department_id;

## Joins
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    - SELECT students.* FROM students JOIN degrees ON students.degree_id = degrees.id WHERE degree_id = 53;
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    - SELECT degrees.* FROM degrees JOIN departments ON degrees.department_id = department_id WHERE departments.name = 'Dipartimento di Neuroscienze' AND degrees.level = 'magistrale';
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    - SELECT course_teacher.* FROM course_teacher JOIN teachers ON course_teacher.teacher_id = teachers.id WHERE teachers.id = 44;
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - SELECT students.*, degrees.name AS corso_laurea, departments.name AS dipartimento FROM students JOIN degrees ON students.degree_id = degrees.id JOIN departments ON degrees.department_id = departments.id ORDER BY students.surname, students.name;
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    - SELECT degrees.name AS corso_laurea, courses.name AS corso, teachers.name AS insegnante FROM degrees JOIN courses ON degrees.id = courses.degree_id JOIN teachers ON course_teacher.teacher_id = teachers.id; ***[!NOT WORKING!]***
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    - ???????????????????????????????????????????????????????????????????????

## BONUS
Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.