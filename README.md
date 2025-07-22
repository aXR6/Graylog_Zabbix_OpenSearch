# Graylog_Zabbix_OpenSearch

Este repositório contém exemplos de `docker-compose` para implantações do **Graylog** e **Zabbix**.

## Utilização

1. Copie os arquivos `.env.example` presentes em cada diretório (`Graylog` e `Zabbix`) para `.env`:

   ```bash
   cp Graylog/.env.example Graylog/.env
   cp Zabbix/.env.example Zabbix/.env
   ```

2. Ajuste os valores conforme o seu ambiente.
3. Dentro de cada pasta execute `docker-compose up -d` para iniciar os containers.

Os arquivos `.env` armazenam informações sensíveis, como credenciais de banco de dados, e por isso estão listados no `.gitignore`.

## Solução de problemas

Se o serviço **mongo** não iniciar e os logs exibirem uma mensagem semelhante a:

```
Unable to read the storage engine metadata file
```

remova os volumes criados anteriormente para que o contêiner possa inicializar
com um diretório de dados limpo. Execute:

```bash
docker-compose down -v
docker-compose up -d
```

Isso recria o volume `mongo_data` utilizado pelo MongoDB e normalmente resolve o
erro.
