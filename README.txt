Modellizzare la struttura di una tabella per memorizzare tutti i dati riguardanti un'università:
    sono presenti diversi dipartimenti, ciascuno con i propri corsi di laurea;
    ogni corso di laurea è formato da diversi corsi;
    ogni corso può essere tenuto da diversi insegnanti e prevede più appelli d'esame;
    ogni studente è iscritto ad un corso di laurea;
    per ogni appello d'esame a cui lo studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente

~~~~~~~~~~~~~~~~~~~~~~~

departments
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
name                STRING          VARCHAR(100)    NOTNULL
address             STRING          VARCHAR(255)    NOTNULL
telephone           STRING          VARCHAR(18)     NOTNULL

~~~~~~~~~~~~~~~~~~~~~~~

degree_courses
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
department_id       NUMBER          SMALLINT        FOREIGN_KEY     AUTO_INCREMENT
name                STRING          VARCHAR(100)    NOTNULL
academic_year       NUMBER          SMALLINT        NOTNULL                         //2021 -> academic year 2021/2022
description         STRING          TEXT            NULL
kind                STRING          VARCHAR(100)    NOTNULL                         //TRIENNALE, MAGISTRALE (Or TINYINT? using options)
language            STRING          VARCHAR(8)      NOTNULL
contacts            STRING          VARCHAR(255)    NOTNULL

~~~~~~~~~~~~~~~~~~~~~~~

teachers
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
first_name          STRING          VARCHAR(16)     NOTNULL
last_name           STRING          VARCHAR(16)     NOTNULL
address             STRING          VARCHAR(100)    NOTNULL
telephone           STRING          VARCHAR(18)     NOTNULL

~~~~~~~~~~~~~~~~~~~~~~~

courses
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
degree_course_id    NUMBER          SMALLINT        FOREIGN_KEY     AUTO_INCREMENT
teacher_id          NUMBER          SMALLINT        FOREIGN_KEY     AUTO_INCREMENT
name                STRING          VARCHAR(80)     NOTNULL
credits             NUMBER          TINYINT         NOTNULL
time                NUMBER          SMALLINT        NULL
year_course         NUMBER          TINYINT         NOTNULL

~~~~~~~~~~~~~~~~~~~~~~~

students
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
degree_course_id    NUMBER          SMALLINT        FOREIGN_KEY     AUTO_INCREMENT
first_name          STRING          VARCHAR(16)     NOTNULL
last_name           STRING          VARCHAR(16)     NOTNULL
address             STRING          VARCHAR(80)     NOTNULL
telephone           STRING          VARCHAR(18)     NOTNULL

~~~~~~~~~~~~~~~~~~~~~~~

exams
id                  NUMBER          SMALLINT        PRIMARY_KEY     AUTO_INCREMENT
course_id           NUMBER          SMALLINT        FOREIGN_KEY     AUTO_INCREMENT
date                DATE            DATE            NOTNULL
description         STRING          VARCHAR(255)    NULL

~~~~~~~~~~~~~~~~~~~~~~~

student_exam
student_id          NUMBER          SMALLINT        PRIMARY_KEY, FOREIGN_KEY   AUTO_INCREMENT
exam_id             NUMBER          SMALLINT        PRIMARY_KEY, FOREIGN_KEY     AUTO_INCREMENT
vote                NUMBER          TINYINT
