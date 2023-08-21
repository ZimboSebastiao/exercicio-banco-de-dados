# Exercícios de Banco de Dados - Etapa 3

## 1) Faça uma consulta que mostre os alunos que nasceram antes do ano 2009
```sql
SELECT data_nascimento AS 'Data de Nascimento' FROM alunos 
WHERE YEAR(data_nascimento) < 2009;
```
![Alt text](img/image.png)

## 2) Faça uma consulta que calcule a média das notas de cada aluno e as mostre com duas casas decimais.

```sql
SELECT id, ROUND(AVG((primeira_nota + segunda_nota) / 2), 2) As 'Média dos Alunos'
FROM alunos
GROUP BY id;
```
![Alt text](img/image-1.png)

## 3) Faça uma consulta que calcule o limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária. Classifique em ordem crescente pelo título do curso.

```sql
SELECT titulo, ROUND(carga_horaria * 0.25) AS 'Limite de Faltas'
FROM cursos
ORDER BY titulo ASC;
```
![Alt text](img/image-2.png)

## 4) Faça uma consulta que mostre os nomes dos professores que são somente da área "desenvolvimento".

```sql
SELECT nome AS Docente
FROM professores
where area_atuacao = 'desenvolvimento';
```
![Alt text](img/image-3.png)


## 5) Faça uma consulta que mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui.

```sql
SELECT area_atuacao AS 'Área de Atuação', COUNT(*) AS 'QTD de Docentes'
FROM professores
GROUP BY area_atuacao;
```
![Alt text](img/image-4.png)