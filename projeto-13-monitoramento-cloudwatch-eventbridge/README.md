# Projeto 13 - Monitoramento com CloudWatch, EventBridge e AWS Config

## Problema

O desafio deste laboratório foi compreender como monitorar recursos em nuvem de forma eficiente e automatizar respostas a eventos importantes. Em ambientes reais, apenas disponibilizar aplicações não é suficiente; também é necessário acompanhar desempenho, identificar falhas rapidamente e garantir que os recursos estejam seguindo padrões e boas práticas de configuração.

## Objetivo

Meu objetivo foi implementar uma solução completa de monitoramento e observabilidade na AWS, coletando métricas e logs de instâncias EC2, criando alarmes, automatizando respostas a eventos e verificando a conformidade dos recursos.

## Solução

Para resolver esse desafio, instalei e configurei o CloudWatch Agent em uma instância EC2 para coletar métricas e logs do ambiente. Em seguida, configurei o envio de logs específicos e criei filtros para transformar eventos em métricas monitoráveis. Também configurei alarmes integrados ao SNS para envio automático de notificações. Para ampliar a automação, utilizei o EventBridge para identificar eventos relacionados às instâncias EC2 e gerar respostas automáticas. Além disso, implementei regras no AWS Config para verificar a conformidade dos recursos e validar boas práticas de configuração.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- Amazon CloudWatch
- CloudWatch Logs
- CloudWatch Alarms
- AWS Systems Manager
- Amazon EventBridge
- Amazon SNS
- AWS Config
- Parameter Store
- CloudWatch Agent
- Monitoramento e observabilidade
- Automação de eventos

## Arquitetura da solução

<img width="2391" height="926" alt="image" src="https://github.com/user-attachments/assets/dcf492bf-4333-49e5-9c41-633e298ad84f" />



## Evidências
### CloudWatch Agent instalado e coletando dados

  <img width="1032" height="539" alt="lab 186" src="https://github.com/user-attachments/assets/71b6e419-e188-451c-8973-2266bcca56ab" />
<img width="1348" height="433" alt="lab 186 1" src="https://github.com/user-attachments/assets/77cedd0d-af3b-4b12-b1fa-faa5fd994acf" />

### Logs sendo enviados para CloudWatch Logs

  <img width="1071" height="387" alt="lab 186 2" src="https://github.com/user-attachments/assets/4cae08c8-7a1b-4c0c-896d-44db628ba9bd" />
  
### Métrica personalizada 404Errors criada

  <img width="1074" height="492" alt="lab 186 3" src="https://github.com/user-attachments/assets/1b0af16f-c98d-4c10-b089-179652ad40a3" />

### Alarme configurado e acionado

  <img width="1082" height="310" alt="lab 186 4" src="https://github.com/user-attachments/assets/08ffc811-a159-497a-91b8-171b16cd9169" />
<img width="1087" height="525" alt="lab 186 5" src="https://github.com/user-attachments/assets/0233290c-fea3-406e-b9d4-da0a237811a1" />

###Notificação recebida via SNS

  <img width="1046" height="448" alt="lab 186 6" src="https://github.com/user-attachments/assets/ab86baa1-ba7b-451b-89a4-f07d7a119f66" />

### Regra do EventBridge funcionando corretamente
  <img width="1039" height="341" alt="lab 186 8" src="https://github.com/user-attachments/assets/94eb228d-8208-4133-be6c-3e8f3ebe745a" />

### AWS Config avaliando conformidade dos recursos

<img width="1019" height="191" alt="lab 186 9" src="https://github.com/user-attachments/assets/0a55dd73-51f8-40c3-938e-881c0bfa22e0" />
<img width="1013" height="199" alt="lab 186 10" src="https://github.com/user-attachments/assets/0a663ab9-8ddc-46e7-afd7-1482d001f93c" />

---

## Script

### Instalação do Agent
```bash
aws ssm send-command \
--document-name "AWS-ConfigureAWSPackage" \
--parameters '{"action":["Install"],"name":["AmazonCloudWatchAgent"]}'
````
### Configuração do Agent
```bash
aws ssm send-command \
--document-name "AmazonCloudWatch-ManageAgent" \
--parameters '{"action":["configure"],"mode":["ec2"],"config-source":["ssm"]}'
````
### Filtro de métrica 404
```bash
[ip, id, user, timestamp, request, status_code=404, size]
````

## Resultado

Ao final do laboratório, consegui implementar uma solução integrada de monitoramento capaz de coletar logs e métricas, gerar alarmes, enviar notificações automáticas e monitorar eventos da infraestrutura. Também validei o funcionamento das regras de conformidade para garantir que os recursos estivessem alinhados às configurações definidas.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre monitoramento, observabilidade e governança em ambientes cloud. Aprendi a importância de acompanhar métricas e logs para identificar problemas rapidamente, além de compreender como automatizar respostas por meio de eventos e notificações. Também entendi como ferramentas de conformidade ajudam a manter ambientes mais organizados, seguros e alinhados com boas práticas de infraestrutura.
