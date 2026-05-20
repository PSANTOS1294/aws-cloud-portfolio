# Banco de Dados com Amazon RDS e Integração com Aplicação

## Objetivo

Meu objetivo foi criar uma instância de banco de dados relacional utilizando o Amazon RDS, configurando recursos de segurança, alta disponibilidade e integração com uma aplicação web.

## Solução

Para resolver esse desafio, configurei uma instância Amazon RDS utilizando o mecanismo MySQL e implementei medidas para garantir segurança e disponibilidade do ambiente. Criei um Security Group específico para controlar o acesso ao banco de dados, permitindo conexões apenas do servidor autorizado. Também configurei sub-redes privadas e um grupo de sub-redes distribuído entre diferentes zonas de disponibilidade. Além disso, habilitei o modo Multi-AZ para aumentar a disponibilidade do banco e realizei a integração da aplicação com o endpoint fornecido pelo RDS.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon RDS (MySQL)
- Amazon EC2
- Amazon VPC
- Security Groups
- Subnets
- DB Subnet Group
- Multi-AZ
- Banco de dados relacional
- Alta disponibilidade
- Controle de acesso

## Evidências


<img width="1091" height="321" alt="LAB 160 1" src="https://github.com/user-attachments/assets/818e2492-c7f2-47a7-961f-cb2f6c8c7d7f" />
<img width="1047" height="262" alt="LAB 160 2" src="https://github.com/user-attachments/assets/c1e6a0ee-001d-4b5a-b7b3-346396f137ae" />
<img width="1044" height="307" alt="LAB 160 3" src="https://github.com/user-attachments/assets/7733db00-9ff0-4bb4-90ad-1c7372faabb2" />

## Resultado

Ao final do laboratório, consegui criar e configurar uma instância de banco de dados funcional e segura, permitindo a comunicação com a aplicação web por meio de uma conexão controlada. Também implementei recursos que aumentaram a disponibilidade e a proteção da solução.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre criação e gerenciamento de bancos de dados na AWS. Aprendi a importância de aplicar boas práticas de segurança, utilizar recursos de alta disponibilidade e configurar corretamente a comunicação entre aplicações e bancos de dados. Além disso, compreendi como uma arquitetura bem planejada pode aumentar a confiabilidade e a escalabilidade dos serviços em nuvem.
