---
lab:
    title: '05 - Repositório remoto'
    module: 'Usando o Helm'
---

# Lab 05 - Trabalhando com repositório remoto

# Laboratório do aluno

## Cenário de laboratório

Trabalhando com repositórios remoto.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Utilizando o comando `helm repo`

## Estimated timing: 10 minutes

## Instruções

#### Tarefa 1: [Opcional] Iniciando os serviços

Nesta tarefa, você irá utilizar comandos para iniciar o docker e o minikube.

1. Faça login no linux com um usuário que tenha acesso administrativo.

1. Execute os comandos abaixo para iniciar o serviço do docker.

    ```shell
    systemctl start docker
    ```

1. Execute os comandos abaixo para iniciar o kinikube.

    ```shell
    minikube start --driver=docker
    ```

#### Tarefa 2: Utilizando o comando `helm repo`

Nesta tarefa, você irá utilizar o comando `helm repo` para manipular repositórios remotos.

1. Execute os comandos abaixo para listar os repositórios conhecidos pelo Helm.

    ```shell
    helm repo list
    ```

1. Execute os comandos abaixo para adicionar um repositório na lista de repositórios conhecidos pelo Helm.

    ```shell
    helm repo add bitnami https://charts.bitnami.com/bitnami
    ```

1. Execute os comandos abaixo para listar os repositórios e veja que foi adicionado um repositório.

    ```shell
    helm repo list
    ```

1. Execute os comandos abaixo para atualizar a lista de chart dos repositórios remotos.

    ```shell
    helm repo update
    ```

1. Execute os comandos abaixo para remover um repositório da lista de repositórios conhecidos pelo Helm.

    ```shell
    helm repo remove bitnami
    ```

1. Execute os comandos abaixo para listar os repositórios conhecidos pelo Helm.

    ```shell
    helm repo list
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou o comando `helm repo` para manipular os repositórios