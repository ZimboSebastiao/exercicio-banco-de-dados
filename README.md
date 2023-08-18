# Exercícios de modelagem e operações em banco de dados


```sql
CREATE TABLE cursos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT NOT NULL
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
    curso_id TINYINT NOT NULL,
    CONSTRAINT fk_professor FOREIGN KEY (professor_id)  REFERENCES professores(id),
    CONSTRAINT fk_curso FOREIGN KEY (curso_id) REFERENCES cursos(Id)
);
```


```sql

DROP TABLE alunos;
DROP TABLE cursos;
DROP TABLE professores;
```

=========


CREATE TABLE cursos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT NOT NULL,
    professor_id TINYINT  NULL
);


CREATE TABLE alunos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2),
    segunda_nota DECIMAL(4,2),
    curso_id TINYINT NOT NULL,
    CONSTRAINT fk_cursos FOREIGN KEY (curso_id)  REFERENCES cursos(id)
);

CREATE TABLE professores(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
   	area_atuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL, 
    carga_horaria TINYINT NOT NULL,
    curso_id TINYINT NOT NULL
);

ALTER TABLE cursos
    ADD CONSTRAINT fk_cursos_professores
    FOREIGN KEY (professor_id) REFERENCES professores(id);

ALTER TABLE professores
    ADD CONSTRAINT fk_professores_cursos
    FOREIGN KEY (curso_id) REFERENCES cursos(id)