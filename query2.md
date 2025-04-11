JOIN

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT  students.*
FROM students 
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT degrees.name AS degree_name, degrees.id, degrees.level, departments.name AS department_name
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Neuroscienze' 
AND degrees.level = 'Magistrale';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT course_teacher.*, teachers.name AS name, teachers.surname, courses.name AS course
FROM course_teacher
JOIN teachers ON course_teacher.teacher_id = teachers.id
JOIN courses ON course_teacher.course_id = courses.id
WHERE teachers.id = 44;


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT students.*, degrees.name AS degree_name, departments.name AS department_name
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname ASC, students.name ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM degrees
JOIN courses ON courses.degree_id = degrees.id
JOIN course_teacher ON course_teacher.course_id = courses.id
JOIN teachers ON course_teacher.teacher_id = teachers.id;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT teachers.*
FROM teachers
JOIN course_teacher ON course_teacher.teacher_id = teachers.id
JOIN courses ON course_teacher.course_id = courses.id
JOIN degrees ON courses.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Matematica';
