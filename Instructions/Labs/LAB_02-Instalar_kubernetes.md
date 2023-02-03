---
lab:
    title: '02 - Instalando o Kubernetes (Linux)'
    module: 'Preparando o ambiente'
---

# Lab 02 - Instalando o Kubernetes (Linux)

# Laboratório do aluno

## Cenário de laboratório

Instalação do Kubernetes no linux para realizar demais atividades do curso.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: Instalando pré-requesitos
+ Tarefa 2: Instalando o minikube
+ Tarefa 3: Instalando o kubectl

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

#### Tarefa 2: Instalando o minikube

Nesta tarefa, você irá instalar o minikube.

1. Execute os comandos abaixo para fazer o download da última versão do minikube.

    ```shell
    wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    ```

1. Execute os comandos abaixo para copiar binário para diretório do sistema.

    ```shell
    sudo cp minikube-linux-amd64 /usr/local/bin/minikube
    ```

1. Execute os comandos abaixo para transformar o binário em executável.

    ```shell
    sudo chmod +x /usr/local/bin/minikube
    ```

1. Execute os comandos abaixo para verificar versão.

    ```shell
    minikube version
    ```

1. Execute os comandos abaixo para iniciar o kinikube.

    ```shell
    minikube start --driver=docker
    ```

1. Execute os comandos abaixo para verificar o status do minikube.

    ```shell
    minikube status
    ```
#### Tarefa 3: Instalando o kubectl

Nesta tarefa, você irá instalar o kubectl.

1. Execute os comandos abaixo para fazer o download da última versão do kubectl.

    ```shell
    curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s
https://storage.googleapis.com/kubernetesrelease/release/stable.txt`/bin/linux/amd64/kubectl
    ```

1. Execute os comandos abaixo para copiar binário para diretório do sistema.

    ```shell
    sudo mv kubectl /usr/local/bin/
    ```

1. Execute os comandos abaixo para transformar o binário em executável.

    ```shell
    sudo chmod +x /usr/local/bin/kubectl
    ```

1. Execute os comandos abaixo para verificar versão.

    ```shell
    kubectl version -o yaml
    ```

#### Revisão

Neste laboratório, você fez:

- Instalação dos pré-requesitos necessários para a instalação do minikube
- Instalação do minikube
- Instalação do kubectl