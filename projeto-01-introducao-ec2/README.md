# Introdução ao Amazon EC2

## Objetivo
Implementar e gerenciar uma instância de servidor web utilizando Amazon EC2, aplicando conceitos fundamentais de computação em nuvem como segurança, monitoramento e escalabilidade.

##  Serviços Utilizados
- Amazon EC2
- Security Group
- Amazon CloudWatch (monitoramento básico)
- Amazon EBS

##  Implementação

Durante este laboratório prático, foram realizadas as seguintes etapas:

1. Inicialização de uma instância EC2 com servidor web configurado.
2. Ativação da proteção contra encerramento para evitar exclusões acidentais.
3. Monitoramento da instância utilizando métricas básicas de desempenho.
4. Configuração e modificação do Security Group para permitir acesso HTTP (porta 80).
5. Redimensionamento da instância, simulando um cenário de escalabilidade.
6. Execução de testes para validação da proteção contra término.
7. Encerramento seguro da instância ao final do laboratório.

## Arquitetura da Solução
A solução consiste na utilização de uma instância EC2 como servidor web, onde o acesso é controlado por meio de um Security Group configurado para permitir tráfego HTTP. O armazenamento é gerenciado com EBS, enquanto o monitoramento da instância é realizado com ferramentas nativas da AWS. A proteção contra término adiciona uma camada extra de segurança operacional.

## Evidências

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/08bfdb7b-eef8-46c0-902a-92d22fe909fe" />


## 📚 Aprendizado
Este laboratório proporcionou uma experiência prática no uso do Amazon EC2, permitindo compreender não apenas a criação de instâncias, mas também aspectos essenciais como segurança, monitoramento e escalabilidade. A prática reforçou a importância da configuração correta de Security Groups e demonstrou como proteger recursos críticos contra exclusões acidentais em ambientes de nuvem.
