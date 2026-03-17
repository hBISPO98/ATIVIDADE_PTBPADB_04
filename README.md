# ATIVIDADE_PTBPADB_04
Join

[ATT_PTBPABD_04.sql](https://github.com/user-attachments/files/26041222/ATT_PTBPABD_04.sql)

--- Questão01: Uunião da tabela student com a takes.

SELECT * FROM student 
INNER JOIN takes ON student.ID = takes.ID;

--- Questão02: Contar a quantidade de cursos realizados pelos alunos do departamento de Civil Eng.
--- Ordenar de maneira descendente a quantidade de cursos associada aos alunos.

SELECT 
    s.ID, 
    s.name, 
    COUNT(t.course_id) AS "Quantidade de cursos"
FROM student s
JOIN takes t ON s.ID = t.ID
WHERE s.dept_name = 'Civil Eng.'
GROUP BY s.ID, s.name
ORDER BY "Quantidade de cursos" DESC;

--- Questão03: view chamada 'civil_eng_students' a partir da relação construída na Questão02.

GO
CREATE VIEW civil_eng_students AS
SELECT 
    s.ID, 
    s.name, 
    COUNT(t.course_id) AS "Quantidade de cursos"
FROM student s
JOIN takes t ON s.ID = t.ID
WHERE s.dept_name = 'Civil Eng.'
GROUP BY s.ID, s.name;
GO
