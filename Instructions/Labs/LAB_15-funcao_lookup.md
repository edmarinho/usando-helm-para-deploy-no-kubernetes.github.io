---
lab:
    title: '15 - Função Lookup'
    module: 'Meu Chart'
---

# Lab 15 - Função Lookup

# Laboratório do aluno

## Cenário de laboratório

Iremos ver como podemos utilizar a função lookup.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objetivos

Neste laboratório, você irá:

+ Tarefa 1: [Opcional] Iniciando os serviços
+ Tarefa 2: Usar a função lookup

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

#### Tarefa 2: Usar a função lookup

Nesta tarefa, você irá ver quais as posibilidades de utilizarmos a função lookup no nosso chart.

1. Execute os comandos abaixo para instalar o nginx como ingress.

    ```shell
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controllerv1.1.0/deploy/static/provider/cloud/deploy.yaml
    ```

1. Execute os comandos abaixo para visualizar recursos do Nginx.

    ```shell
    kubectl get all -n ingress-nginx
    ```

1. Execute os comandos abaixo para visualizar informações do service do nginx.

    ```shell
    kubectl edit service -n ingress-nginx ingress-nginx-controller
    ```

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: {{ .Release.Name }}-configmap
    data:
      ServiceIp: {{ (lookup "v1" "Service" "ingress-nginx" "ingress-nginx-controller").spec.clusterIP }}
    ```

1. Execute os comandos abaixo para instalar o chart.

    ```shell
    helm install --debug lookup ./meuchart
    ```
    > **_NOTE:_**  Observe o resultado

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: {{ .Release.Name }}-configmap
    data:
      {{- range $index, $pod := (lookup "v1" "Pod" "ingress-nginx" "").items }}
      pod: {{ $pod.metadata.name }}
      {{ end }}
    ```

1. Execute os comandos abaixo para reinstalar o chart.

    ```shell
    helm uninstall lookup && helm install --debug lookup ./mychart
    ```
    > **_NOTE:_**  Observe o resultado

1. Edite o arquivo configmap.yaml adicionando conforme os dados abaixo.

    ```yaml
    apiVersion: v1
    kind: ConfigMap
    metadata:
      name: {{ .Release.Name }}-configmap
    data:
      {{- if (lookup "v1" "Service" "ingress-nginx" "ingress-nginx-controller")}}
      lookup: "Serviço existe"
      {{- end }}
    ```

1. Execute os comandos abaixo para reinstalar o chart.

    ```shell
    helm uninstall lookup && helm install --debug lookup ./mychart
    ```
    > **_NOTE:_**  Observe o resultado

1. Execute os comandos abaixo para remover o nginx.

    ```shell
    kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controllerv1.1.0/deploy/static/provider/cloud/deploy.yaml
    ```

1. Execute os comandos abaixo para visualizar recursos do Nginx.

    ```shell
    kubectl get all -n ingress-nginx
    ```

1. Execute os comandos abaixo para reinstalar o chart.

    ```shell
    helm uninstall lookup && helm install --debug lookup ./mychart
    ```
    > **_NOTE:_**  Observe o resultado

1. Execute os comandos abaixo para remover o chart.

    ```shell
    helm uninstall lookup
    ```

#### Revisão

Neste laboratório, você fez:

- [Opcional] Iniciou os serviços
- Utilizou a função with