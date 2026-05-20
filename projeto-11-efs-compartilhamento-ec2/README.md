# Projeto 11 — Compartilhamento de Arquivos com Amazon EFS

## Problema

O desafio deste laboratório foi compreender como disponibilizar armazenamento compartilhado entre diferentes servidores em um ambiente de nuvem. Em cenários reais, aplicações distribuídas frequentemente precisam acessar os mesmos arquivos simultaneamente, exigindo uma solução centralizada, escalável e persistente.

## Objetivo

Meu objetivo foi implementar um sistema de armazenamento compartilhado utilizando o Amazon EFS, permitindo que múltiplas instâncias EC2 acessassem e manipulassem os mesmos arquivos de forma simultânea.

## Solução

Para resolver esse desafio, criei uma VPC com sub-redes e implementei três instâncias EC2 distribuídas em diferentes Zonas de Disponibilidade. Em seguida, criei um sistema de arquivos utilizando o Amazon EFS e realizei sua montagem em duas instâncias EC2. Após a configuração, executei testes para validar o compartilhamento, verificando que arquivos criados em uma instância também estavam disponíveis na outra, confirmando o funcionamento do armazenamento compartilhado.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon VPC
- Amazon EC2
- Amazon EFS
- AWS CLI
- Terminal Linux
- EC2 Instance Connect
- Secure Shell (SSH)
- Armazenamento compartilhado
- Sistema de arquivos distribuído
- Persistência de dados

## Arquitetura da solução
<img width="1536" height="1024" alt="Diagrama Arquitetura Lab 10 04" src="https://github.com/user-attachments/assets/03991c06-36c9-43f3-8e45-c149ce647d71" />


A arquitetura consiste em:

- Uma VPC com sub-redes públicas
- Três instâncias EC2
- Um sistema de arquivos Amazon EFS
- Duas instâncias montando o mesmo EFS simultaneamente

Isso permite armazenamento compartilhado e persistente entre servidores.

---

## Evidências


### VPC e Sub-redes criadas e configuradas com IPV4 automático
<img width="1346" height="408" alt="Lab 10 04 - 1" src="https://github.com/user-attachments/assets/c2ee514c-8e97-4e61-bb14-3ef66be88e80" />

### Grupo de segurança criado
<img width="1344" height="341" alt="Lab 10 04 - 2" src="https://github.com/user-attachments/assets/1c7737d8-9f5e-4f6a-a807-94f6e6a174d7" />

### Sistema de arquivos EFS criado
<img width="1353" height="476" alt="Lab 10 04 - 3" src="https://github.com/user-attachments/assets/e75e778c-c50a-420a-bcd7-6f60fc81641c" />

### Conexão via Secure Shell
<img width="1321" height="569" alt="Lab 10 04 - 4" src="https://github.com/user-attachments/assets/9954c3ac-b255-40c4-8835-c237113496fd" />

### Verificação com df -h
<img width="1361" height="574" alt="Lab 10 04 - 5" src="https://github.com/user-attachments/assets/82945d6c-bf8c-4147-8665-e4ea5e83d14f" />

### As 3 instâncias criadas e configuradas
<img width="1366" height="725" alt="Lab 10 04 - 6" src="https://github.com/user-attachments/assets/d403089e-4763-46f6-afea-deb1bc5e72df" />


---

## Script

Comandos utilizados para montar o EFS:

```bash
sudo -s
yum -y update
yum install -y amazon-efs-utils

mkdir financeiro

sudo mount -t efs -o tls fs-0bfdadb3e6d87f951.efs.us-west-2.amazonaws.com:/ financeiro

df -h
````
## Resultado

Ao final do laboratório, consegui implementar um sistema de armazenamento compartilhado funcional entre diferentes instâncias EC2. Também validei o acesso simultâneo aos mesmos arquivos, demonstrando o funcionamento correto do Amazon EFS em um ambiente distribuído.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre armazenamento compartilhado em ambientes cloud. Aprendi a diferença entre armazenamento local e distribuído, além de compreender como o Amazon EFS pode ser utilizado para permitir acesso simultâneo a arquivos entre diferentes servidores. Também entendi a importância desse tipo de solução em arquiteturas escaláveis, resilientes e que exigem compartilhamento contínuo de dados.
