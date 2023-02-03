---
lab:
    title: '03 - Instalando o Helm (Linux)'
    module: 'Preparando o ambiente'
---

# Lab 03 - Instalando o Helm (Linux)

# Laboratório do aluno

## Cenário de laboratório

Instalação do Helm no linux para realizar demais atividades do curso.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: Instalando pré-requesitos
+ Tarefa 2: Instalando o Helm

## Estimated timing: 10 minutes

## Instruções

#### Tarefa 1: Instalando pré-requesitos

Nesta tarefa, você irá instalar os pré-requisitos para a instalação do docker.

1. Faça login no linux com um usuário que tenha acesso administrativo.

1. Execute os comandos abaixo para atualizar a lista de pacotes disponíveis para instalação.

    ```shell
    sudo apt update
    ```

1. Execute os comandos abaixo para instalar pré-requesitos.

    ```shell
    sudo apt install -y curl wget apt-transport-https
    ```

1. Execute os comandos abaixo para adicionar a chave do repositório oficial do Helm.

    ```shell
    curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
    ```

1. Execute os comandos abaixo para adicionar o repositório oficial do Helm na lista de repositórios do Linux.

    ```shell
    echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee
/etc/apt/sources.list.d/helm-stable-debian.list
    ```

#### Tarefa 2: Instalando o Helm

Nesta tarefa, você irá instalar o minikube.

1. Execute os comandos abaixo para atualizar a lista de pacotes dos repositórios.

    ```shell
    sudo apt update
    ```

1. Execute os comandos abaixo para instalar o Helm.

    ```shell
    sudo apt-get install -y helm
    ```

1. Execute os comandos abaixo para validar instalação do Helm.

    ```shell
    helm version
    ```

#### Revisão

Neste laboratório, você fez:

- Instalação dos pré-requesitos necessários para a instalação do minikube
- Instalação do Helm