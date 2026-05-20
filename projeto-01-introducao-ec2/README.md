# Introdução ao Amazon EC2

## Problema
O desafio deste laboratório foi compreender como criar e administrar um servidor em nuvem de forma segura e eficiente. Em ambientes reais, além de disponibilizar um servidor para acesso, também é necessário controlar permissões, monitorar desempenho e evitar falhas ou exclusões acidentais que possam comprometer os serviços.

## Objetivo
Meu objetivo foi implementar e gerenciar uma instância virtual utilizando o Amazon EC2, aplicando conceitos importantes da computação em nuvem relacionados à segurança, monitoramento e gerenciamento de recursos.

## Arquitetura da Solução
A solução consiste na utilização de uma instância EC2 como servidor web, onde o acesso é controlado por meio de um Security Group configurado para permitir tráfego HTTP. O armazenamento é gerenciado com EBS, enquanto o monitoramento da instância é realizado com ferramentas nativas da AWS. A proteção contra término adiciona uma camada extra de segurança operacional.

##  Serviços Utilizados
- Amazon EC2
- Security Group
- Amazon CloudWatch (monitoramento básico)
- Amazon EBS

##  Implementação

Durante este laboratório prático, realizei as seguintes etapas:

1. Inicialização de uma instância EC2 com servidor web configurado.
2. Ativação da proteção contra encerramento para evitar exclusões acidentais.
3. Monitoramento da instância utilizando métricas básicas de desempenho.
4. Configuração e modificação do Security Group para permitir acesso HTTP (porta 80).
5. Redimensionamento da instância, simulando um cenário de escalabilidade.
6. Execução de testes para validação da proteção contra término.
7. Encerramento seguro da instância ao final do laboratório.



## Evidências

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/08bfdb7b-eef8-46c0-902a-92d22fe909fe" />

## Resultados
Ao final do laboratório, consegui criar e configurar um servidor funcional em ambiente de nuvem, garantindo acesso controlado, monitoramento básico do desempenho e aplicação de medidas de segurança para proteger a infraestrutura. Também consegui realizar testes e ajustes que demonstraram a flexibilidade do ambiente em nuvem.


## 📚 Aprendizado
Este laboratório me permitiu compreender, na prática, como funciona a criação e administração de servidores utilizando serviços em nuvem. Aprendi a importância de configurar corretamente regras de acesso, monitorar recursos e implementar mecanismos de proteção para evitar erros operacionais. Além disso, desenvolvi uma visão mais ampla sobre como a computação em nuvem oferece escalabilidade e flexibilidade para atender diferentes necessidades de infraestrutura.
