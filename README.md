# Black Burguer

Os pedidos são gravados em um banco SQLite no servidor. O arquivo do banco é
criado automaticamente no primeiro início do servidor; não é necessário instalar
um driver nem configurar outro serviço.
Os dados de pedidos e seus status ficam no SQLite; o controle de estoque continua
no `localStorage` do navegador, como antes.

## Executar com Docker

Na pasta do projeto, execute:

```sh
docker compose up --build
```

Acesse `http://localhost:8080`. O banco fica no volume Docker `pedidos-data` e
continua existindo após reiniciar ou recriar o contêiner. Para parar o serviço,
execute `docker compose down`; não remova o volume se quiser manter os pedidos.

## Executar sem Docker

Com Python 3 instalado, execute na pasta do projeto:

```sh
python server.py
```

Acesse `http://localhost:8080`. O SQLite será criado em `data/pedidos.sqlite3`.
Para escolher outra pasta para os dados, defina a variável `BB_DATA_DIR` antes
de iniciar o servidor.

Abra o site pelo endereço do servidor. Abrir `index.html` diretamente como um
arquivo (`file://`) não inicia a API e não permite gravar pedidos.

> **Atenção:** a API ainda não possui autenticação. Não a exponha à internet
> pública; os registros incluem nome e endereço dos clientes.
# blackbg
