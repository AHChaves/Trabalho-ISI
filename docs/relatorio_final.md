# Trabalho de Introdução aos Sistemas Inteligentes

**Arthur Henrique Chaves Oliveira**  
**Sophia Neves Alvim Ottoni**  
**Lucas Rodrigues Caetano Matos**


## Sumário

1. [BASE DE DADOS](#base-de-dados)
   1. [Dicionário de dados](#dicionário-de-dados)
   2. [Redução da base de dados](#redução-da-base-de-dados)
   3. [Resultado](#resultado)
2. [O PROBLEMA](#o-problema)
3. [ANÁLISE EXPLORATÓRIA](#análise-exploratória)
   1. [Admissão maior que 90%](#admissão-maior-que-90)
   2. [TOEFL acima e abaixo da mediana](#toefl-acima-e-abaixo-da-mediana)
      1. [Acima da mediana](#acima-da-mediana)
      2. [Abaixo da mediana](#abaixo-da-mediana)
   3. [CGPA acima ou abaixo da mediana](#cgpa-acima-ou-abaixo-da-mediana)
      1. [Acima da mediana](#cgpa-acima-da-mediana)
      2. [Abaixo da mediana](#cgpa-abaixo-da-mediana)
4. [GRÁFICOS](#gráficos)
   1. [Gráfico geral](#gráfico-geral)
   2. [Gráfico baseado em Chance of Admit](#gráfico-baseado-em-chance-of-admit)
      1. [TOEFL](#toefl)
      2. [CGPA](#cgpa)
      3. [GRE Score](#gre-score)
   3. [Gráfico baseado no TOEFL](#gráfico-baseado-no-toefl)
      1. [CGPA](#cgpa-2)
      2. [GRE Score](#gre-score-2)
5. [CONCLUSÃO](#conclusão)

## BASE DE DADOS

Para a realização deste trabalho foi decidido a utilização da base de dados “Data for Admission in the University”. Esta base de dados fornece informações sobre diversos alunos, como: GRE Scores, TOEFL score, university rating, etc; além da chance que eles possuem de serem admitidos nas universidades. Ela possui 400 dados de diferentes alunos.

### Dicionário de dados

| Coluna/Atributo   | Tipo de dado           | Descrição |
|-------------------|------------------------|-----------|
| Serial Number     | Números Inteiros (int) | Dado que nos informa o índice da pessoa referente a linha, ele vai de 1 a 400. |
| GRE score         | Inteiro                | Atributo que guarda a nota obtida pelo aluno no GRE (Graduate Record Examination), indo de 0 a 340. |
| TOEFL score       | Inteiro                | Atributo que nos informa a nota obtida pelo aluno no TOEFL (Test of English as a Foreign Language), os valores desta coluna variam entre 0 e 120. |
| University Rating | Categórico ordinal     | Define a qualidade da universidade em que o aluno está tentando passar. Os dados dessa coluna vão de 1 a 5, sendo: 1 - qualidade muita baixa, 2 - qualidade baixa, 3 - qualidade razoável, 4 - qualidade boa, 5 - qualidade muito boa. |
| LOR               | Categórico ordinal     | Atributo que informa a qualidade da Letter of Recommendation que foi enviado à universidade. Esse atributo varia de 1 a 5 (1, 1.5, 2, 2.5, ..., 5), sendo valores mais próximos de 1 uma qualidade ruim e valores mais próximos de 5 uma qualidade boa. |
| SOP               | Categórico ordinal     | Atributo que guarda a qualidade do Statement of Purpose que foi enviado à universidade. Esse atributo varia de 1 a 5 (1, 1.5, 2, 2.5, ..., 5), sendo valores mais próximos de 1 uma qualidade ruim e valores mais próximos de 5 uma qualidade boa. |
| Research          | Booleano               | Define se a pessoa referência já participou de pesquisas ou não. |
| CGPA              | Número Real (float)    | Dado que informa o valor do Undergraduate Grade Point Average do aluno, esse valor varia de 1 a 10. |
| Chance of Admit   | Percentual             | Atributo que guarda a chance do aluno passar na universidade escolhida, esse valor está em porcentagem. |

### Redução da base de dados

Após uma análise dos atributos presentes na tabela foi-se considerado desnecessário a presença do atributo “Serial Number”, portanto sua remoção foi feita por meio de um código em python.

### Resultado

Tendo sido feita a redução de atributos a base de dados fica desta forma:
![Imagem 1 - Tabela de dados](https://raw.githubusercontent.com/AHChaves/Trabalho-ISI/main/assets/results/foto%20tabela.png)

Fonte: tabela modificada pelos autores

## O PROBLEMA

Nos dias atuais diversos alunos querem realizar um curso de mestrado no exterior, no entanto muitos deles não sabem o que é necessário fazer para poder entrar, ou o quão bem eles precisam ir nos testes para poder passar. Pensando nisso, o nosso projeto busca identificar quais atributos possuem uma maior influência na chance de uma pessoa ser admitida no mestrado de uma determinada universidade.

Tendo como exemplo um aluno que teve seu CGPA baixo, um dado que não poderia ser alterado a não ser que seja realizada uma nova graduação, deveria então focar em outros campos para poder ter uma maior chance de admissão. Ele então poderia utilizar de nossos resultados para procurar os pontos de melhoria precisos.

## ANÁLISE EXPLORATÓRIA

Uma análise estatística da tabela se torna necessária para podermos tirar conclusões sobre a mesma. Esta análise seria feita por meio das médias, medianas, e modas dos atributos, esses valores são obtidos pela utilização de um código em python.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 316.8  | 317     | 312; 324 | 340  | 290  |
| TOEFL score       | 107.41 | 107     | 110      | 120  | 92   |
| University Rating | 3.08   | 3       | 3        | 5    | 1    |
| LOR               | 3.45   | 3.5     | 3        | 5    | 1    |
| SOP               | 3.4    | 3.5     | 3.5; 4   | 5    | 1    |
| CGPA              | 8.59   | 8.61    | 8        | 9.92 | 6.8  |
| Chance of Admit   | 72.43% | 73%     | 64%      | 97%  | 34%  |

Fonte: elaborada pelos autores

Com uma análise da tabela é possível notar uma separação muito grande entre os valores mínimos e máximos dos atributos, além de valores de média e mediana sempre muito próximos.

Para podermos analisar ainda mais a fundo os valores obtidos foi feita uma separação dos dados pela mediana e faixa de valores de alguns deles, resultando em algumas categorias de dados, sendo elas: pessoas com a chance de admissão maior que 90%, pessoas que tiveram o TOEFL acima e abaixo da mediana, pessoas com o CGPA abaixo e acima da mediana.

### Admissão maior que 90%

A separação das pessoas que possuíam uma chance maior ou igual a 90% melhora a visualização de possíveis padrões em quem possui a maior chance de ser admitido em uma universidade, como por exemplo o fato de os valores de CGPA estarem todos acima de 9.16, ou o fato da moda do GRE para essa faixa de valores ser igual a 340.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 333.24 | 334     | 340      | 340  | 320  |
| TOEFL score       | 116.26 | 116     | 118      | 120  | 110  |
| University Rating | 4.56   | 5       | 5        | 5    | 2    |
| LOR               | 4.42   | 4.5     | 4.5      | 5    | 3    |
| SOP               | 4.3    | 4.5     | 4.5      | 5    | 3    |
| CGPA              | 9.49   | 9.5     | 9.65     | 9.92 | 9.16 |

Fonte: elaborada pelos autores

### TOEFL acima e abaixo da mediana

Separar os dados de acordo com a mediana dos atributos nos permite verificar quais são as características de pessoas com os melhores e os piores resultados.

#### Acima da mediana

Com a separação dos dados pelo valor da mediana de TOEFL, conseguimos observar que as pessoas que obtiveram uma nota acima da mediana possuem também uma nota de GRE superior a média.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 322.33 | 322     | 320      | 340  | 310  |
| TOEFL score       | 113.02 | 113     | 113      | 120  | 108  |
| University Rating | 3.66   | 4       | 4        | 5    | 1    |
| LOR               | 3.86   | 4       | 4        | 5    | 2    |
| SOP               | 3.73   | 4       | 4        | 5    | 1    |
| CGPA              | 9.04   | 9.11    | 8.87     | 9.92 | 7.9  |
| Chance of Admit   | 81.54% | 82%     | 90%      | 97%  | 51%  |

Fonte: elaborada pelos autores

#### Abaixo da mediana

Para aqueles alunos que não atingiram a mediana do TOEFL, podemos observar que suas chances de admissão são, em média, consideravelmente menores.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 311.34 | 311     | 313      | 340  | 290  |
| TOEFL score       | 101.78 | 101     | 100      | 107  | 92   |
| University Rating | 2.52   | 2       | 1        | 5    | 1    |
| LOR               | 3.04   | 3       | 3        | 5    | 1.5  |
| SOP               | 3.06   | 3       | 3        | 5    | 1    |
| CGPA              | 8.12   | 8.18    | 8.02     | 9.89 | 6.8  |
| Chance of Admit   | 63.32% | 62.5%   | 50%      | 93%  | 34%  |

Fonte: elaborada pelos autores

### CGPA acima ou abaixo da mediana

#### Acima da mediana

A tabela abaixo mostra que alunos com CGPA acima da mediana geralmente possuem uma pontuação TOEFL e GRE superior.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 321.87 | 322     | 324      | 340  | 301  |
| TOEFL score       | 112.13 | 112     | 110      | 120  | 100  |
| University Rating | 3.5    | 4       | 4        | 5    | 1    |
| LOR               | 3.72   | 4       | 4        | 5    | 2    |
| SOP               | 3.63   | 4       | 4        | 5    | 1    |
| CGPA              | 9.06   | 9.11    | 8.87     | 9.92 | 8.03 |
| Chance of Admit   | 80.22% | 82%     | 90%      | 97%  | 34%  |

Fonte: elaborada pelos autores

#### Abaixo da mediana

Alunos com CGPA abaixo da mediana apresentam, em média, pontuações TOEFL e GRE menores.

| Coluna/Atributo   | Média  | Mediana | Moda     | Máx  | Min  |
|-------------------|--------|---------|----------|------|------|
| GRE score         | 311.42 | 312     | 313      | 340  | 290  |
| TOEFL score       | 102.7  | 103     | 104      | 117  | 92   |
| University Rating | 2.65   | 3       | 2        | 5    | 1    |
| LOR               | 3.18   | 3       | 3        | 5    | 1.5  |
| SOP               | 3.2    | 3       | 3        | 5    | 1    |
| CGPA              | 8.12   | 8.2     | 8.02     | 9.0  | 6.8  |
| Chance of Admit   | 64.44% | 64.5%   | 50%      | 93%  | 34%  |

Fonte: elaborada pelos autores

## GRÁFICOS

Os gráficos a seguir representam visualmente as correlações entre os atributos analisados e a chance de admissão dos alunos.

### Gráfico geral

![Gráfico Geral](../assets/results/Geral.png)

Fonte: elaborado pelos autores

### Gráfico baseado em Chance of Admit

Os gráficos a seguir representam a correlação entre Chance of Admit e os principais atributos analisados.

#### TOEFL

![Gráfico TOEFL](#)

Fonte: elaborado pelos autores

#### CGPA

![Gráfico CGPA](#)

Fonte: elaborado pelos autores

#### GRE Score

![Gráfico GRE Score](#)

Fonte: elaborado pelos autores

### Gráfico baseado no TOEFL

Os gráficos abaixo mostram a correlação entre TOEFL e os principais atributos analisados.

#### CGPA

![Gráfico CGPA - TOEFL](#)

Fonte: elaborado pelos autores

#### GRE Score

![Gráfico GRE Score - TOEFL](#)

Fonte: elaborado pelos autores

## CONCLUSÃO

Através da análise realizada, verificamos que os alunos que obtiveram as maiores chances de admissão em programas de mestrado possuíam notas elevadas nos exames TOEFL e GRE, além de um CGPA elevado. A qualidade das cartas de recomendação (LOR) e declarações de propósito (SOP) também se mostrou relevante, mas com impacto menor comparado aos exames e ao GPA.

Com isso, é recomendável que alunos interessados em programas de mestrado no exterior invistam fortemente na preparação para os exames TOEFL e GRE, e mantenham um alto desempenho acadêmico durante a graduação para maximizar suas chances de admissão.
