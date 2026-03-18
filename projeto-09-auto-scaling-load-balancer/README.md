# Auto Scaling e Load Balancer na AWS

## Objetivo
Implementar uma arquitetura altamente disponível e escalável utilizando Elastic Load Balancer (ELB) e Auto Scaling, garantindo distribuição de carga e ajuste automático de capacidade conforme a demanda.

## Serviços Utilizados
- Amazon EC2
- Elastic Load Balancer (Application Load Balancer)
- Auto Scaling Group
- Amazon CloudWatch
- Amazon VPC
- Amazon Machine Image (AMI)

## Implementação

Durante este laboratório prático, foram realizadas as seguintes etapas:

1. Criação de uma AMI a partir de uma instância EC2 existente.
2. Configuração de um Application Load Balancer (ALB).
3. Criação de um Target Group para gerenciamento das instâncias.
4. Configuração de listeners e regras de roteamento HTTP.
5. Criação de um Launch Template com a AMI gerada.
6. Definição do tipo de instância e Security Group.
7. Criação de um Auto Scaling Group.
8. Configuração de sub-redes privadas em múltiplas zonas de disponibilidade.
9. Associação do Auto Scaling Group ao Load Balancer.
10. Definição de capacidade mínima, desejada e máxima (2 a 4 instâncias).
11. Configuração de política de escalabilidade baseada em CPU (50%).
12. Criação automática de alarmes no CloudWatch.
13. Teste de balanceamento de carga via DNS do Load Balancer.
14. Simulação de carga para acionar o Auto Scaling.
15. Monitoramento do aumento automático de instâncias.
16. Encerramento da instância original após criação da AMI.

## Arquitetura da Solução
A arquitetura consiste em um Application Load Balancer distribuindo o tráfego entre múltiplas instâncias EC2 localizadas em sub-redes privadas e em diferentes Zonas de Disponibilidade. O Auto Scaling Group garante que a quantidade de instâncias se ajuste automaticamente conforme a demanda, baseado em métricas de CPU monitoradas pelo CloudWatch. Essa abordagem proporciona alta disponibilidade, tolerância a falhas e otimização de custos.

## Evidências

<img width="1097" height="257" alt="LAB 174 1" src="https://github.com/user-attachments/assets/add18d31-fd3c-4891-a91c-dfd57b8f1cb2" />
<img width="1084" height="348" alt="LAB 174 2" src="https://github.com/user-attachments/assets/f39b6e0b-3e7e-4776-9695-f447d0ddc630" />
<img width="1092" height="379" alt="LAB 174 3" src="https://github.com/user-attachments/assets/25eda705-8b3d-45ca-b7ad-37c8aa23d08a" />
<img width="1292" height="281" alt="LAB 174 4" src="https://github.com/user-attachments/assets/985f47f6-ff14-4d54-864e-7f344c5e691d" />
<img width="1333" height="480" alt="LAB 174 5" src="https://github.com/user-attachments/assets/762a0f53-c6d5-43c7-aa2d-53e404b6c380" />


## Aprendizado
Este laboratório proporcionou uma visão prática e aprofundada sobre arquiteturas escaláveis e resilientes na AWS. Foi possível compreender como distribuir carga entre múltiplas instâncias utilizando um Load Balancer, além de automatizar o provisionamento de recursos com Auto Scaling. Também foram reforçados conceitos como alta disponibilidade, uso de múltiplas zonas de disponibilidade, monitoramento com CloudWatch e otimização de custos com escalabilidade automática. Esses conhecimentos são essenciais para o desenvolvimento de soluções robustas em ambientes de produção na nuvem.
