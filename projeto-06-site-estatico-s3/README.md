# Hospedagem de Site Estático no Amazon S3

## Problema

O desafio deste laboratório foi compreender como publicar e disponibilizar um site na nuvem de maneira simples, segura e organizada. Além da hospedagem do conteúdo, também foi necessário entender como controlar permissões de acesso e automatizar processos para facilitar futuras atualizações do site.

## Objetivo

Meu objetivo foi criar e hospedar um site estático utilizando o Amazon S3, utilizando a AWS CLI para automatizar tarefas e o IAM para gerenciar permissões de acesso aos recursos utilizados.

## Solução

Para resolver esse desafio, acessei uma instância EC2 utilizando o Systems Manager e configurei a AWS CLI para comunicação com os serviços da AWS. Em seguida, criei um bucket no Amazon S3 para armazenar os arquivos do site, configurei permissões de acesso utilizando o IAM e habilitei a hospedagem estática do bucket. Após realizar o upload dos arquivos do site, desenvolvi um script em bash para automatizar futuras atualizações, permitindo uma nova publicação do conteúdo de forma mais rápida e prática.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon S3
- AWS Command Line Interface (AWS CLI)
- AWS Identity and Access Management (IAM)
- Amazon EC2
- AWS Systems Manager (Session Manager)
- Linux
- Script Bash
- Hospedagem de site estático
- Automação de deploy
- Controle de acesso

## Evidências

<img width="1322" height="609" alt="Lab 170 1" src="https://github.com/user-attachments/assets/cc0314b9-a36e-4ff2-9bc8-6af7671177b2" />
<img width="1345" height="617" alt="Lab 170 3" src="https://github.com/user-attachments/assets/380f7903-6adb-42c3-b4a1-0f6b346b512c" />
<img width="587" height="603" alt="Lab 170 2" src="https://github.com/user-attachments/assets/0189f280-bac3-4bea-aeb9-2bcbbf51d390" />


## Script
```bash
# Configurar CLI
aws configure

# Criar bucket
aws s3api create-bucket --bucket <nome-do-bucket> --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2

# Configurar site estático
aws s3 website s3://<nome-do-bucket>/ --index-document index.html

# Upload dos arquivos
aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<nome-do-bucket>/ --recursive --acl public-read

# Listar arquivos no bucket
aws s3 ls s3://<nome-do-bucket>/

# Script de atualização
#!/bin/bash
aws s3 cp /home/ec2-user/sysops-activity-files/static-website/ s3://<nome-do-bucket>/ --recursive --acl public-read
````
## Resultado

Ao final do laboratório, consegui hospedar um site estático no Amazon S3 e disponibilizá-lo por meio de um endereço público. Também configurei permissões adequadas para acesso aos recursos e automatizei o processo de atualização do site, tornando futuras alterações mais rápidas e eficientes.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre hospedagem de sites estáticos na AWS e mostrou como serviços diferentes podem trabalhar em conjunto. Aprendi a configurar permissões utilizando o IAM, utilizar a AWS CLI para automatizar tarefas e criar scripts para facilitar processos repetitivos. Além disso, compreendi a importância da automação para otimizar atividades e tornar a administração de ambientes cloud mais eficiente.
