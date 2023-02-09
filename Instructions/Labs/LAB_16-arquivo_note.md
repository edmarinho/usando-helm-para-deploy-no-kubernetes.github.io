---
lab:
    title: 'Arquivo NOTES.txt'
    module: 'Meu Chart'
---

# Lab - Arquivo NOTES.txt

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a arquivo NOTES.txt.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar o arquivo NOTES.txt

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

#### Tarefa 2: Usar o arquivo NOTES.txt

Nesta tarefa, você irá ver quais as posibilidades de utilizarmos o arquivo NOTES.txt no nosso chart.

1. Edite o arquivo values.yaml conforme os dados abaixo.

    ```yaml
    favorita:
      bebida: café
      comida: pizza
    ```

1. Dentro do diretório templates crie um arquivo NOTES.txt e adiciona o seguinte conteúdo.

    ```txt
    Obrigado por instalar {{ .Chart.Name }}.
    Seu release name é {{ .Release.Name }}.
    Para mais informações sobre a release, execute:
      $ helm status {{ .Release.Name }}
      $ helm get all {{ .Release.Name }}
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
    > **_NOTE:_**  Observe o resultado

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou o arquivo NOTES.txt