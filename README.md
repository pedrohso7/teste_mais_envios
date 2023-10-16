<p align="middle">
<img alt="teste banner" src="https://github.com/pedrohso7/teste_mais_envios/assets/32853995/9bd8a03e-e7b3-4077-9040-14daa044eefa" width="600"/>
</p>

         
<p align="center">
  <a href="#-O projeto">O projeto</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Tecnologias">Tecnologias</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Visão-Geral">Visão Geral</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Executando">Executando</a>
  &nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-Comece-a-Usar">Comece a Usar</a>
</p>

## ✦ O projeto
<h4>Objetivos</h4>
<p align="justify">
O objetivo do teste é construir uma API REST que deverá atender os seguintes critérios:
<ul>
<li>Receberá uma planilha de etiquetas (diretório root), que deverá ser processada em background.</li>
<li>Não precisa conectar um banco de dados as informações podem ficar em memória</li>
<li>Seja possível visualizar, atualizar e apagar as etiquetas via API Rest.</li>
</ul>

<h4>Critérios</h4>
Em critérios de tecnologia, é esperado:
<ul>
<li>Teste seja feito em NodeJS</li>
<li>Versionar o código no Github ou Gitlab</li>
<li>Json</li>
<li>REST</li>
<li>Documentação de código</li>
</ul>
</p>

<h4>Autor:</h4>
<ul>
<li>Pedro Oliveira</li>
</ul>

## ✦ Tecnologias
O projeto foi criado utilizando as tecnologias abaixo:
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
<img alt="RabbitMQ workflow" src="https://github.com/pedrohso7/teste_mais_envios/assets/32853995/4e1f7acc-d810-4522-a46f-28bb7a471a78" width="800"/>
</p>

A API Rest desenvolvida exerce o papel de publisher para vários micro serviços mas, neste caso, só existe um, o processador de arquivos. A API publica os dados do arquivo enviado utilizando a fila "spreadsheet_exchange", que será consumida pelo micro serviço, o consumer. Este, por sua vez, recebe o arquivo e processa a planilha, retornando todas as etiquetas extraídas.

## ✦ Executando
<h4>Configurando o repositório</h4>
<p align="justify">
Primeiro, é necessário que você clone o repositório e, em seguida, se certifique de estar na raíz do projeto:
</p>

```
cd teste_mais_envios
```
<p align="justify">
Esse repositório clonado é a raíz dos nossos dois projetos, que foram adicionados através dos submódulos do git. Em outras palavras, agora é necessário "clonar" o restante do projeto utilizando os comandos abaixo:
</p>

```git submodule init```

<p align="justify">
Em seguida:
</p>

```git submodule update```

<h4>Executando</h4>
<p align="justify">
Caso nao tenha o Docker e o Docker Compose já instaládos:
</p>

<ul>
<li>Acesse o link clicando <a href="https://docs.docker.com/engine/install/">aqui</a> para instalação do Docker.</li>
<li>Acesse o link <a href="https://docs.docker.com/compose/install/">aqui</a> para a instalação do docker compose.</li>
</ul>

<p align="justify">
Após a instalação das dependências, execute o comando abaixo para executar o sistema:
</p>

```
docker-compose up
```

<p align="justify">
Aguarde a execução e, quando finalizada, o servidor estará ativo em "localhost:3000".
</p>

## ✦ Comece a Usar

<p align="justify">
Para acessar a documentação do sistema, https://docs.docker.com/compose/install/primeiro execute-o seguindo o tutorial de execução e clique <a href="http://localhost:3000/api">aqui</a> para o acesso ao Swagger
</p>

<p align="justify">
Os endpoints disponíveis são:
</p>

<ul>
<br>Upload: <pre>POST: /tags/upload</pre></br>
<br><li>Create: <pre>POST: /tags</pre></li></br>
<br><li>Update: <pre>PATCH: /tags/:id</pre></li></br>
<br><li>GetAll: <pre>GET: /tags</pre></li></br>
<br><li>GetOne: <pre>GET: /tags/:id</pre></li></br>
<br><li>Delete: <pre>DELETE: /tags/:id</pre></li></br>
</ul>
