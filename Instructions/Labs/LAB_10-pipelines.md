---
lab:
    title: 'Pipelines'
    module: 'Meu Chart'
---

# Lab - Pipelines

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos criar uma pipeline para modificação de um objeto em tempo de execução.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função quote fora de uma pipeline
+ Tarefa 3: Usar a função quote dentro de uma pipeline
+ Tarefa 4: Usar a função upper dentro de uma pipeline
+ Tarefa 5: Usar a função repeat dentro de uma pipeline

## Tempo estimado: 20 minutes

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

#### Tarefa 2: Usar a função quote fora de uma pipeline

Nesta tarefa, você irá ver como podemos utilizar a função quote fora de uma pipeline.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ quote .Values.favorita.bebida }}
        comida: {{ quote .Values.favorita.comida }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Tarefa 3: Usar a função quote dentro de uma pipeline

Nesta tarefa, você irá ver como podemos utilizar a função quote dentro de uma pipeline.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.favorita.bebida | quote }}
        comida: {{ .Values.favorita.comida | quote }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Tarefa 4: Usar a função upper dentro de uma pipeline

Nesta tarefa, você irá ver como podemos utilizar a função upper dentro de uma pipeline.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.favorita.bebida | quote }}
        comida: {{ .Values.favorita.comida | upper | quote }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Tarefa 5: Usar a função repeat dentro de uma pipeline

Nesta tarefa, você irá ver como podemos utilizar a função repeat dentro de uma pipeline.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.favorita.bebida | repeat 5 | quote }}
        comida: {{ .Values.favorita.comida | upper | quote }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou a função quote fora de uma pipeline
- Utilizou a função quote dentro de uma pipeline
- Utilizou a função upper fora de uma pipeline
- Utilizou a função repeat fora de uma pipeline