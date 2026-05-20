# Auto Scaling e Load Balancer na AWS

## Problema

O desafio deste laboratório foi compreender como manter aplicações disponíveis e com bom desempenho mesmo quando ocorre aumento no número de acessos. Em ambientes reais, uma única instância pode não ser suficiente para atender à demanda, tornando necessário distribuir a carga e aumentar recursos automaticamente quando necessário.

## Objetivo

Meu objetivo foi implementar uma arquitetura escalável e altamente disponível utilizando Load Balancer e Auto Scaling, garantindo distribuição de tráfego entre servidores e ajuste automático da capacidade conforme a demanda.

## Solução

Para resolver esse desafio, criei uma imagem (AMI) a partir de uma instância EC2 existente e a utilizei para padronizar novas implantações. Em seguida, configurei um Application Load Balancer para distribuir o tráfego entre diferentes instâncias e criei um Target Group para gerenciar esses recursos. Também configurei um Launch Template e um Auto Scaling Group para criar e remover instâncias automaticamente conforme o uso de CPU. Além disso, utilizei múltiplas zonas de disponibilidade e monitorei métricas utilizando o CloudWatch.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- Elastic Load Balancer (Application Load Balancer)
- Auto Scaling Group
- Amazon CloudWatch
- Amazon VPC
- Amazon Machine Image (AMI)
- Launch Template
- Target Group
- Alta disponibilidade
- Escalabilidade automática
- Balanceamento de carga


## Evidências

<img width="1097" height="257" alt="LAB 174 1" src="https://github.com/user-attachments/assets/add18d31-fd3c-4891-a91c-dfd57b8f1cb2" />
<img width="1084" height="348" alt="LAB 174 2" src="https://github.com/user-attachments/assets/f39b6e0b-3e7e-4776-9695-f447d0ddc630" />
<img width="1092" height="379" alt="LAB 174 3" src="https://github.com/user-attachments/assets/25eda705-8b3d-45ca-b7ad-37c8aa23d08a" />
<img width="1292" height="281" alt="LAB 174 4" src="https://github.com/user-attachments/assets/985f47f6-ff14-4d54-864e-7f344c5e691d" />
<img width="1333" height="480" alt="LAB 174 5" src="https://github.com/user-attachments/assets/762a0f53-c6d5-43c7-aa2d-53e404b6c380" />


## Resultado

Ao final do laboratório, consegui criar uma arquitetura capaz de distribuir automaticamente o tráfego entre múltiplas instâncias e ajustar a quantidade de servidores conforme a demanda. Também validei o funcionamento do balanceamento de carga e acompanhei a criação automática de novas instâncias durante os testes de aumento de carga.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre arquiteturas escaláveis e resilientes na AWS. Aprendi a importância de distribuir cargas entre diferentes servidores para melhorar a disponibilidade das aplicações e reduzir pontos únicos de falha. Também compreendi como o Auto Scaling ajuda a otimizar recursos e custos, aumentando ou reduzindo automaticamente a infraestrutura de acordo com a necessidade do ambiente.
