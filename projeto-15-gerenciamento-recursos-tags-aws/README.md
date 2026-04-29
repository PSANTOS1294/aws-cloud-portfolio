# Projeto: Gerenciamento de Recursos com Tags na AWS



## Objetivo
Utilizar tags para organizar, identificar e automatizar o gerenciamento de instâncias EC2, incluindo ações como busca, modificação, parada, inicialização e encerramento de recursos com base em critérios definidos.

---

## Serviços utilizados
- Amazon EC2  
- AWS CLI  
- AWS SDK for PHP  
- Amazon VPC  

---

## Implementação
- Acesso à instância **Command Host** com AWS CLI configurada  
- Identificação de instâncias via filtros de tags (`Project`, `Environment`, `Version`)  
- Uso de **JMESPath** para formatar e refinar resultados  
- Criação e execução de script Bash para alterar tags em lote  
- Uso do script **stopinator.php** para parar e iniciar instâncias automaticamente  
- Execução de script para detectar e encerrar instâncias sem tag obrigatória (`Environment`)  

---

## Arquitetura da solução

<img width="853" height="339" alt="image" src="https://github.com/user-attachments/assets/be957631-2804-4518-ba5d-f24b0eb29139" />


A solução consiste em uma VPC com sub-redes pública e privada contendo múltiplas instâncias EC2. Uma instância central (Command Host) executa comandos via AWS CLI e scripts automatizados que gerenciam as demais instâncias com base em suas tags.

---

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
## Aprendizado
Neste laboratório, aprendi na prática como as tags são fundamentais para organizar e gerenciar recursos na AWS de forma escalável. Entendi como utilizar a AWS CLI com filtros e consultas avançadas (JMESPath) para localizar instâncias específicas, além de automatizar ações como alteração de tags, parada e inicialização de recursos. Também compreendi como implementar políticas de segurança baseadas em conformidade, como o conceito de “tag-or-terminate”, que garante que apenas recursos devidamente identificados permaneçam ativos, reforçando governança e controle em ambientes cloud.
