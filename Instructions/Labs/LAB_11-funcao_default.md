---
lab:
    title: '11 - Função default'
    module: 'Meu Chart'
---

# Lab 11 - Função default

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a função default.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função defaul

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

#### Tarefa 2: Usar a função default

Nesta tarefa, você irá ver como podemos utilizar a função default para quando não for passado um valor no arquivo values.yaml ou com o parâmetro --set.

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
        bebida: {{ .Values.favorita.bebida | default "chá" | quote }}
        comida: {{ .Values.favorita.comida | upper | quote }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

1. Edite o arquivo values.yaml comantando a linha bebida conforme os dados abaixo.

    ```yaml
    favorita:
        #bebida: café
        comida: pizza
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou a função default