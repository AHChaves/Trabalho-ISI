# Trababalho de Introdução aos Sistemas Inteligentes

* [Arthur Henrique Chaves Oliveira](https://github.com/AHChaves)
* [Sophia Neves Alvim Ottoni](https://github.com/sophiaottoni)
* [Lucas Rodrigues Caetano Matos](https://github.com/LRCaetanoM)

## Resumo

Este trabalho foi realizado, com fins de aprendizado, para a disciplina de Introdução aos Sistemas Inteligentes(ISI) da PUC Minas, ele analisa a base de dados "Data for Admission in the University", que contém informações de 400 alunos, incluindo notas de exames (GRE e TOEFL), avaliações de universidades, qualidade de cartas de recomendação (LOR) e declarações de propósito (SOP), participação em pesquisas, GPA e chance de admissão. Utilizando métodos estatísticos e gráficos, investigamos quais atributos influenciam mais a chance de admissão em programas de mestrado no exterior. A análise é feita com base na mediana e em outras categorias, destacando a importância do desempenho acadêmico e das habilidades em inglês na obtenção de uma vaga.

## Organização do repositório

```
├── Trabalho ISI
│
│
├── assets/
│   ├── data/ (Pasta que guarda as tabelas de dados)
│   │   ├── adm_data_reduced.csv (Base de dados tratada)
│   │   │
│   │   └── adn_data.csv (Base de dados original)
│   │
│   └── results/ (pasta que guarda as imagens dos gráficos)
│       └── *.png
│
├── docs/ (documentos do projeto)
│   ├── Trabalho de Introdução aos Sistemas Inteligentes.pdf (relatorio no modelo de
│   │   artigo acadêmico)
│   │
│   └── relatorio_final.md (relatorio como .md)
│
├── src/ (pasta que guarda os arquivos .ipynb utilizados)
│   ├── Analise_Exploratoria.ipynb (arquivo que é realizada a analise exploratória,
│   │   processo que os dados são analisados por meio de estatística simples)
│   │
│   ├── Graficos.ipynb (Arquivo que contem os codigos que utilizados para a geração 
│   │   dos gráficos) 
│   │  
│   └── Limpeza_de_daos.ipynb (Onde é retirada as colunas desnecessárias da tabela
│       original)
│
└── README.md
```