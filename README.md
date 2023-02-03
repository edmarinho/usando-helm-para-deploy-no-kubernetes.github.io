# Usando Helm para deploy no Kubernetes

O contéudo aqui faz parte do treinamento **[Usando Helm para deploy no Kubernetes](https://www.udemy.com/course/usando-helm-para-deploy-no-kubernetes/)**

## Laboratórios

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| Module | Lab |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

