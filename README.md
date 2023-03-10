# Projeto Modern Data Stack

Repositório para armazenar os artefatos do Pipeline utilizando Modern Data Stack realizado pela Stack Academy com AirByte + DBT + Airflow + SnowFlake + Metabase

## Arquitetura escolhida para o projeto

[![Architecture](https://github.com/guimarczewski/modern-data-stack-stackacademy/raw/main/images/arquitetura.PNG)]()


- Fonte de dados: Google Covid-19 Open Data - https://health.google.com/covid-19/open-data/raw-data

- Airbyte: Deploy utilizando docker container. Utilizado para realizar a ingestão dos dados de covid disponíveis na web, em arquivos csv, no snowflake.

- DBT: Repositório dbt-model contendo a transformação dos dados e separação entre staging e marts e criação da nova tabela covid19_model, resultante do agrupamento das tabelas disponibilizadas pelo Google. [One Developer - ForeverFree]

- Airflow: Deploy utilizando docker container. Utilizado para realizar a orquestração do carregamento airbyte-snowflake e DBT. [Open Source]

- Snowflake: Data Warehouse utilizado no projeto.

- Metabase: Deploy utilizando docker container. Ferramenta de BI para visualização dos dados. [Open Source]


## Ambiente de desenvolvimento

Para ambiente de desenvolvimento desse projeto foi utilizado o Gitpod - https://gitpod.io/ - um ambiente de desenvolvimento em cloud que permite rodar o VS Code, seus plugins, Docker containers, integração Git/Github, entre outras funcionalidades.


## Modelagem DBT - Lineage Graph

[![DBT](https://github.com/guimarczewski/modern-data-stack-stackacademy/raw/main/images/lineage_dbt.jpeg)]()


## Dashboard

[![Dashboard_day](https://github.com/guimarczewski/modern-data-stack-stackacademy/raw/main/images/metabase_day.PNG)]()

[![Dashboard_night](https://github.com/guimarczewski/modern-data-stack-stackacademy/raw/main/images/metabase_night.PNG)]()