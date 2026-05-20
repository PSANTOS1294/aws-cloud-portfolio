# Projeto 12 - Automação com AWS CloudFormation

## Problema

O desafio deste laboratório foi compreender como criar e gerenciar infraestrutura em nuvem de forma automatizada. Em ambientes reais, criar recursos manualmente pode gerar inconsistências, aumentar o tempo de implantação e dificultar a padronização entre diferentes ambientes.

## Objetivo

Meu objetivo foi automatizar a criação de infraestrutura na AWS utilizando o AWS CloudFormation, permitindo o provisionamento de recursos de maneira consistente, reutilizável e escalável por meio de templates em YAML.

## Solução

Para resolver esse desafio, utilizei o AWS CloudFormation para definir a infraestrutura como código utilizando templates em YAML. Inicialmente, criei uma stack contendo recursos básicos como VPC, sub-rede e grupo de segurança. Em seguida, atualizei o template para adicionar um bucket S3 e posteriormente uma instância EC2 configurada com uma AMI dinâmica obtida pelo Systems Manager Parameter Store. Durante o processo, acompanhei a criação e atualização dos recursos até a validação da infraestrutura. Ao final, realizei a exclusão da stack, removendo automaticamente todos os recursos criados.

## Ferramentas

Tecnologias e recursos utilizados no projeto:

- AWS CloudFormation
- Amazon VPC
- Amazon EC2
- Amazon S3
- AWS Systems Manager (Parameter Store)
- YAML
- Infrastructure as Code (IaC)
- Stack
- Templates
- Automação de infraestrutura


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
## Resultado

Ao final do laboratório, consegui automatizar a criação completa de uma infraestrutura na AWS utilizando templates. Também realizei atualizações no ambiente adicionando novos recursos sem precisar recriar toda a estrutura, além de automatizar a remoção dos componentes ao finalizar o projeto.

## Aprendizados

Este laboratório me proporcionou uma experiência prática sobre infraestrutura como código e automação em ambientes cloud. Aprendi como o CloudFormation permite criar ambientes padronizados e reproduzíveis, reduzindo erros manuais e aumentando a eficiência do provisionamento. Também compreendi a importância do uso de templates reutilizáveis e da automação no gerenciamento do ciclo de vida da infraestrutura.
