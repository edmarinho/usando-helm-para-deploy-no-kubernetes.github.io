---
lab:
    title: '09 - Arquivo values.yaml'
    module: 'Meu Chart'
---

# Lab 09 - Arquivo values.yaml

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos trabalhar com o arquivo values.yaml.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Trabalhando com valores de único nível
+ Tarefa 3: Trabalhando com valores de múltiplos níveis

## Estimated timing: 20 minutes

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

#### Tarefa 2: Trabalhando com valores de único nível

Nesta tarefa, você irá trabalhar com valores passados pelo arquivo values.yaml e --set de único nível.

1. Acesse o arquivo values.yaml que está dentro do diretório meuchart, remova todos o seu conteúdo e adiciona os dados abaixo.

    ```yaml
    bebida: café
    ```

1. Edite o arquivo configmap.yaml adicionando o objeto {{ .Release.Name }} conforme indicado abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.bebida }}
    ```
    > **_NOTE:_**  O objeto {{ .Values.bebida }} precisará receber um valor para que a implementação funcione corretamente.

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

1. Execute os comandos abaixo para testar a implementação usando o parâmetro --set.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart --set bebida=refrigerante
    ```
    > **_NOTE:_**  O valor passado usando o parâmetro --set sobrescreve o valor informado no arquivo values.yaml

#### Tarefa 3: Trabalhando com valores de múltiplos níveis

Nesta tarefa, você irá trabalhar com valores passados pelo arquivo values.yaml de múltiplos níveis.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Testou a implementação de um chart usando valores de único nível
- Testou a implementação de um chart usando valores de múltiplos níveis