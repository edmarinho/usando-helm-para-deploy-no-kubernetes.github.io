---
lab:
    title: 'Função range'
    module: 'Meu Chart'
---

# Lab - Função range

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a função range.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função range

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

#### Tarefa 2: Usar a função range

Nesta tarefa, você irá ver quais as posibilidades de utilizarmos a função range no nosso chart.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
      bebida:
        - café
        - suco
        - leite
        - água
      comida:
        - pizza
        - macarrão
        - lasanha
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
      myvalue: "Hello World"
      bebida: |-
        {{- range .Values.favorita.bebida }}
        - {{ . | quote }}
        {{- end }}
      comida: |-
        {{- range .Values.favorita.comida }}
        - {{ . | quote }}
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
      comida: pizza
    ingredientepizza:
      - nome: farinha
        local: massa
      - nome: molho
        local: cobertura
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
      ingredientes: |-
        {{- range .Values.ingredientepizza }}
        - nome: {{ .nome | quote }}
          local: {{ .local | quote }}
        {{- end }}
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