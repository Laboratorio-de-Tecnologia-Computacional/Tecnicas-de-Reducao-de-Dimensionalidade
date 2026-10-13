# Técnicas de Redução de Dimensionalidade

**Projeto, Teoria e Aplicações — Uma Abordagem Unificada e Baseada em Cenários**

Aderval S. Luna ([0000-0001-6772-0182](https://orcid.org/0000-0001-6772-0182)) ·
Nathalia Alvim de Souza ([0009-0008-8992-2680](https://orcid.org/0009-0008-8992-2680))

Universidade do Estado do Rio de Janeiro (UERJ), Programa de Pós-Graduação em Engenharia Química

Primeira edição · Rio de Janeiro, Brasil · 2026 · edição digital gratuita, não destinada à venda

**ISBN 978-65-02-42814-6** · **DOI [10.5281/zenodo.23225955](https://doi.org/10.5281/zenodo.23225955)**

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23225955.svg)](https://doi.org/10.5281/zenodo.23225955)
[![ISBN](https://img.shields.io/badge/ISBN-978--65--02--42814--6-0B2447.svg)](https://doi.org/10.5281/zenodo.23225955)
[![Licença: CC BY-NC-SA 4.0](https://img.shields.io/badge/Licen%C3%A7a-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt_BR)
[![R](https://img.shields.io/badge/R-4.5.1-276DC3.svg)](https://cran.r-project.org/)
[![Páginas](https://img.shields.io/badge/livro-320%20p%C3%A1ginas-0B2447.svg)](https://doi.org/10.5281/zenodo.23225955)

Esta é a **edição em português** de *Dimensionality Reduction Techniques: Design, Theory,
and Applications — A Unified and Scenario-Driven Framework* (ISBN 978-65-02-35818-4,
DOI [10.5281/zenodo.22221611](https://doi.org/10.5281/zenodo.22221611)). O código em R, os
conjuntos de dados e as tabelas de métricas são os mesmos das duas edições: tudo o que está
impresso no livro pode ser recalculado a partir do que está publicado aqui.


---

## Sobre o livro

Dados de alta dimensionalidade são hoje rotina nas ciências físicas, biológicas e da
engenharia, e a redução de dimensionalidade tornou-se uma etapa padrão para deles extrair
estrutura interpretável. A dificuldade é que nenhuma técnica é universalmente preferível:
cada método otimiza um objetivo diferente, e uma projeção excelente para visualizar
agrupamentos pode ser ruim para preservar a geometria global ou para sustentar a
reconstrução dos dados.

Este livro trata desse problema com um framework unificado e orientado por cenários.
Quatorze métodos convexos e não convexos são apresentados com sua formulação matemática,
hipóteses, custo computacional e limitações conhecidas, e então avaliados com treze medidas
de qualidade normalizadas. As medidas são combinadas em quatro índices compostos e
ponderadas segundo o objetivo analítico, de modo que a escolha do método decorra do
propósito da análise, e não da convenção. Uma análise de robustez baseada na perturbação de
±10% dos pesos quantifica a estabilidade de cada ranqueamento.

O framework é demonstrado em sete conjuntos de dados de referência do UCI Machine Learning
Repository, com tamanhos de amostra de 88 a 13.611 observações.

**Métodos abordados.** PCA · PCA por kernel · PCA com norma L1 · MDS clássico · MDS não
métrico · Isomap · diffusion maps · DRR · FastICA · Hessian LLE · DrL · Fruchterman–Reingold ·
Kamada–Kawai · t-SNE.

## Como o framework funciona

As treze medidas de qualidade são normalizadas em `[0, 1]`, orientadas de modo que maior
seja sempre melhor, e combinadas em quatro índices compostos.

| Índice | Medidas combinadas |
|---|---|
| `Índice_Local` | Qlocal · confiabilidade · precisão · revocação |
| `Índice_Global` | Qglobal · AUC da curva RNX · correlação cofenética · tau de Kendall |
| `Índice_Geom` | RMSE de reconstrução · descontinuidade · GCE · medida C |
| `Índice_Classe` | acurácia k-NN · precisão · revocação |

Cada objetivo analítico pondera os quatro índices de forma diferente, e a soma ponderada é
a `Pontuação_Final` que produz o ranqueamento.

| Objetivo | Local | Global | Geometria | Classe |
|---|---|---|---|---|
| Agrupamento | 0,50 | 0,20 | 0,15 | 0,15 |
| Reconstrução | 0,30 | 0,30 | 0,40 | 0,00 |
| Visualização | 0,40 | 0,20 | 0,00 | 0,40 |
| Pipeline de ML | 0,40 | 0,20 | 0,00 | 0,40 |

Ao lado do ranqueamento por objetivo, um procedimento de consenso seleciona a medida cujo
ranqueamento mais concorda com todos os demais — a maior média da correlação de Spearman
absoluta na matriz de postos — e informa o método que a otimiza.

## Estudos de caso

| # | Conjunto de dados | n | Variáveis | Classes | Medida de consenso | Campeão |
|---|---|---|---|---|---|---|
| I | Breast Cancer Wisconsin (Diagnostic) | 569 | 30 | 2 | Qlocal | MDS não métrico |
| II | Chemical Composition of Ceramic Samples | 88 | 19 | 2 | Confiabilidade | t-SNE |
| III | Dry Bean | 13.611 | 16 | 7 | Medida C | t-SNE |
| IV | Glass Identification | 214 | 9 | 6 | Descontinuidade | MDS não métrico |
| V | Hepatitis | 155 | 19 | 2 | AUC de RNX | t-SNE |
| VI | Iris | 150 | 4 | 3 | Confiabilidade | Kamada–Kawai |
| VII | Wine | 178 | 13 | 3 | Confiabilidade | t-SNE |



## Dados

Os sete conjuntos de dados vêm do UCI Machine Learning Repository e são redistribuídos aqui
como analisados, para que os resultados possam ser reproduzidos exatamente. Cada um mantém
seu arquivo de documentação original. Cite as fontes originais, listadas nas referências do
livro, junto com o livro.

## Como citar

> LUNA, Aderval S.; ALVIM DE SOUZA, Nathalia. **Técnicas de Redução de Dimensionalidade:
> Projeto, Teoria e Aplicações — Uma Abordagem Unificada e Baseada em Cenários**. 1. ed.
> Rio de Janeiro: Edição dos autores, 2026. 320 p. ISBN 978-65-02-42814-6.
> DOI: 10.5281/zenodo.23225955.



## Licença

O livro, as figuras e o texto estão licenciados sob
[Creative Commons Atribuição-NãoComercial-CompartilhaIgual 4.0 Internacional](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.pt_BR)
(CC BY-NC-SA 4.0) — © 2026 Aderval S. Luna e Nathalia Alvim de Souza. Você pode compartilhar e
adaptar o material para fins não comerciais, desde que atribua o crédito apropriado e distribua
qualquer obra derivada sob a mesma licença.

Os conjuntos de dados permanecem sob os termos de seus provedores originais.

## Agradecimentos

A. S. Luna agradece ao CNPq (304581/2022-4) e à FAPERJ (E-26/204.174/2024) pela bolsa, e à
UERJ pelo Programa PAPD Sênior.

Nathália Alvim agradece ao apoio financeiro do Programa de Formação de Recursos Humanos da Agência Nacional do Petróleo,
Gás Natural e Biocombustíveis – PRH-ANP, gerido pela Fundação de Amparo à Pesquisa do Estado de
São Paulo (FAPESP), Brasil. Processo nº 2025/03791-6

## Contato

Dúvidas sobre o framework, entrar em contato pelo e-mail: adsluna@gmail.com ou natalvimdesouza@hotmail.com 
