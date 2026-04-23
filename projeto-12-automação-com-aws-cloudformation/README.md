# Projeto 12 - Automação com AWS CloudFormation

## Objetivo
Automatizar a criação de infraestrutura na AWS utilizando o AWS CloudFormation, permitindo provisionamento consistente, reproduzível e escalável por meio de templates em YAML.

---

## Serviços utilizados
- AWS CloudFormation
- Amazon VPC
- Amazon EC2
- Amazon S3
- AWS Systems Manager (Parameter Store)

---

## Implementação

### Etapa 1: Criação da Stack inicial
- Upload do template `task1.yaml`
- Criação de:
  - VPC
  - Sub-rede
  - Grupo de segurança
- Acompanhamento via aba **Events** e **Resources**

### Etapa 2: Adição do S3
- Edição do template YAML
- Inclusão de um bucket S3 na seção `Resources`
- Atualização da stack existente
- Validação via **UPDATE_COMPLETE**

### Etapa 3: Adição de EC2
- Inclusão de parâmetro dinâmico para AMI via Parameter Store
- Criação de instância EC2 com:
  - AMI dinâmica
  - Tipo t3.micro
  - Security Group existente
  - Sub-rede pública
- Uso de `!Ref` para referenciar recursos existentes

### Etapa 4: Exclusão da Stack
- Remoção completa da infraestrutura
- Exclusão automática de todos os recursos criados

---

## Arquitetura da solução


<img width="2391" height="1142" alt="image" src="https://github.com/user-attachments/assets/3f2cc5d6-9326-4c57-81a5-8d094dadbe63" />




- Infraestrutura definida como código (IaC)
- Stack gerencia:
  - VPC
  - Sub-rede pública
  - EC2 (App Server)
  - Bucket S3
- Todos os recursos são criados e destruídos automaticamente

---

## Evidências

<img width="1325" height="504" alt="LAB 190" src="https://github.com/user-attachments/assets/fa137d99-53f6-4818-9d45-314cd53b5414" />
<img width="890" height="346" alt="LAB 190 1" src="https://github.com/user-attachments/assets/8f7ca55f-4209-46e4-b48e-66535822b9cd" />
<img width="1348" height="487" alt="LAB 190 3" src="https://github.com/user-attachments/assets/9e7cf18f-1488-44c5-a5c0-3b3fc87b53c8" />


---

## Script

### Exemplo - Adição do bucket S3
```yaml
Resources:
  S3Bucket:
    Type: AWS::S3::Bucket
````
## Parâmetro para AMI dinâmica
```yaml
Parameters:
  AmazonLinuxAMIID:
    Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
    Default: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2
````
## Exemplo - Instância EC2
```yaml
Resources:
  EC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: !Ref AmazonLinuxAMIID
      InstanceType: t3.micro
      SecurityGroupIds:
        - !Ref AppSecurityGroup
      SubnetId: !Ref PublicSubnet
      Tags:
        - Key: Name
          Value: App Server
````
## Aprendizado

- Infraestrutura como código (IaC) na prática
- Uso de templates YAML no CloudFormation
- Criação e atualização de stacks
- Referência entre recursos com !Ref
- Uso do Parameter Store para AMIs dinâmicas
- Gerenciamento automatizado do ciclo de vida da infraestrutura
