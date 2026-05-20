# Failover com Route 53

## Problema

O desafio deste laboratório foi compreender como garantir a continuidade de uma aplicação mesmo quando ocorre falha em um servidor. Em ambientes de produção, a indisponibilidade de recursos pode impactar usuários e serviços, tornando necessário implementar mecanismos que detectem falhas e redirecionem o tráfego automaticamente.

## Objetivo

Meu objetivo foi implementar um mecanismo de alta disponibilidade utilizando o Amazon Route 53, configurando failover automático entre duas instâncias EC2 localizadas em diferentes Zonas de Disponibilidade.

## Solução

Para resolver esse desafio, utilizei duas instâncias EC2 executando a mesma aplicação, distribuídas em diferentes Zonas de Disponibilidade. Configurei uma Health Check no Route 53 para monitorar continuamente a instância principal e identificar possíveis falhas. Em seguida, criei registros DNS com política de roteamento do tipo Failover, definindo uma instância como principal e outra como secundária. Também configurei alertas utilizando SNS para notificar eventos relacionados à disponibilidade da aplicação.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- Amazon Route 53
- Amazon CloudWatch
- AWS SNS (Simple Notification Service)
- AWS CloudFormation
- Health Check
- DNS Failover
- Alta disponibilidade
- Monitoramento
- Alertas automáticos


## Evidências

<img width="1048" height="502" alt="176 1" src="https://github.com/user-attachments/assets/e05f3368-a3ee-41a7-828f-991ca911e69c" />
<img width="984" height="590" alt="176 2" src="https://github.com/user-attachments/assets/198f1f57-1540-4f8e-a3ee-ba6476710f23" />
<img width="978" height="582" alt="176 3" src="https://github.com/user-attachments/assets/6e3ae04c-9827-40ba-ad17-7c1044766cca" />


## Resultado

Ao final do laboratório, consegui implementar um ambiente com failover automático, permitindo que o tráfego fosse redirecionado para a instância secundária quando a instância principal apresentasse falha. Também validei o funcionamento do monitoramento e recebi notificações automáticas sobre os eventos configurados.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre alta disponibilidade e continuidade de serviços em ambientes cloud. Aprendi como o Route 53 pode monitorar recursos e redirecionar acessos automaticamente quando ocorre uma falha. Também compreendi a importância de distribuir aplicações entre diferentes Zonas de Disponibilidade e utilizar monitoramento com alertas para reduzir impactos e garantir maior confiabilidade dos serviços.
