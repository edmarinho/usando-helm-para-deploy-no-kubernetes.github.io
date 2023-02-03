---
lab:
    title: '01 - Instalando o docker (Linux)'
    module: 'Preparando o ambiente'
---

# Lab 01 - Instalando o docker (Linux)

# Laboratório do aluno

## Cenário de laboratório

Instalação do docker community no linux para realizar demais atividades do curso.

>**Note:** As tarefas foram executadas no Ubuntu 22.04.

## Objectives

Neste laboratório, você irá:

+ Tarefa 1: Instalando pré-requesitos
+ Tarefa 2: Instalando o docker

## Estimated timing: 10 minutes

## Architecture diagram
![image](../media/lab01.png)

## Instruções

#### Tarefa 1: Instalando pré-requesitos

Nesta tarefa, você irá instalar os pré-requisitos para a instalação do docker.

1. Faça login no linux com um usuário que tenha acesso administrativo.

1. Execute os comandos abaixo para atualizar a lista de pacotes disponíveis para instalação.

```
sudo apt update
```

1. Execute os comandos abaixo para instalar pré-requesitos que faz com que o apt utilize https.

```
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

1. Execute os comandos abaixo para adicionar a chave GPG do repositório oficial do Docker.

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

1. Execute os comandos abaixo para adicionar o repositório do Docker na lista de repositórios do linux.

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu
focal stable"
```

1. Execute os comandos abaixo para atualizar a lista de pacotes disponíveis para instalação.

```
sudo apt update
```

#### Tarefa 2: Instalando o docker

Nesta tarefa, você irá instalar o docker na versão community.

1. Execute os comandos abaixo para instalar o docker.

```
sudo apt install -y docker-ce
```

1. Execute os comandos abaixo para verificar o status do serviço do docker.

```
systemctl status docker
```

1. [Opcional] Execute os comandos abaixo para iniciar o serviço do docker.

```
systemctl start docker
```

1. Execute os comandos abaixo para dar permissão, de executar os comando do docker, ao usuário em uso.

```
sudo usermod -aG docker ${USER}
```

#### Revisão

Neste laboratório, você fez:

- Instalação dos pré-requesitos necessários para a instalação do docker
- Instalação do docker