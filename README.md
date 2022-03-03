# Caso de Covid 19
### Analise da coleta de dados de uma empresa em contexto da pandemia


Com o decorrer da pandemia, nossa empresa foi obtendo os dados da situação dos funcionários em relação à doença e os sintomas. Esses dados foram salvos numa base, e agora, com objeto de tomar decisões estratégicas sobre o modo de trabalho, quantidade de funcionários por setor, etc., é que surgem da direção as seguintes perguntas:

1 - Quantos casos foram relatados no período por tipo de situação? (Ex: Confirmado, Confirmado Recuperado, etc)

2 - Qual o percentual de casos recuperados por Diretoria?

3 - Quais são os empregados que estão com status atual confirmado e tem uma situação anterior confirmado recuperado?

4 - Qual o percentual de casos por cidade dentro de cada UF? Ordene do maior para o menor.

5 - Qual o modo de trabalho mais recorrente com casos confirmados?

6 - Retorne os 3 maiores tipos de situação dentro de cada diretoria.


A base de dados gerada possui o seguinte esquema:

<p align="center">
  <img src="Estrela.png" >

  Com base nisso elaboramos as seguintes consultas em SQL para trazer respostas e visualizações para esses requisitos:
  
  **1)**
 ```
SELECT
	CASE
	WHEN SITUACAO_ID = '1' THEN "Confirmado" 
	WHEN SITUACAO_ID = '2' THEN "Confirmado recuperado"
	WHEN SITUACAO_ID = '3' THEN "Suspeito"
	WHEN SITUACAO_ID = '4' THEN "Descartado"
	WHEN SITUACAO_ID = '5' THEN "Óbito covid"
	WHEN SITUACAO_ID = '6' THEN "Óbito não covid"
	END AS Situacao,
	COUNT (SITUACAO_ID) AS "Quantidade"
FROM TAB_CASOS
GROUP BY 1
```
