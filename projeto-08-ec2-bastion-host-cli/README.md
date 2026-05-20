# Arquitetura com EC2 Bastion Host e Provisionamento via AWS CLI

## Problema

O desafio deste laboratório foi compreender como criar uma arquitetura que permitisse acesso seguro aos recursos em nuvem e, ao mesmo tempo, automatizar a criação de novos servidores. Em ambientes corporativos, realizar configurações manualmente pode aumentar o risco de erros, além de dificultar a padronização e a escalabilidade da infraestrutura.

## Objetivo

Meu objetivo foi criar uma arquitetura utilizando um Bastion Host com Amazon EC2 e realizar o provisionamento automatizado de uma segunda instância por meio da AWS CLI, aplicando conceitos de segurança e automação.

## Solução

Para resolver esse desafio, criei uma instância EC2 atuando como Bastion Host, que serviu como ponto seguro de acesso ao ambiente. Configurei permissões por meio de Security Groups e associei uma Role IAM para permitir a utilização da AWS CLI. Em seguida, utilizei comandos para recuperar informações necessárias, como a AMI mais recente, sub-redes e grupos de segurança. Também realizei o provisionamento automatizado de uma nova instância EC2, configurando automaticamente um servidor web por meio de um script User Data.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- Amazon EC2
- AWS CLI
- AWS Systems Manager (Parameter Store)
- Amazon VPC
- Security Groups
- Amazon Linux 2
- Bastion Host
- User Data
- IAM Role
- Automação de infraestrutura
- Provisionamento de recursos

## Evidências

<img width="1118" height="309" alt="Lab 171 1" src="https://github.com/user-attachments/assets/a50799d6-f225-482f-a454-cc3c8ab40c8d" />
<img width="1158" height="382" alt="Lab 171 2" src="https://github.com/user-attachments/assets/0bbe61f9-28cd-49f5-9a9c-613b5507b77d" />


## Script

```bash
# Definir região automaticamente
AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}

# Obter AMI mais recente
AMI=$(aws ssm get-parameters --names /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2 --query 'Parameters[0].[Value]' --output text)

# Obter Subnet
SUBNET=$(aws ec2 describe-subnets --filters 'Name=tag:Name,Values=Public Subnet' --query Subnets[].SubnetId --output text)

# Obter Security Group
SG=$(aws ec2 describe-security-groups --filters Name=group-name,Values=WebSecurityGroup --query SecurityGroups[].GroupId --output text)

# Baixar script de configuração
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RSJAWS-1-23732/171-lab-JAWS-create-ec2/s3/UserData.txt

# Criar instância Web Server
INSTANCE=$(aws ec2 run-instances \
--image-id $AMI \
--subnet-id $SUBNET \
--security-group-ids $SG \
--user-data file:///home/ec2-user/UserData.txt \
--instance-type t3.micro \
--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Web Server}]' \
--query 'Instances[*].InstanceId' \
--output text)

# Verificar status
aws ec2 describe-instances --instance-ids $INSTANCE --query 'Reservations[].Instances[].State.Name' --output text

# Obter DNS público
aws ec2 describe-instances --instance-ids $INSTANCE --query Reservations[].Instances[].PublicDnsName --output text
````
## Resultado

Ao final do laboratório, consegui criar uma arquitetura funcional com um Bastion Host como ponto seguro de acesso e provisionar automaticamente uma nova instância configurada como servidor web. Também validei a comunicação entre os recursos e confirmei o funcionamento correto do servidor por meio do acesso via navegador.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre segurança e automação em ambientes cloud. Aprendi a importância do Bastion Host para proteger acessos, além de compreender como a AWS CLI pode ser utilizada para automatizar processos e reduzir atividades manuais. Também entendi como recursos como User Data e recuperação dinâmica de informações contribuem para maior padronização, escalabilidade e eficiência na administração da infraestrutura.
