![poketroca_logo](https://github.com/pedrohso7/teste_mais_envios/assets/32853995/9bd8a03e-e7b3-4077-9040-14daa044eefa)

         
<p align="center">
  <a href="#-O projeto">O projeto</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Tecnologias">Tecnologias</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Visão Geral">Visão Geral</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-poketroca-usecase-views">PokeTroca UseCase Views</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Executando">Executando</a>
</p>

## ✦ O projeto
<p align="justify">
O objetivo do teste é construir uma API REST que deverá atender os seguintes critérios:
<ul>
<li>Receberá uma planilha de etiquetas (diretório root), que deverá ser processada em background.</li>
<li>Não precisa conectar um banco de dados as informações podem ficar em memória</li>
<li>Seja possível visualizar, atualizar e apagar as etiquetas via API Rest.</li>
</ul>

Em critérios de tecnologia, é esperado:
<ul>
<li>Teste seja feito em NodeJS</li>
<li>Versionar o código no Github ou Gitlab</li>
<li>Json</li>
<li>REST</li>
<li>Documentação de código</li>
</ul>
</p>

<p align="justify">
Authors:
</p>
<ul>
<li>Pedro Oliveira</li>
</ul>

## ✦ Tecnologias
This O projeto was made using the tecnologies below:
- [NodeJs](https://nodejs.org/en)
- [NestJs](https://nestjs.com/)
- [Docker](https://www.docker.com/)
- [RabbitMQ](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html?gclid=CjwKCAjwvrOpBhBdEiwAR58-3O1p9B8pD2zkwC9NVNYvtpPdatfvHeF5jzb3jih2DTDnsmKdnw4bLRoCGbcQAvD_BwE)

## ✦ Visão Geral
<p align="justify">
O projeto foi escrito utilizando o framework NestJS, dividindo o projeto em duas partes (dois repositórios). Um para a API Rest, responsável por lidar com todas as operações do sistema. E o outro repositório para um micro serviço cuja a função é receber um arquivo no formato de planilha, processar e retornar os respectivos valores. 
</p>

<p align="justify">
O sistema foi distribuído utilizando o workflow padrão do rabbitQM, onde existem dois tipos de entidade, o publisher e o consumer: 
</p>

<p align="middle">
<img alt="RabbitMQ workflow" src="https://github.com/pedrohso7/teste_mais_envios/assets/32853995/4e1f7acc-d810-4522-a46f-28bb7a471a78" width="450"/>
</p>

A API Rest desenvolvida exerce o papel de publisher para vários micro serviços mas, neste caso, só existe um, o processador de arquivos. A API publica os dados do arquivo enviado utilizando a fila "spreadsheet_exchange", que será consumida pelo micro serviço, o consumer. Este, por sua vez, recebe o arquivo e processa a planilha, retornando todas as etiquetas extraídas.

## ✦ Executando
<p align="justify">
Primeiro, é necessário que você clone o repositório e, em seguida, se certifique de estar na raíz do projeto:
</p>

```
cd teste_mais_envios
```

<p align="justify">
Caso nao tenha o Docker e o Docker Compose já instaládos:
</p>

<ul>
<li>Acesse o link clicando <a href="https://docs.docker.com/engine/install/">aqui</a> para instalação do Docker.</li>
<li>Acesse o link <a href="https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04">aqui</a> para a instalação do docker compose.</li>
</ul>

<p align="justify">
Após a instalação das dependẽncias, execute o comando para executar o sistema
</p>

```
docker-compose up
```

<p align="justify">
Aguarde a execução e, quando finalizada, o servidor estará ativo em "localhost:3000".
</p>
## ✦ Comece a usar

<p align="justify">
Para acessar a documentação do sistema, primeiro execute-o seguindo o tutorial de execução e clique <a href="http://localhost:3000/api">aqui</a> para o acesso ao Swagger
</p>

<p align="justify">
Os endpoint disponíveis são:
</p>

<ul>
<li>Upload: ```POST: /hang-tags/upload```</li>
<li>Create: ```POST: /hang-tags```</li>
<li>Update: ```PATCH: /hang-tags/:id```</li>
<li>GetAll: ```GET: /hang-tags```</li>
<li>GetOne: ```GET: /hang-tags/:id```</li>
<li>Delete: ```DELETE: /hang-tags/:id```</li>
</ul>
