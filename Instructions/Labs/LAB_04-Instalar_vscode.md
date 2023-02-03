---
lab:
    title: '04 - Instalando o VSCode (Linux)'
    module: 'Preparando o ambiente'
---

# Lab 04 - Instalando o VSCode (Linux)

# Laboratório do aluno

## Cenário de laboratório

Instalação do VSCode no linux para realizar demais atividades do curso.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: Instalando pré-requesitos
+ Tarefa 2: Instalando o VSCode

## Estimated timing: 10 minutes

## Instruções

#### Tarefa 1: Instalando pré-requesitos

Nesta tarefa, você irá instalar os pré-requisitos para a instalação do docker.

1. Faça login no linux com um usuário que tenha acesso administrativo.

1. Execute os comandos abaixo para atualizar a lista de pacotes disponíveis para instalação.

    ```shell
    sudo apt update
    ```

1. Execute os comandos abaixo para adicionar a chave GPG do repositório da Microsoft.

    ```shell
    wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add
    ```

1. Execute os comandos abaixo para adicionar o repositório do VsCode na lista de repositórios.

    ```shell
    sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode
stable main"
    ```

#### Tarefa 2: Instalando o VSCode

Nesta tarefa, você irá instalar o VSCode.

1. Execute os comandos abaixo para atualizar a lista de pacotes dos repositórios.

    ```shell
    sudo apt update
    ```

1. Execute os comandos abaixo para instalar o VSCode.

    ```shell
    sudo apt install -y code
    ```

#### Revisão

Neste laboratório, você fez:

- Instalação dos pré-requesitos necessários para a instalação do minikube
- Instalação do VSCode