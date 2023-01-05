# airbyte-dbt-airflow-snowflake-metabase
Repositório para armazenar os artefatos do Pipeline utilizando Modern Data Stack com AirByte + DBT + Airflow + SnowFlake + Metabase


Tarefas:

Infraestrutura:

- Setup do ambiente de desenvolvimento gitpod.io https://gitpod.io (Hardware, Software - Linux, Python, Docker, Curl, Pip, Git, Npm, etc...) X

- Setar as Permissoes do Gitpod ao Repositorio no Github (https://gitpod.io/integrations) X

- Subir o Airbyte via docker - https://docs.airbyte.com/quickstart/deploy-airbyte/ (Realizar antes um fork do repositório do airbyte para a minha conta, para poder fazer alterações, e depois cria uma nova branch para esse repo. Depois faz o git clone com o meu repo.  
git clone -b modern-data-stack https://github.com/guimarczewski/airbyte.git 
Depois altera o .env retirando user e senha, depois 
cd airbyte
docker-compose up) x

- Subir o Airflow via docker - https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html (cria uma pasta "airflow", 
cd airflow, curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.5.0/docker-compose.yaml'
mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)" > .env
docker compose up airflow-init
docker-compose up
user e senha foram setados no arquivo docker-compose.yaml) x

- Criar arquivo ".gitignore" dentro da pasta airflow e incluir "logs/*" para ignorar todos os arquivos dentro da pasta logs ao fazer o commit. Só depois disso faz o commit. x

- Subir o Metabase via docker e utilizar o docker-compose - https://gist.github.com/eliashussary/379e44a99e2389bd6a8ea6a23c2d5af8 (Cria um diretório metabase e arquivo docker-compose.yaml, dentro desse arquivo remove o postgres e da linha environment para baixo, pois usaremos o snowflake, e altera a porta para 3000. Após isso "cd metabase" e docker-compose up" ) x

- Criar o script de execução - script linux para subir containers automaticamente... Será feito no final

- Testar a Execução

- Snowflake Data Warehouse:
    
    - Criar a Conta no SnowFlake x
    - Verificar a existência das tabelas x
    - Obter os links de conexão e nome da conta x


Extração:

- No Airbyte:

    - Conectar com as origens baseadas nos Csvs x
    - Criar as entidades no snowflake através do script base da documentação x
    - Conectar o destino no snowflake x
    - Criar as conexões do airbyte associando as origens ao destino x
    - Testar as conexões x


Preparação:

- No Airbyte (Destination Loading Method):

    - Local Staging (Ambiente de Desenvolvimento) x
    - Cloud Staging (Ambiente de Produção) x


Transformação:

- No Dbt:

    - Criação da Conta x
    - Conexão com o Github, sempre a partir de um repo vazio x
    - Criação do Dbt Project x
    - Criação do Profile de conexão com o snowflake x
    - Criação do Schema x
    - Criação dos Modelos Base x
    - Criação do Modelo Relacionado x
    - Visualização gráfica do modelo x
    - Teste de execução x
    - Commits, Branches, Pull Requests, Merges no Github x
    - Obtenção do link de conexão com o Airbyte (Coloca o link do repositório git na aba transformation dentro da última conexão no airbyte, para quando finalizar o job rodar a transformação dbt) x


Visualização:

- No Metabase:

    - Conectar Metabase com o Snowflake 
    - Criar uma Question  
    - Criar um Dashboard 
    - Adicionar uma Question 
    - Visualizar o Resultado  


Orquestração:

- No Airflow:

    - Lib para conectar airbyte("apache-airflow-providers-airbyte") no container airlfow (attach shell do airflow-webserver)  - "pip install apache-airflow-providers-airbyte". Após isso restart container airflow webserver e verifica se airbyte está nos tipos de conexão - admin/connections

    - Criar a Docker network  - "docker network create modern-data-stack", para verificar os container dentro dessa rede: "docker network inspect modern-data-stack"

    - Colocar os containers dentro da rede modern-data-stack: "docker network connect modern-data-stack airbyte-proxy" e "docker network connect modern-data-stack airflow-airflow-webserver-1"

    - Criar a connection airbyte_example(host airbyte_proxy e porta 8000)

    - Criar a Dag em airflow/dags

    - Incluir nos composes a network criada

    - Setup Up no serviço

    - Testar a conexao entre os containers do airflow e do airbyte

    - Criar as conexões com o Airbyte através do script  

    - Testar a execução do pipeline  


Encerramento:

- Material de Apoio:

    - Links 

    - Códigos fonte

    - Apresentação
	