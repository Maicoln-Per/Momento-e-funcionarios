# Momento & Seus Funcionários

A Momento é uma empresa única que faz o melhor que pode para alcançar o melhor da humanidade. 

Dessa forma, O que a Momento faz? 

Há alguma empresa que faça algo parecido? 

E qual o seu ideal de empresa? 

## ***Podemos juntar?***
Podemos!

Nesse exercício vamos usar alguns comandos bem básicos como:

SELECT AVG(*) FROM tabela_exemplo WHERE coluna_exemplo = "Novo Valor";

UPDATE tabela_exemplo SET coluna_exemplo = "Novo Valor" WHERE id = 1;

INSERT INTO tabela_exemplo (coluna_1,, coluna_2) VALUES ("VALOR 1", "VALOR 2");

SELECT paises.pais_name, regiao.regiao_name From paises INNER JOIN regiao On paises.regiao_id = regiao.regiao_id WHERE paises.regiao_id = 4

## ***O que vamos fazer?***

### 1. Inclua suas próprias informações no departamento de tecnologia da empresa
```
INSERT INTO funcionarios(funcionario_id,primeiro_nome,sobrenome,email,senha,telefone,data_contratacao,cargo_id,salario,gerente_id,departamento_id) VALUES (555,'Maicoln','Pereira de Sousa','maicolnp@gmail.com','maicolalindo40028922','523.967.878-97','2023-03-06',8,5500.00,100,6);
```

### 2. A administração está sem funcionários. Inclua alguns colegas de turma nesse departamento. 
```
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)
VALUES 
  (556, 'Carla', 'Silva', 'carla.silva@email.com', 'senhacarla123', '987.654.321-00', '2023-05-15', 5, 4800.00, 101, 1),
  (557, 'Pedro', 'Mendes', 'pedro.mendes@email.com', 'senhapedro456', '123.456.789-01', '2023-07-22', 3, 6000.00, 102, 1),
  (558, 'Ana', 'Santos', 'ana.santos@email.com', 'senhaana789', '555.111.222-33', '2023-09-10', 7, 7000.00, 103, 1),
  (559, 'Rafael', 'Oliveira', 'rafael.oliveira@email.com', 'senharafaelabc', '777.888.999-44', '2023-11-28', 6, 5500.00, 104, 1),
  (560, 'Fernanda', 'Costa', 'fernanda.costa@email.com', 'senhafernanda567', '222.333.444-55', '2024-01-05', 4, 6200.00, 105, 1);
```
### 3. Agora diga, quantos funcionários temos ao total na empresa?
```
SELECT COUNT(*) AS total_funcionarios FROM funcionarios;
```
### 4. Quantos funcionários temos no departamento de finanças?
```
SELECT AVG(salario) AS media_salarial_tecnologia FROM funcionarios WHERE departamento_id = "6";
```
### 5. Qual a média salarial do departamento de tecnologia?
```
SELECT SUM(salario) AS gasto_total_salarios_transportes FROM funcionarios WHERE departamento_id = "5";
```
### 6. Quanto o departamento de Transportes gasta em salários?
```
SELECT SUM(salario) AS gasto_total_salarios_transportes FROM funcionarios WHERE departamento_id = "5";
```
### 7. Um novo departamento foi criado. O departamento de inovações. 
Ele será locado no Brasil. Por favor, adicione-o no banco de dados.
```
INSERT INTO escritorios(escritorio_id,escritorio_nome,endereco,cep,cidade,estado_provincia,pais_id) VALUES (5570,"Bar de Nárnia",'Rua Alameda Santos','09876','Guarulhos','São Paulo','BR');
INSERT INTO departamentos(departamento_id,departamento_nome,escritorio_id) VALUES (14,'Inovações',5570);
```
### 8. Três novos funcionários foram contratados para o departamento de inovações. 
Por favor, adicione-os: William Ferreira, casado com Inara Ferreira, 
possuem uma filha chamada Maria Antônia que tem 1 anos e adora brincar com cachorros. 
Ele será programador.
Já a Fernanda Lima, que é casada com o Rodrigo, não possui filhos. 
Ela vai ocupar a posição de desenvolvedora.  
Por último, a Gerente do departamento será Sumaia Azevedo. 
Casada, duas filhas (Tainã e Nathalia).
```
INSERT INTO cargos(cargo_id,cargo_nome,min_salario,max_salario) VALUES (23,'Programador',2200.00,9000.00);
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)
VALUES (561, 'William', 'Ferreira', 'william.ferreira@email.com', 'senhaWilliam123', '11932466556', '2024-02-01', 23, 6000.00, 563, 14);
INSERT INTO dependentes(dependente_id, primeiro_nome, sobrenome, relacionamento, funcionario_id)
VALUES (38, 'Maria Antônia', 'Ferreira', 'Filha', 561);
```
```
INSERT INTO cargos(cargo_id,cargo_nome,min_salario,max_salario) VALUES (24,'Desenvolvedor',4200.00,9500.00);
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)
VALUES (562, 'Fernanda', 'Lima', 'fernanda.lima@email.com', 'senhaFernanda456', '11986570454', '2024-02-01', 24, 5500.00, 563, 14);
```
```
INSERT INTO cargos(cargo_id,cargo_nome,min_salario,max_salario) VALUES (22,'Gerente de Tecnologia',8000.00,16000.00);
INSERT INTO funcionarios(funcionario_id, primeiro_nome, sobrenome, email, senha, telefone, data_contratacao, cargo_id, salario, gerente_id, departamento_id)
VALUES (563, 'Sumaia', 'Azevedo', 'sumaia.azevedo@email.com', 'senhaSumaia789', '11976546545', '2021-01-04', 22, 7000.00, NULL, 14);
INSERT INTO dependentes(dependente_id, primeiro_nome, sobrenome, relacionamento, funcionario_id)
VALUES(39, 'Tainã', 'Azevedo', 'Filha', 563), (40, 'Nathalia', 'Azevedo', 'Filha', 563);
```
#### O salário de todos eles será a média salarial dos departamentos de administração e finanças.
```
SELECT AVG(salario) AS media_salarial FROM funcionarios WHERE departamento_id IN (1, 10);
```
### 9. Informe todas as regiões em que a empresa atua acompanhadas de seus países.
```
SELECT r.regiao_nome, p.pais_nome FROM regioes r JOIN paises p ON r.regiao_id = p.regiao_id;
```
### 10. Joe Sciarra é filho de quem?
> Filho do Ismael Sciarra
```
SELECT primeiro_nome, sobrenome FROM funcionarios WHERE funcionario_id = 111; 
```
### 11. Jose Manuel possui filhos?
> Christian Urman
```
SELECT primeiro_nome, sobrenome FROM dependentes WHERE funcionario_id = 112;
```
### 12. Qual região possui mais países?
> Europa, com 11 países
```
SELECT r.regiao_nome, COUNT(p.pais_id) AS total_paises
FROM regioes r
JOIN paises p ON r.regiao_id = p.regiao_id
GROUP BY r.regiao_id
ORDER BY total_paises DESC
LIMIT 1;
```
### 13. Exiba o nome cada funcionário acompanhado de seus dependentes.
```
SELECT
  f.primeiro_nome AS nome_funcionario,
  d.primeiro_nome AS nome_dependente
FROM
  funcionarios f
LEFT JOIN
  dependentes d ON f.funcionario_id = d.funcionario_id;
```
### 14. Karen Partners possui um(a) cônjuge?
> Apenas um filho: Alec Partners
```
SELECT primeiro_nome, sobrenome, relacionamento FROM dependentes WHERE funcionario_id = 146;
```
