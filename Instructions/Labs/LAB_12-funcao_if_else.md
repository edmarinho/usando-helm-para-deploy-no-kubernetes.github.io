---
lab:
    title: 'Função if/else'
    module: 'Meu Chart'
---

# Lab - Função if/else

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a função if/else.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função if/else

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

#### Tarefa 2: Usar a função if/else

Nesta tarefa, você irá ver quais as posibilidades de utilizarmos a função if/else no nosso chart.

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
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
        {{ if eq .Values.favorita.bebida "café" }}
        caneca: "Sim"
        {{ end }}
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
        temperatura: quente
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
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
        {{- if and (eq .Values.favorita.bebida "café") (eq .Values.favorita.temperatura
        "quente") }}
        caneca: "Sim, com protetor"
        {{ else }}
        caneca: "Sim, sem protetor"
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
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
        {{- if and (eq .Values.favorita.bebida "café") (eq .Values.favorita.temperatura
        "quente") }}
        caneca: "Sim, com protetor"
        {{ else }}
        caneca: "Sim, sem protetor"
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
        temperatura: quente
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
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
        {{- if and (eq .Values.favorita.bebida "café") (eq .Values.favorita.temperatura
        "quente") }}
        caneca: "Sim, com protetor"
        {{ else if and (eq .Values.favorita.bebida "café") (eq .Values.favorita.temperatura "fria") }}
        caneca: "Sim, sem protetor"
        {{ else }}
        caneca: "Não"
        {{- end }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    configmap:
        enabled: true
    favorita:
        bebida: café
        comida: pizza
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    {{ if eq .Values.configmap.enabled true }}
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
        bebida: {{ .Values.favorita.bebida }}
        comida: {{ .Values.favorita.comida }}
    {{ end }}
    ```

1. Execute os comandos abaixo para testar a implementação.

    ```shell
    helm install --debug --dry-run restaurante ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou a função if/else