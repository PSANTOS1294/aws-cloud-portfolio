# Projeto: Gerenciamento de Recursos com Tags na AWS

## Problema

O desafio deste laboratório foi compreender como organizar e administrar recursos em ambientes cloud que possuem diversas instâncias e serviços ativos. Em cenários reais, identificar recursos manualmente pode se tornar complexo e aumentar a chance de erros, tornando necessária uma estratégia que facilite gerenciamento, automação e controle do ambiente.

## Objetivo

Meu objetivo foi utilizar tags para organizar, identificar e automatizar o gerenciamento de instâncias EC2, permitindo executar ações como busca, modificação, parada, inicialização e encerramento de recursos com base em critérios específicos.

## Solução

Para resolver esse desafio, utilizei uma instância central responsável pelo gerenciamento das demais instâncias por meio da AWS CLI e scripts automatizados. Realizei a identificação de recursos utilizando filtros baseados em tags como projeto, ambiente e versão. Também utilizei consultas avançadas para refinar resultados e criei scripts para automatizar alterações em lote, iniciar e interromper instâncias automaticamente e identificar recursos que não atendiam às regras definidas de conformidade.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- AWS CLI
- AWS SDK for PHP
- Amazon VPC
- Bash Script
- JMESPath
- Tags AWS
- Automação de infraestrutura
- Gerenciamento de recursos
- Governança em nuvem

## Arquitetura da solução

<img width="853" height="339" alt="image" src="https://github.com/user-attachments/assets/be957631-2804-4518-ba5d-f24b0eb29139" />


A solução consiste em uma VPC com sub-redes pública e privada contendo múltiplas instâncias EC2. Uma instância central (Command Host) executa comandos via AWS CLI e scripts automatizados que gerenciam as demais instâncias com base em suas tags.



## Evidências

### Listagem de instâncias filtradas por tags  

<img width="508" height="590" alt="lab 188 1" src="https://github.com/user-attachments/assets/ae8241bb-ea4a-4f2c-9b20-b074c3169c50" />

### Instâncias de desenvolvimento sendo paradas e iniciadas automaticamente  
<img width="834" height="459" alt="lab 188 2" src="https://github.com/user-attachments/assets/0ea70a81-d4f9-42e6-926a-d75c32e7fa89" />

<img width="1123" height="290" alt="lab 188 3" src="https://github.com/user-attachments/assets/b899dc19-a9ef-400b-b826-12422596d6e3" />

<img width="1031" height="94" alt="lab 188 4" src="https://github.com/user-attachments/assets/692f5e1f-d7d5-4a17-80ca-72f8c1f5ef42" />

### Instâncias sem tag `Environment` sendo identificadas e encerradas  
<img width="884" height="321" alt="lab 188 5" src="https://github.com/user-attachments/assets/56e9b334-4ab0-4fd1-85cd-f744e42fe107" />

---

## Script

### Alteração de tags em lote (Bash)
```bash
#!/bin/bash

ids=$(aws ec2 describe-instances \
--filter "Name=tag:Project,Values=ERPSystem" \
"Name=tag:Environment,Values=development" \
--query 'Reservations[*].Instances[*].InstanceId' \
--output text)

aws ec2 create-tags --resources $ids --tags 'Key=Version,Value=1.1'
````
### Parar instâncias por tag
```bash
./stopinator.php -t"Project=ERPSystem;Environment=development"
````
### Iniciar instâncias por tag
```bash
./stopinator.php -t"Project=ERPSystem;Environment=development" -s
````
### Encerrar instâncias sem conformidade
```bash
aws ec2 terminate-instances --instance-ids <ids>
````
## Resultado

Ao final do laboratório, consegui identificar, organizar e administrar instâncias EC2 utilizando tags como critério principal. Também automatizei ações de gerenciamento, como atualização de informações, parada, inicialização e encerramento de recursos, tornando a administração do ambiente mais eficiente.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre gerenciamento e organização de recursos em ambientes cloud. Aprendi como as tags podem facilitar a identificação de recursos e contribuir para automação e governança. Também compreendi a importância de utilizar filtros, scripts e políticas de conformidade para reduzir tarefas manuais, aumentar o controle sobre a infraestrutura e manter ambientes mais organizados e escaláveis.
