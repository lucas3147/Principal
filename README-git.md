# MENU

- [Repositórios GitHub](#repositórios-github)
    - [Web LLM](#web-llm)
    - [Code InterView University](#code-interview-university)
    - [Tech Interview Handbook](#tech-interview-handbook)
    - [Build your own X](#build-your-own-x)
    - [Real World](#real-world)
- [Comandos GitHub](#comandos-git)
    - [Visite o site](#1-visite-o-site)
    - [Configuração](#2-configuração)
    - [Criação e Clonagem de Repositórios](#3-criação-e-clonagem-de-repositórios)
    - [Controle de Versão](#4-controle-de-versão)
    - [Branching e Merging](#5)
    - [Inspeção e Comparação](#6-inspeção-e-comparação)
    - [Atualização e Publicação](#7-atualização-e-publicação)
    - [Desfazendo Alterações](#8-desfazendo-alterações)
    - [Alteração entre Ramos](#9-alteração-entre-ramos)

## Repositórios GitHub

### Web LLM

- [Acesse aqui](https://github.com/mlc-ai/web-llm)

**Descrição:**

```

```

### Code InterView University

- [Acesse aqui](https://github.com/jwasham/coding-interview-university/blob/main/translations/README-ptbr.md)

**Descrição:**

```

```

### Tech Interview Handbook

- [Acesse aqui](https://github.com/yangshun/tech-interview-handbook)

**Descrição:**

```

```

### Build your own X

- [Acesse aqui](https://github.com/yangshun/tech-interview-handbook)

**Descrição:**

```

```

### Real World

- [Acesse aqui](https://github.com/gothinkster/realworld)

**Descrição:**

```

```

## Comandos GIT

Este documento fornece uma lista dos principais comandos Git e suas descrições.

### Índice

1. [Visite o site](#1-visite-o-site)
2. [Configuração](#configuracao)
3. [Criação e Clonagem de Repositórios](#criacao-e-clonagem-de-repositorios)
4. [Controle de Versão](#controle-de-versao)
5. [Branching e Merging](#branching-e-merging)
6. [Inspeção e Comparação](#inspecao-e-comparacao)
7. [Atualização e Publicação](#atualizacao-e-publicacao)
8. [Desfazendo Alterações](#desfazendo-alteracoes)

### 1. Visite o site

- [gitfluence](https://www.gitfluence.com/): Fornece comandos a partir da linguagem natural do ser humano. 

### 2. Configuração

- `git config --global user.name "Seu Nome"`: Define o nome do usuário para todos os repositórios no sistema.
- `git config --global user.email "seu.email@example.com"`: Define o e-mail do usuário para todos os repositórios no sistema.
- `git config --list`: Lista todas as configurações do Git.

### 3. Criação e Clonagem de Repositórios

- `git init`: Inicializa um novo repositório Git.
- `git clone <url>`: Clona um repositório existente de um URL.

### 4. Controle de Versão

- `git status`: Exibe o estado das alterações no repositório.
- `git add <arquivo>`: Adiciona um arquivo ao staging area.
- `git add .`: Adiciona todos os arquivos modificados ao staging area.
- `git commit -m "mensagem"`: Faz um commit das alterações com uma mensagem descritiva.
- `git commit -a`: Faz um commit de todas as alterações rastreadas.

### 5. Branching e Merging

- `git branch`: Lista todas as branches no repositório.
- `git branch <nome-da-branch>`: Cria uma nova branch.
- `git checkout <nome-da-branch>`: Troca para a branch especificada.
- `git merge <nome-da-branch>`: Mescla a branch especificada na branch atual.
- `git branch -d <nome-da-branch>`: Deleta a branch especificada.

### 6. Inspeção e Comparação

- `git log`: Exibe o histórico de commits.
- `git log --oneline`: Exibe o histórico de commits em uma linha.
- `git diff`: Mostra as diferenças entre os arquivos não comitados e o repositório.
- `git diff <branch1> <branch2>`: Mostra as diferenças entre duas branches.

### 7. Atualização e Publicação

- `git fetch`: Baixa objetos e referências do repositório remoto.
- `git pull`: Baixa e integra mudanças do repositório remoto na branch atual.
- `git push`: Envia commits para o repositório remoto.

### 8. Desfazendo Alterações

- `git reset <arquivo>`: Remove um arquivo do staging area.
- `git reset --hard`: Reseta o índice e a árvore de trabalho para o último commit.
- `git revert <commit>`: Reverte um commit específico, criando um novo commit que desfaz as mudanças.

### 9. Alteração entre Ramos

- `git rebase <main>`: Re-aplicar commits de uma branch sobre outra.
- `git rebase -i <main>`: Rebase interativo.

Este é um guia básico com os comandos mais comuns. Existem muitos outros comandos e opções no Git para funcionalidades mais avançadas.
