---
lab:
    title: '07 - Removendo pacote'
    module: 'Usando o Helm'
---

# Lab 07 - Removendo pacote

# Laboratório do aluno

## Cenário de laboratório

Removendo um pacote.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Instalar um pacote

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

#### Tarefa 2: Removendo um pacote

Nesta tarefa, você irá remover o pacote instalado no [laboratório 06](/Instructions/Labs/LAB_06-instalando_pacote.md).

1. Execute os comandos abaixo para listar os pacotes instalados.

    ```shell
    helm list
    ```

1. Execute os comandos abaixo para listar todos os pacotes.

    ```shell
    helm list -A
    ```

1. Execute os comandos abaixo para removendo o pacote.

    ```shell
    helm uninstall my-release
    ```

1. Execute os comandos abaixo para listar os recursos no Kubernetes.

    ```shell
    kubectl get all
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Removeu um pacote