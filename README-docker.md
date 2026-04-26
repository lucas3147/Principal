# MENU

- [O que é o docker?](#o-que-é-o-docker)
    - [Na minha máquina funciona](#na-minha-máquina-funciona)
    - [Dependência de ferramentas](#dependência-de-ferramentas)
- [Instalação do docker](#instalação-do-docker)
    - [Testando se realmente está instalado](#testando-se-realmente-está-instalado)
- [Comandos Básicos do docker](#comandos-básicos-do-docker)
    - [comando docker run <container>](#comando-docker-run)
    - [comando docker ps](#comando-docker-ps)
    - [comando docker ps -a](#comando-docker-ps--a)
    - [comando docker rm](#comando-rm)

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

### comando docker run <image>

Comando utilizado para rodar um container pela sua imagem.

```cmd
docker run hello-world
```

O processo "run", procura na máquina local o container "hello-world", se ele não encontra, ele procura pela internet.

Run Container

```
    comando -> máquina local / internet (download do container)
```

### comando docker ps

Comando utilizado para listar os containers em execução

### comando docker ps -a

Comando utilizado para listar todos os containers

### comando rm <id-container>

Remove um container pelo seu identificador (id)

### comando docker images

Lista as imagens

### comando docker rmi <uid-images>

Remove a imagem pelo seu identificador

### O que é uma Imagem ?

Uma imagem é um modelo de um container

Imagem = Modelo de um container

Um processo de configuração de como um container funciona.