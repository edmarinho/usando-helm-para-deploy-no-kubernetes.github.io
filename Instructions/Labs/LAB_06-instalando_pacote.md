---
lab:
    title: '06 - Instalando pacote'
    module: 'Usando o Helm'
---

# Lab 04 - Instalando pacote

# Laboratório do aluno

## Cenário de laboratório

Instalando um pacote.

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

#### Tarefa 2: Instalando um pacote

Nesta tarefa, você irá instalar um pacote e visualizar os recursos criados no cluster.

1. Execute os comandos abaixo para adicionar o repositório.

    ```shell
    helm repo add bitnami https://charts.bitnami.com/bitnami
    ```

1. Execute os comandos abaixo para atualizar a lista de chart dos repositórios remotos.

    ```shell
    helm repo update
    ```

1. Execute os comandos abaixo para instalar o chart do PHPMyAdmin.

    ```shell
    helm install my-release bitnami/phpmyadmin
    ```

1. Execute os comandos abaixo para listar os repositórios e veja que foi adicionado um repositório.

    ```shell
    helm repo list
    ```

1. Execute os comandos abaixo para Listar recursos no Kubernetes.

    ```shell
    kubectl get all
    ```

1. Execute os comandos abaixo para esperar o pod subir.

    ```shell
    kubectl get pods -w
    ```

1. Execute os comandos abaixo para Criar redirecionamento de porta.

    ```shell
    kubectl port-forward --namespace default svc/my-release-phpmyadmin 8080:80
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Instalou um pacote