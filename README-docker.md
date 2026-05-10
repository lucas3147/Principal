# MENU

- [O que é o docker?](#o-que-é-o-docker)
    - [Na minha máquina funciona](#na-minha-máquina-funciona)
    - [Dependência de ferramentas](#dependência-de-ferramentas)
- [Instalação do docker](#instalação-do-docker)
    - [Testando se realmente está instalado](#testando-se-realmente-está-instalado)
- [Comandos Básicos do docker](#comandos-básicos-do-docker)

## O que é o docker?

É uma plataforma para trabalhar projetos como backend, frontend, em diferentes linguagens (não importa a tecnologia).

### Na minha máquina funciona

Já ouviu a frase: "Na minha máquina funciona" ?

Porque isso acontece ? Muitos motivos, mas pode ser a versão de uma ferramenta que está no seu computador é diferente da versão que está rodando no servidor de hospedagem da sua aplicação.

O docker facilita o processo de implantação, permitindo que a sua aplicação dependa da versão correta da ferramenta que você está utilizando.

### Dependência de ferramentas

O docker permite configurar a aplicação que utiliza uma versão de alguma biblioteca facilmente.

Ponto positivo: Não é preciso instalar necessariamente as bibliotecas na máquina do desenvolvedor, para a aplicação funcionar, tudo está diretamente ligado ao container do Docker, como se fosse uma "máquina virtual" simplificada.

## Instalação do docker

Antes de instalar, é importante saber desses conceitos:

- Docker Desktop: Software com uma interface gráfica visual, para nos auxiliar a criar os containers do docker.

- Docker Engine: É a principal ferramenta, o que precisa ser feita será realizado no docker engine.
    - Docker Compose: Definição de comandos concentradas em um único arquivo YAML.
    - Docker CLI: Comandos no terminal (é importante saber os comandos para hospedagem do docker nos servidores).

Se você estiver windows mais antigo (ex.: windows 7 ou windows 8) provavelmente não irá rodar o docker. Porque o docker precisa de um recurso do windows chamado **WSL 2**. Se não estiver habilitado, pode consultar como habilitar no seguinte link: [Habilitar o WSL](https://learn.microsoft.com/pt-br/windows/wsl/install).

### Testando se realmente está instalado

É necessário usar a variável de ambiente chamada "PATH", ou configurá-la nas variáveis de ambiente do sistema, para executar os comandos do docker.

Verificando se está instalado:

```cmd
docker --version
```

## Comandos básicos do docker

Iniciaremos o estudo com docker com o primeiro container "Hello-World"

### O que é uma Imagem ?

Uma imagem é um modelo de um container

Imagem = Modelo de um container

Um processo de configuração de como um container funciona.

### Comandos

- `docker run <name-image>`: Roda um container pela sua imagem. Ex.: docker run hello-world. O processo "run", procura na máquina local o container "hello-world", se ele não encontra, ele procura pela internet.
- `docker ps`: Lista os containers em execução.
- `docker ps -a`: Lista todos os containers.
- `docker rm <id-container>`: Remove um container pelo seu identificador (id).
- `docker images`: Lista as imagens baixadas.
- `docker rmi <id-image>`: Remove a imagem pelo seu identificador.
- `docker pull <name-image>`: Baixa / Atualiza a última versão de uma imagem.
- `docker stop <id-container>`: Para um container pelo seu identificador.
- `docker run --name <name-container> <name-image>`: Executa um container com um nome específico pela sua imagem. 
- `docker run <name-image>:latest`: Roda um container pela sua imagem utilizando a sua última versão.
- `docker run <name-image>:<number-version>`: Roda um container pela sua imagem utilizando a versão especificada.
- `docker run -it --rm -v ${pwd}:/app -w /app -p 3000:3000 node:18 bash`: (Compatível apenas no **PowerShell**) Cria um container e configura para subir um projeto específico. Veja mais em [primeiro-container-proprio](#explicação-do-comando-primeiro-container-proprio)
- `docker build -t meu-projeto-node .`: Cria e configura uma imagem utilizando o arquivo Dockerfile. Veja mais em [primeira-imagem-dockerfile](#explicação-do-comando-primeira-imagem-dockerfile)
- `docker run -p 3000:3000 --name meu-servidor meu-projeto-node`: Sobe e executa um container com o nome "meu-servidor" utilizando a imagem "meu-projeto-node" com espelhamento de portas do docker para o computador atual.
- `docker build -t meu-projeto-node:v1 .`: Cria e configura uma imagem utilizando o arquivo Dockerfile com uma versão específica chamada v1.
- `docker volume create banco`: Cria um volume nomeado com o nome "banco".
- `docker volume ls`: Lista todos os volumes nomeados criados no docker.
- `docker volume rm banco`: Remove um volume nomeado pelo seu nome, no caso "banco".
- `docker run -v banco:/app/data -p 3000:3000 --name meu-servidor meu-node`: Executa um container "meu servidor" com espelhamento de porta e associa um container ao volume chamado "banco", o volume estará associado a pasta /app/data dentro do container, utilizando a imagem "meu-node".
- `docker run -v ${pwd}:/app -p 3000:3000 --name meu-servidor meu-node`: Cria um container com bind mount associado na pasta :/app dentro do container com espelhamento de porta, nome "meu-servidor" utilizando a imagem "meu-node".
- `docker network ls`: Lista todas as redes do host.
- `docker network create [nome-rede]`: Cria uma nova rede Docker.
- `docker run -p 3000:3000 --network rede-xyz --name frontend meu-node`: Sobe um container com espelhamento de porta do host "3000", utilizando a rede "rede-xyz", com o nome "frontend", na imagem "meu-node"
- `docker run -p 4000:3000 -p 4001:5000 --name meu-server meu-node`: Subindo um container com múltiplos espelhamento de portas com o nome "meu-server" e imagem "meu-node".
- `docker run -p 3000:3000 -e AUTHOR=l.lima --name meu-server meu-node`: Subindo um container com espelhamento de porta, utilizando uma variável de ambiente chamada AUTHOR com valor "l.lima", o container possui o nome "meu-server" e imagem "meu-node". 
- `docker run --env-file .env -p 3000:3000 --name meu-server meu-node`: Sobe um container com um arquivo de ambiente ".env" do node (só funciona se o arquivo estiver na pasta do projeto)

## Explorando o DockerHub

É um repositório de imagens online do Docker. 
Existem imagens maliciosas, é necessário ter certo receio antes de baixar qualquer coisa no seu computador.

- [docker-hub](https://hub.docker.com/)

## Criando seu primeiro container com Node.js

Antes de mais nada navegue até a pasta do seu projeto.

Após isso, rode o comando:

- `docker run -it --rm -v ${pwd}:/app -w /app -p 3000:3000 node:18 bash`: PowerShell
- `docker run -it --rm -v ${PWD}:/app -w /app -p 3000:3000 node:18 bash`: Linux
- `docker run -it --rm -v %cd%:/app -w /app -p 3000:3000 node:18 bash`: CMD

### Explicação do comando primeiro-container-proprio:

- `-it` - Você consegue usar o container como se fosse um terminal normal.
- `--rm` - Remove o container automaticamente quando você sair.
- `-v ${pwd}:/app` - Especifica para o docker onde você quer colocar os arquivos de projeto no container.
- `-w /app` - Depois de criar a pasta no container, acesse a pasta /app.
- `-p 3000:3000` - Espelhamento de porta do container para a porta do computador atual.
- `node:18` - Especifica a imagem e versão dela (se não tiver na máquina puxa do docker-hub)
- `bash` - Após criar o container, pede acesso para incluir comandos Linux dentro do terminal do container.

## Introdução ao Dockerfile

É um arquivo de configuração do docker paa não precisar digitar comandos toda vez que subir um ambiente para o container.

Exemplo de uso:

Nome do arquivo: **Dockerfile**
```
FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

**Explicação comandos dockerfile**

- `FROM <imagem>:<versao>` - Utilize a imagem com a versão especificada.
- `WORKDIR /app` - Crie e configure uma pasta dentro do contaner pelo caminho "/app"
- `COPY <origem> <origem>` - copiar arquivos da sua máquina para dentro da imagem Docker.
- `EXPOSE 3000` - Exporte a porta 3000 do docker para espelhamento (posteriormente).
- `CMD ["npm", "start"]` - Comandos do prompt utilizados dentro do contexto do container, expressos em array de string.

Feito a primeira configuração dentro do arquivo, iremos criar uma imagem própria para utilizar esse arquivo de configuração para rodar o nosso projeto. Na prática, é uma imagem que utiliza o node com as minhas configurações.

### Explicação do comando primeira-imagem-dockerfile

Primeiro, navegue até a pasta do seu projeto, depois execute:

- `docker build -t meu-projeto-node .`

Explicação:

- `docker build`: O comando build manda o Docker construir uma imagem, ele lê as instruções do arquivo **Dockerfile**.
- `-t meu-projeto-node`: O parâmetro -t especifica o nome da imagem.
- `.`: O ponto significa: "Use a pasta atual como contexto da build.

**Observação**

```
Depois de utilizar esse comando, toda vez que alterar o código do seu projeto, precisa dar um build na imagem, porque ela não atualiza sozinha. 

Caso o container já exista, é necessário criar um novo, para utilizar a nova versão da imagem.

Os containers são criados com um tipo de versão das imagens, mesmo que essa versão não exista na máquina, pois foram atualizada com o build.
```

## Boas práticas no Dockerfile

Boas práticas:

- Realizar comandos sequenciais, ordem correta:
    - 1° - Pegar os arquivos de projeto e colocar dentro do container.
    - 2° - Comandos para configurar arquivos dentro do container.
    - 3° - Roda o projeto.

Além disso, utilizamos um arquivo chamado **.dockerignore**

### .DOCKERIGNORE

É um arquivo do docker para ignorar arquivos temporários na pasta do seu projeto, o docker utiliza esse arquivo para excluir arquivos quando você utiliza o comando: **COPY <origem> <destino>**.

Exemplo do conteúdo .dockerignore:

```
node_modules
npm-debug.log
.git
.env
```

## Trabalhando com volumes 1

Utilizar volumes no docker significa disponibilizar espaço no HD do computador/servidor para armazenar as aplicações.

Utilização:

- Os container após excluidos todos os dados presentes nele serão excluidos automaticamente, para evitar isso, utilizamos os volumes que são locais onde são armazenado informações.

**Existem dois tipos de volumes**

1. Volume nomeado:
    - Gerenciado pelo próprio docker
    - Utlizado em: Banco de dados, uploads
    - Mais de um container pode utilizar o mesmo volume

2. Bind Mounts:
    - Associa uma pasta do PC Local (Host) à uma pasta dentro do container.
    - O que coloca de informação nessa pasta do Host, vai aparecer no container, e vice-versa.
    - Utilizado em Ambientes de desenvolvimento - Com isso não é necessário dar um build na imagem e depois criar um container novo.

## Trabalhando com volumes 2

**Bind Mounts**

Bind Mounts são criados no momento que executo um container pela sua imagem.

Ele cria um vínculo entre a pasta do computador que está rodando o docker (host) e a pasta do container.

### Explicação do comando meu-primeiro-bind-mount

- `docker run -v ${pwd}:/app -p 3000:3000 --name meu-servidor meu-node`

Explicação:

- `-v ${pwd}:/app`: monta uma pasta da máquina dentro do container.
    - Síntaxe: `-v origem:destino`
    - `${pwd}` -> diretório atual
    - `/app`   -> pasta principal do container

### Pequeno problema

Arquivos salvos na pasta influenciam no container, porém, em projetos como o node por exemplo, o fato de salvar o arquivo, não significa que o arquivo será atualizado automaticamente no navegador, porque o servidor node continua rodando mesmo após o arquivo ser alterado no ambiente de desenvolvimento. 

**Para puxar o arquivo ajustado, digite os comandos**

- `docker stop meu-servidor`
- `docker start meu-servidor`

O container vai utilizar os arquivos da pasta roteada.

### Melhorando o Dockerfile (com projeto Node)

Remova os containers utilizando a imagem do node versão 18.

Na versão 20 em diante, o node possui um comando chamado --watch

- `"dev": "node --watch index.js"`

É um comando utilizando para o Node monitorar o arquivo chamado index.js`

Dockerfile

```
FROM node:22

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "run", "dev"]
```

## Redes no Docker

A partir de agora, vamos aprender como realizar a comunicação entre um container e outro.

Vamos supor, dois projetos em containers diferentes:

```
Container 1: Projeto rodando em Node
Container 2: Banco de dados MySQL
```

Eu preciso que o container 1 se comunique com o container 2.

### Rede padrão dos containers: Bridge

Todos os containers por padrão estarão numa rede chamada Bridge.

**Todos os containers dentro da mesma rede, tem acessos um ao outro.**

### Como se conectar em containers diferentes ?

**Exemplo 1:**

```
Container 1: projeto -> Projeto rodando em Node - rede Bridge
Container 2: banco -> Banco de dados MongoDB - porta 27017 - rede Bridge
```

Para realizar a comunicação entre eles, algo parecido com isso:

```
Container 1 -> mongodb://banco:27017
```

**Exemplo 2:**

```
Container 1: frontend -> Projeto rodando em React -> Rede ProjetoXYZ
Container 2: backend -> Projeto rodando em Python -> Rede ProjetoXYZ
```
"
Comunicação:

```
http://backend/api/test
```

Se o container backend estivesse com a porta 5000, ficaria assim:

```
http://backend:5000/api/test
```

## Expondo portas e entendendo -p

Primeiro de tudo, o "EXPOSE: 3000" no Dockerfile, não tem um efeito prático, mas apenas para efeito de documentação do projeto.

O que importa de fato é o `-p` na hora de subir o container.

Vejamos o comando:

- `docker run -p 4000:3000 --name meu-server meu-node`

A porta 4000 é a porta do host.
A porta 3000 é a porta do container.
Todo o trafego que acontecer na porta 4000 do meu pc, manda para a porta 3000 do container.

### Como usar mais de uma porta no mesmo container?

Em aplicações complexas, pode ser necessário utilizar mais de uma aplicação rodando em paralelo, e por serem independentes, terão portas distintas.

Com isso podemos, ter mais de um espelhamento de portas do host para o mesmo container.

Como fazer ?
- Use vários **-p**

```
docker run -p 4000:3000 -p 4001:5000 --name meu-server meu-node
```

## Variáveis de ambiente em Container

Na hora de criar o container, você pode definir variáveis de ambiente, e dentro do container você pode usar essas variáveis para você fazer o que quiser.

**Comando:**

- `docker run -p 3000:3000 -e AUTHOR=l.lima --name meu-server meu-node`: Explicação do comando em [Comandos Básicos do docker](#comandos-básicos-do-docker)

**Como acessar no projeto Node ?**

```js
const author = process.env.AUTHOR;
```

**Especificar um arquivo onde estão as variáveis de ambiente:**

Crie um arquivo chamado .env na pasta do seu projeto.

Depois rode o comando:

- ``: Veja a explicação em [Comandos Básicos do docker](#comandos-básicos-do-docker)

