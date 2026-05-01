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
- `docker run -it --rm -v ${pwd}:/app -w /app -p 3000:3000 node:18 bash`: (Compatível apenas no **PowerShell**) Cria um container e configura para subir um projeto específico. Veja mais em 

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

Explicação do comando:

- `-it` - Você consegue usar o container como se fosse um terminal normal.
- `--rm` - Remove o container automaticamente quando você sair.
- `-v ${pwd}:/app` - Especifica para o docker onde você quer colocar os arquivos de projeto no container.
- `-w /app` - Depois de criar a pasta no container, acesse a pasta /app.
- `-p 3000:3000` - Espelhamento de porta do container para a porta do computador atual.
- `node:18` - Especifica a imagem e versão dela (se não tiver na máquina puxa do docker-hub)
- `bash` - Após criar o container, pede acesso para incluir comandos Linux dentro do terminal do container.