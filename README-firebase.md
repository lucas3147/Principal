# MENU

- [Comandos Firebase](#comandos-firebase)
    - [Autenticação](#autenticação)
    - [Projeto](#projeto)
    - [Emuladores](#emuladores)
    - [Instalação e Atualização](#instalação-e-atualização)
    - [PowerShell](#powershell)

## Autenticação

- `firebase login`: Autentica sua conta do Google no Firebase CLI, permitindo que você interaja com seus projetos Firebase.
- `firebase logout`: Desconecta sua conta do Firebase CLI.
- `firebase logout --all`: Remove todas as credenciais armazenadas do Firebase CLI, permitindo que você faça login novamente com uma conta diferente, se necessário.

## Projeto

- `firebase init`: Inicializa um novo projeto Firebase no diretório atual, permitindo que você configure recursos como Firestore, Hosting, Functions, etc.
- `firebase projects:list`: Lista todos os projetos Firebase disponíveis na sua conta.
- `firebase use <project-id>`: Seleciona um projeto Firebase específico para o ambiente atual, onde <project-id> é o ID do projeto.

## Emuladores

- `firebase emulators:start --only firestore`: Inicia o emulador local do Firestore, permitindo que você teste suas interações com um banco de dados Firestore simulado.

## Instalação e Atualização

- `npm install -g firebase-tools`: Instala ou atualiza a CLI do Firebase globalmente no seu sistema.

## PowerShell

- `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`: (PowerShell) Permite a execução de scripts no PowerShell, necessário para rodar comandos do Firebase CLI no Windows (deve ser executado como administrador).