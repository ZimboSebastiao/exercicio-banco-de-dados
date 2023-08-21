# ETAPA 1 - Exercícios de modelagem e operações em banco de dados

## Criação das tabelas 

```sql
CREATE TABLE cursos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT NOT NULL,
    professor_id TINYINT  NULL
);
```


```sql
CREATE TABLE alunos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2),
    segunda_nota DECIMAL(4,2),
    curso_id TINYINT NOT NULL,
    CONSTRAINT fk_cursos FOREIGN KEY (curso_id)  REFERENCES cursos(id)
);
```



```sql
CREATE TABLE professores(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
   	area_atuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL, 
    carga_horaria TINYINT NOT NULL,
    curso_id TINYINT NOT NULL
);
```

## Adição das chaves estrangeiras

```sql
ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores
    FOREIGN KEY (professor_id) REFERENCES professores(id);
```

```sql
ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos
    FOREIGN KEY (curso_id) REFERENCES cursos(id)
```

## Comandos para deletar as tabelas

```sql

DROP TABLE alunos;
DROP TABLE cursos;
DROP TABLE professores;
```

=================================================================
# CRUD - Cadastro geral

## Cadastro de 5 cursos:

```sql
INSERT INTO cursos(titulo, carga_horaria)
VALUES('Back_End', 80),
	  ('Front_End', 40h),
	  ('UX/UI Design', 30),
      ('Figma', 10),
      ('Redes de Computadores', 100)
;
```

## Cadastro de 5 professores:

```sql
INSERT INTO professores(nome, area_atuacao, curso_id)
VALUES('Jon Oliva', 'infra', 5),
	  ('Lemmy Kilmister', 'design', 4),
	  ('Neil Peart', 'design', 3),
      ('Ozzy Osbourne', 'desenvolvimento', 2),
      ('David Gilmour', 'desenvolvimento', 1)
;
```

## Atualização dos dados do campo professor_id da tabela cursos, associando cada curso ao seu professor correspondente:

```sql
UPDATE cursos SET professor_id = 6
WHERE id = 5; 

UPDATE cursos SET professor_id = 7
WHERE id = 4;

UPDATE cursos SET professor_id = 8
WHERE id = 3;

UPDATE cursos SET professor_id = 9
WHERE id = 2;

UPDATE cursos SET professor_id = 10
WHERE id = 1;

```

## Cadastro de 10 alunos:

```sql
INSERT INTO alunos(nome, data_nascimento, primeira_nota, segunda_nota, curso_id)
VALUES('Aicha Mubobo', '2000-05-15', 10.00, 10.00, 5),
	  ('Adriana Manuel','1995-12-14', 9.00, 8.00, 4),
	  ('Ndombele João','2001-04-17', 7.00, 8.00, 3),
	  ('Anacleta Kiesse','1985-04-14', 10.00, 10.00, 4),
	  ('João Paulo','2000-01-08', 10.00, 10.00, 2),
	  ('Graciano Mangurra','2000-03-13', 10.00, 10.00, 4),
	  ('Ariel Ngurra','2000-09-29', 10.00, 10.00, 1),
	  ('Paulo Afonso','1998-6-19', 4.00, 6.00, 1),
	  ('Carlos Diogo','1991-08-12', 3.00, 8.00, 2),
	  ('Mateus Afonso','1999-02-14', 5.00, 7.00, 5)
;
```







