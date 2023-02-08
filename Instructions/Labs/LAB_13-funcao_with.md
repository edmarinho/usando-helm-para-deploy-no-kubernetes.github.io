---
lab:
    title: '13 - Função with'
    module: 'Meu Chart'
---

# Lab 13 - Função with

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a função with.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função with

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

#### Tarefa 2: Usar a função with

Nesta tarefa, você irá ver quais as posibilidades de utilizarmos a função with no nosso chart.

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
        {{- with .Values.favorita }}
        bebida: {{ .bebida }}
        comida: {{ .comida }}
        {{- end }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        caneca: sim
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
        {{- with .Values.favorita }}
        bebida: {{ .bebida }}
        comida: {{ .comida }}
        {{- end }}
        caneca: {{ .Values.favorita.caneca }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
        bebida: café
        temperatura: frio
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
        {{- with .Values.favorita }}
        bebida: {{ .bebida }}
        comida: {{ .comida }}
        release: {{ $.Release.Name }}
        {{- end }}
        caneca: {{ .Values.favorita.caneca }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou a função with