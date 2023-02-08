---
lab:
    title: 'Meu primeiro Chart'
    module: 'Meu Chart'
---

# Lab - Meu primeiro Chart

# Laboratório do aluno

## Cenário de laboratório

Iremos criar nosso primeiro chart.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Criar um chart
+ Tarefa 3: Adicionar um objeto

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

#### Tarefa 2: Criar um chart

Nesta tarefa, você irá criar o seu primeiro chart.

1. Execute os comandos abaixo para que o helm crie um chart.

    ```shell
    helm create meuchart
    ```
    > **_NOTE:_**  <br>
    *NOTES.txt:* Texto de ajuda para o seu Chart. É exibido para os usuários quando o mesmo
for instalado.<br><br>
*deployment.yaml:* Um manifesto básico para a criação de uma implantação no
Kubernetes.<br><br>
*service.yaml:* Um manifesto básico para a criação de um serviço para a sua implantação.<br><br>
*_herlpers.tpl:* Lugar para colocar templates auxiliares que podemos reutilizar em todo o
chart

1. Execute os comandos abaixo para remover todos os arquivos criados pelo helm, pois iremos criar o nosso.

    ```shell
    rm -rf meuchart/templates/*
    ```

1. Dentro do diretório templates crie um arquivo configmap.yaml e adiciona o seguinte conteúdo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: meuchart-configmap
    data:
        myvalue: "Hello World"
    ```

1. Execute os comandos abaixo para instalar o chart.

    ```shell
    helm install meuchart-v1 ./meuchart
    ```
1. Execute os comandos abaixo para verificar os recursos criados.

    ```shell
    helm get manifest meuchart-v1
    ```
1. Execute os comandos abaixo para remover o chart.

    ```shell
    helm uninstall meuchart-v1
    ```
#### Tarefa 3: Adicionar um objeto

Nesta tarefa, você irá adicionar um objeto no chart e instalar novamente.

1. Edite o arquivo configmap.yaml adicionando o objeto {{ .Release.Name }} conforme indicado abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
        name: {{ .Release.Name }}-configmap
    data:
        myvalue: "Hello World"
    ```
    > **_NOTE:_**  Os objetos nos templates são representados por dois pares de chaves ({{ e }})

1. Execute os comandos abaixo para instalar o chart.

    ```shell
    helm install meuchart-v1 ./meuchart
    ```
1. Execute os comandos abaixo para verificar os recursos criados.

    ```shell
    helm get manifest meuchart-v1
    ```
1. Execute os comandos abaixo para remover o chart.

    ```shell
    helm uninstall meuchart-v1
    ```
1. [Opcional] Execute os comandos abaixo para testar uma implementação sem a necessidade de fazer a instalação e talvez comprometer o seu ambiente.

    ```shell
    helm install --debug --dry-run meuchart-v3 ./meuchart
    ```
    > **_NOTE:_**  *--dry-run:* Usado para simular a implantação de um chart. O resultado sem erro não indica que não poderá ocorrer erros durante a instalação, pois poderá haver conflitos com outros recursos criados no Kubernetes.

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Criou um chart
- Adicionou um objeto ao chart criado