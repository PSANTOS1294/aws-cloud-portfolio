# Banco de Dados com Amazon RDS e Integração com Aplicação

## Objetivo
Criar uma instância de banco de dados relacional utilizando o Amazon RDS com alta disponibilidade, configurar o acesso seguro e realizar a integração com uma aplicação web.

## Serviços Utilizados
- Amazon RDS (MySQL)
- Amazon EC2
- Amazon VPC
- Security Groups
- Subnets

## Implementação

Durante este laboratório prático, foram realizadas as seguintes etapas:

1. Criação de um Security Group para o banco de dados, permitindo acesso apenas do servidor web.
2. Configuração de regras de entrada na porta 3306 (MySQL).
3. Criação de um grupo de sub-redes (DB Subnet Group) em duas zonas de disponibilidade.
4. Configuração de sub-redes privadas para maior segurança.
5. Criação de uma instância Amazon RDS com mecanismo MySQL.
6. Configuração do banco de dados em modo Multi-AZ para alta disponibilidade.
7. Definição de credenciais de acesso ao banco de dados.
8. Associação do Security Group à instância RDS.
9. Configuração de conectividade dentro da VPC.
10. Monitoramento do status da instância até ficar disponível.


## Arquitetura da Solução
A solução consiste em uma arquitetura em nuvem com uma instância de banco de dados Amazon RDS configurada em modo Multi-AZ, garantindo alta disponibilidade e resiliência. O banco de dados é implantado em sub-redes privadas dentro de uma VPC, aumentando a segurança. O acesso ao banco é controlado por meio de Security Groups, permitindo conexões apenas de servidores autorizados (EC2). A aplicação web se conecta ao banco utilizando o endpoint fornecido pelo RDS.

## Evidências


<img width="1091" height="321" alt="LAB 160 1" src="https://github.com/user-attachments/assets/818e2492-c7f2-47a7-961f-cb2f6c8c7d7f" />
<img width="1047" height="262" alt="LAB 160 2" src="https://github.com/user-attachments/assets/c1e6a0ee-001d-4b5a-b7b3-346396f137ae" />
<img width="1044" height="307" alt="LAB 160 3" src="https://github.com/user-attachments/assets/7733db00-9ff0-4bb4-90ad-1c7372faabb2" />

## Aprendizado
Este laboratório proporcionou uma compreensão prática sobre como configurar e gerenciar bancos de dados relacionais na AWS utilizando o Amazon RDS. Foi possível entender conceitos fundamentais como alta disponibilidade com Multi-AZ, isolamento de rede com sub-redes privadas, controle de acesso via Security Groups e integração entre aplicação e banco de dados. Além disso, reforçou a importância de boas práticas de arquitetura, segurança e escalabilidade em ambientes de Cloud Computing.
