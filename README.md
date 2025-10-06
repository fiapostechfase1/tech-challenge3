🧠 Tech Challenge – Fase 3: Análise PNAD COVID-19
📋 Descrição do Projeto

Este projeto foi desenvolvido como parte do Tech Challenge da Pós-Tech FIAP (Fase 3 – Big Data).
O desafio proposto consiste em atuar como Expert em Data Analytics de um hospital de grande porte, com o objetivo de compreender o comportamento da população brasileira durante a pandemia da COVID-19 e gerar insights estratégicos para o planejamento em caso de novos surtos.

A base de dados utilizada é a PNAD COVID-19, pesquisa realizada pelo IBGE em 2020, que reúne informações sobre saúde, comportamento e condições socioeconômicas da população brasileira durante a pandemia.

🎯 Objetivos

Selecionar 20 perguntas principais da PNAD COVID-19, representando:

- Sintomas e indicadores clínicos;
- Comportamento e medidas de prevenção;
- Condições socioeconômicas da população.
- Criar uma solução analítica completa, com pipeline de dados em nuvem (AWS) e visualização interativa no Power BI.
- Gerar insights acionáveis para auxiliar o hospital parceiro no planejamento de recursos e ações preventivas.

🧩 Arquitetura do Projeto

A arquitetura foi desenvolvida em 10 etapas, organizadas em camadas dentro de um Data Lake na AWS S3.

1️⃣ Coleta de Dados
- Fonte: IBGE – PNAD COVID-19
- Período analisado: Setembro, Outubro e Novembro de 2020
- Formato original: CSV

2️⃣ Estruturação do Data Lake (AWS S3)
- Camada Bronze → Dados brutos (originais, sem tratamento).
- Camada Prata → Dados limpos e padronizados.
- Camada Ouro → Dados refinados e agregados para consumo analítico.

3️⃣ Catalogação (AWS Glue Crawler & Data Catalog)
- Criação automática de schemas e metadados.
- Conversão dos arquivos para o formato Parquet (melhor desempenho).

4️⃣ Limpeza e Processamento (AWS Glue ETL)
- Renomeação e padronização de colunas.
- Criação de dicionários de tradução (ex: uf, sexo, cor_raca).
- Geração de coluna mes e identificação única id_form.
- Armazenamento da versão tratada na camada Prata.

5️⃣ Refinamento (Camada Ouro)
- Seleção das 20 variáveis principais.
- Junção dos três meses (set, out, nov/2020).
- Conversão final para Parquet otimizado.

6️⃣ Consumo Analítico (Power BI)
- Conexão direta com o dataset Parquet local (camada Ouro).
- Modelagem em Star Schema (fato/dimensões).
- Criação de dashboards interativos com indicadores de:
- Saúde e sintomas
- Prevenção e comportamento
- Impactos socioeconômicos

📊 Storytelling dos Painéis

🩺 Painel 1 – Saúde e Sintomas
Mostra os sintomas mais relatados, o comportamento da população diante deles e a relação com os casos confirmados.
- ➡️ Insight principal:
A maioria dos sintomáticos não buscou atendimento médico, revelando o fenômeno de subnotificação e “iceberg epidemiológico”.

🧍‍♀️ Painel 2 – Prevenção e Comportamento
Analisa como a população reagiu às orientações de isolamento, trabalho remoto e uso dos serviços de saúde.
- ➡️ Insight principal:
A adesão às medidas de prevenção foi desigual e fortemente influenciada por condições socioeconômicas, com alta dependência do SUS.

💰 Painel 3 – Socioeconomia e Impactos
Explora os efeitos econômicos da pandemia, destacando os impactos do auxílio emergencial e a vulnerabilidade das micro e pequenas empresas.
- ➡️ Insight principal:
O auxílio emergencial evitou colapso social, mas o fechamento de pequenos negócios gerou consequências indiretas para a saúde mental e financeira da população.

🧱 Tecnologias Utilizadas

| Categoria         | Ferramenta                          | Finalidade                              |
| ----------------- | ----------------------------------- | --------------------------------------- |
| Armazenamento     | **AWS S3**                          | Data Lake (Bronze, Prata, Ouro)         |
| Processamento ETL | **AWS Glue (PySpark)**              | Limpeza, transformação e enriquecimento |
| Catalogação       | **AWS Glue Crawler / Data Catalog** | Inferência de schema e metadados        |
| Consulta SQL      | **AWS Athena**                      | Exploração dos dados                    |
| Visualização      | **Microsoft Power BI**              | Dashboards e storytelling               |
| Linguagem         | **SQL / Python (PySpark)**          | Processamento e transformação de dados  |
| Formato           | **Parquet / CSV**                   | Otimização de armazenamento             |

🧠 Principais Insights

- Sintomas prevalentes: dor de cabeça, coriza e tosse foram os mais relatados.
- Busca por atendimento: menos de 10% dos sintomáticos procuraram ajuda médica.
- Home office: apenas 8,6% conseguiram trabalhar remotamente.
- Dependência do SUS: cerca de 60% buscaram atendimento em unidades públicas.
- Auxílio emergencial: injetou R$ 1,51 bilhão, sustentando milhões de famílias.

🔍 Conclusão

A análise da PNAD COVID-19 evidencia o impacto multifacetado da pandemia sobre a sociedade brasileira — sanitário, comportamental e econômico.
Os resultados obtidos reforçam a importância de dados integrados e inteligência analítica como pilares de suporte à tomada de decisão hospitalar, permitindo antecipar demandas, otimizar recursos e planejar respostas mais eficientes em crises futuras.
