# Investigação de Incidente com AWS CloudTrail + Athena

## Objetivo
Investigar uma invasão em uma instância EC2 utilizando logs do AWS CloudTrail, identificar o responsável, analisar ações suspeitas e aplicar correções de segurança no ambiente AWS.

---

## Serviços Utilizados
- AWS CloudTrail
- Amazon S3
- Amazon Athena
- AWS EC2
- AWS IAM
- AWS CLI
- Linux (grep, SSH)

---

## Implementação

1. Análise inicial do ambiente EC2 e grupo de segurança
2. Criação de uma trilha no CloudTrail para captura de eventos
3. Identificação de alteração suspeita (abertura da porta 22 para 0.0.0.0/0)
4. Download dos logs do CloudTrail via AWS CLI
5. Extração e análise dos logs com comandos Linux (grep)
6. Consulta de eventos com AWS CLI (lookup-events)
7. Criação de tabela no Athena para análise estruturada
8. Execução de queries SQL para identificar o invasor
9. Identificação do usuário malicioso (chaos-user)
10. Remoção do acesso indevido no sistema operacional
11. Correção de falhas de segurança no SSH
12. Exclusão do usuário malicioso no IAM
13. Restauração do site comprometido

---

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
## Aprendizado

Neste laboratório aprendi na prática como utilizar o AWS CloudTrail como ferramenta de auditoria e investigação de segurança, entendendo como rastrear ações realizadas dentro da conta AWS. Também desenvolvi habilidades na análise de logs utilizando tanto ferramentas de linha de comando quanto consultas SQL no Athena, o que facilitou a identificação do invasor e das ações realizadas. Além disso, compreendi a importância de boas práticas de segurança, como restrições em grupos de segurança, uso correto de autenticação SSH e gestão adequada de usuários IAM para evitar acessos indevidos e vulnerabilidades em ambientes cloud.
