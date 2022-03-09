# rotten-potatoes

## Configuração

MONGODB_DB => Nome do database

MONGODB_HOST => Host do MongoDB

MONGODB_PORT => Posta de acesso ao MongoDB

MONGODB_USERNAME => Usuário do MongoDB

MONGODB_PASSWORD => Senha do MongoDB

## Docker

1) Foi criado o arquivo Dockerfile para a aplicação Python.

2) Foi criado o arquivo docker-compose.yaml com configuração para criar o container mongodb e da aplicação Python.
    - Criei um volume para ser utilizado no container do mongodb e não perder os dados caso destrua os containers
    - Criei uma network para ser utilizada pela aplicação e o mongodb, e eles conseguirem ser acessíveis entre si
    - Defini o service chamado app que seria a aplicação Python
      - Defini o nome da imagem da aplicação a ser utilizada
      - Especifiquei de onde utilizar o Dockerfile para criação da imagem
      - Expus a aplicação na porta 8080
      - Especifiquei a rede a ser utilizada (rotten_network)
      - Informamos que o container deve ser construído após a construção do container mongodb
      - Especifiquei as variáveis de ambiente que a aplicação utiliza
    - Defini o service chamado mongodb
      - Defini o nome da imagem do mongo a ser utilizada
      - Expus o mongo na porta default (27017)
      - Especifiquei a rede a ser utilizada (rotten_network)
      - Fiz o mapeamento o volume
      - Especifiquei as variáveis de ambiente (MONGO_INITDB_ROOT_USERNAME, MONGO_INITDB_ROOT_PASSWORD)

3) Para executar a aplicação utilizando o docker-compose, execute:
    `docker-compose up -d`

    Caso precise reconstruir a imagem inclua o argumento `--build`

4) Para parar a execução dos containers:
    `docker-compose down`