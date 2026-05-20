# Investigação de Incidente com AWS CloudTrail + Athena

## Problema

O desafio deste laboratório foi compreender como investigar incidentes de segurança em ambientes cloud e identificar atividades suspeitas dentro da infraestrutura. Em cenários reais, ataques ou configurações incorretas podem comprometer recursos e serviços, tornando essencial a capacidade de rastrear eventos, identificar a origem do problema e aplicar correções rapidamente.

## Objetivo

Meu objetivo foi investigar um incidente em uma instância EC2 utilizando logs do AWS CloudTrail, identificar ações suspeitas, descobrir a origem do problema e aplicar correções de segurança no ambiente AWS.

## Solução

Para resolver esse desafio, iniciei a análise verificando configurações da instância EC2 e regras de segurança do ambiente. Em seguida, utilizei o AWS CloudTrail para registrar e rastrear eventos realizados na conta. Os logs gerados foram armazenados no Amazon S3 e analisados utilizando ferramentas de linha de comando e consultas estruturadas no Amazon Athena. Durante a investigação, identifiquei alterações suspeitas relacionadas à configuração do ambiente, localizei o usuário responsável pelas ações indevidas e realizei correções de segurança, incluindo remoção de acessos indevidos, ajustes de permissões e restauração do ambiente comprometido.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- AWS CloudTrail
- Amazon S3
- Amazon Athena
- Amazon EC2
- AWS IAM
- AWS CLI
- Linux
- SSH
- Logs de auditoria
- Investigação de incidentes
- Consultas SQL


## Arquitetura da Solução

<img width="814" height="437" alt="image" src="https://github.com/user-attachments/assets/0f377cd0-9bf5-4c5e-845c-0b1b1e47b08c" />


Fluxo:

EC2 → CloudTrail → S3 → Athena → Investigação → Correção

---

## Evidências

### Site alterado (defacement)
<img width="1071" height="614" alt="lab 187 2" src="https://github.com/user-attachments/assets/abeabae1-49df-4adc-8d75-aa125027fe3a" />

### Regra de segurança indevida (SSH aberto para todos)

<img width="1063" height="222" alt="lab 187 3" src="https://github.com/user-attachments/assets/a6c7364a-46f9-4e49-980d-acf1732402bc" />

### Consulta SQL no Athena identificando o invasor

<img width="961" height="147" alt="lab 187 5" src="https://github.com/user-attachments/assets/a9c4d012-bb6a-4af9-808c-d97cd79248ef" />

### Comandos Linux evidenciando acesso indevido
<img width="992" height="402" alt="lab 187 6" src="https://github.com/user-attachments/assets/fa3832ef-517c-494a-bd34-84c351eb0919" />

### Backup do arquivo de imagens original

<img width="740" height="427" alt="lab 187 7" src="https://github.com/user-attachments/assets/bf3dfabb-85d1-4e2a-9936-6ab93b5d55fa" />

### Site restaurado

<img width="1152" height="573" alt="lab 187 8" src="https://github.com/user-attachments/assets/be4c0460-0230-4dff-9716-a3c229d89557" />

### Exclusão do usuário indevido

<img width="626" height="516" alt="lab 187 9" src="https://github.com/user-attachments/assets/6db8116a-c509-42fd-b6c8-427292a60e54" />

---

## Scripts

### Download dos logs
```bash
aws s3 cp s3://<bucket>/ . --recursive
````
### Descompactar logs
```bash
gunzip *.gz
```
### Análise com grep
```bash
cat arquivo.json | python -m json.tool | grep eventName
````
### Buscar eventos via CLI
```bash
aws cloudtrail lookup-events \
--lookup-attributes AttributeKey=ResourceType,AttributeValue=AWS::EC2::SecurityGroup
````
### Consulta no Athena
```bash
SELECT useridentity.userName, eventtime, eventsource, eventname
FROM cloudtrail_logs_monitoring####
WHERE eventsource = 'ec2.amazonaws.com'
````
## Resultado

Ao final do laboratório, consegui identificar a origem das alterações indevidas no ambiente, rastrear as ações realizadas e aplicar medidas corretivas para restaurar a segurança da infraestrutura. Também validei a remoção dos acessos não autorizados e a recuperação do ambiente comprometido.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre investigação e resposta a incidentes em ambientes cloud. Aprendi a importância dos logs de auditoria para rastrear atividades realizadas na infraestrutura e compreendi como ferramentas como CloudTrail e Athena podem auxiliar na análise e identificação de eventos suspeitos. Além disso, reforcei conhecimentos relacionados a boas práticas de segurança, gerenciamento de acessos e correção de vulnerabilidades para reduzir riscos em ambientes na nuvem.
