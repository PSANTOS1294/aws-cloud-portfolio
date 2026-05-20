# Instalação e Configuração da AWS CLI

## Problema

O desafio deste laboratório foi compreender como realizar a conexão e o gerenciamento de recursos da AWS por meio de linha de comando. Em ambientes profissionais, muitas atividades são executadas utilizando ferramentas automatizadas e comandos, tornando necessário entender como configurar acessos seguros e interagir com os serviços de forma eficiente.

## Objetivo

Meu objetivo foi instalar e configurar a AWS Command Line Interface (AWS CLI) em uma instância Linux Red Hat, utilizando um ambiente Windows para acesso remoto, permitindo a comunicação com serviços da AWS por meio de comandos e autenticação segura.

## Solução

Para resolver esse desafio, acessei uma instância EC2 baseada em Linux Red Hat por meio de conexão SSH utilizando o PuTTY. Em seguida, realizei a instalação da AWS CLI, validei seu funcionamento e configurei credenciais de acesso utilizando informações fornecidas pelo IAM. Após a configuração, executei comandos para interagir com recursos da AWS e validar a comunicação com os serviços disponíveis.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- AWS Command Line Interface (AWS CLI)
- AWS Identity and Access Management (IAM)
- Amazon VPC
- SSH
- PuTTY
- Linux Red Hat
- Gerenciamento por linha de comando
- Controle de acesso
- 
## Evidências

<img width="658" height="419" alt="LAB 168 1" src="https://github.com/user-attachments/assets/27b34ab8-32d8-4e99-8d3f-420c61fed8fb" />
<img width="644" height="338" alt="LAB 168 2" src="https://github.com/user-attachments/assets/7a9ae87a-5638-4787-8ebe-22381eaa2d77" />


## Script
```bash
# Download da AWS CLI
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

# Descompactar
unzip -u awscliv2.zip

# Instalar
sudo ./aws/install

# Verificar instalação
aws --version

# Ajuda da CLI
aws help

# Configurar credenciais
aws configure

# Testar acesso ao IAM
aws iam list-users
```
## Resultado

Ao final do laboratório, consegui instalar e configurar a AWS CLI em uma instância Linux, estabelecendo uma conexão segura com a AWS e realizando interações com recursos por meio de comandos. Também validei o acesso utilizando credenciais configuradas corretamente.

## Aprendizados

Este laboratório me proporcionou uma experiência prática no uso da AWS CLI e reforçou a importância das ferramentas de linha de comando em ambientes de computação em nuvem. Aprendi como realizar conexões remotas seguras, configurar autenticação utilizando o IAM e executar comandos para administrar recursos da AWS. Além disso, compreendi como esse tipo de ferramenta pode aumentar a produtividade e facilitar tarefas administrativas em ambientes cloud.
