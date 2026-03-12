![SUBINDO CONFIGURAÇÕES](https://github.com/user-attachments/assets/2569e8af-3b8f-4c74-9ddd-edfbeb9a53c0)
![CONFIGURAÇÃO CIRD E ZONA](https://github.com/user-attachments/assets/92b500ad-3f51-4cf0-a966-0a7296a4a242)
![CRIAÇÃO VPC](https://github.com/user-attachments/assets/4a4a48c7-c6bb-4f95-b349-da73151929bc)
![Resultado](https://github.com/user-attachments/assets/943340a2-b7ec-40ec-a88d-038314aa2cd1)
![VPC](https://github.com/user-attachments/assets/d587eaa6-a198-4cb9-bec3-ba1e5fd081c1)
![Security Group](https://github.com/user-attachments/assets/153ce1ec-5990-496a-a382-82b73893fdf6)
![WhatsApp Image 2026-03-12 at 15 21 21](https://github.com/user-attachments/assets/4f7d7f52-0347-4df7-b5bf-c51dd21504f3)
![Criação EC2](https://github.com/user-attachments/assets/6e0ba19e-0347-4bf2-8527-8ffb7e798b65)
Laboratório AWS – VPC + Servidor Web EC2

Este projeto demonstra a criação de uma infraestrutura de rede na AWS utilizando Amazon VPC, subnets, tabelas de rotas e EC2 para implantação de um servidor web.

Visão Geral da Arquitetura

O ambiente criado no laboratório inclui:

1 VPC (10.0.0.0/16)

2 Availability Zones

2 Subnets Públicas

2 Subnets Privadas

Internet Gateway

NAT Gateway

Route Tables

Security Group

Instância EC2 com servidor web

Essa arquitetura representa um modelo básico de rede em cloud, utilizado em ambientes reais para garantir organização, segurança e escalabilidade.

Configuração da Rede
VPC

CIDR Block: 10.0.0.0/16

Subnets Públicas

10.0.0.0/24

10.0.2.0/24

As subnets públicas possuem rota para o Internet Gateway, permitindo acesso direto à internet.

Subnets Privadas

10.0.1.0/24

10.0.3.0/24

As subnets privadas utilizam um NAT Gateway para acessar a internet de forma segura sem exposição direta.

Security Group

Foi criado um Security Group atuando como firewall virtual para a instância EC2.

Regras de Entrada
Tipo	Protocolo	Porta	Origem
HTTP	TCP	80	0.0.0.0/0

Essa regra permite acesso ao servidor web através da internet.

Deploy do Servidor Web (EC2)

Configuração da instância:

AMI: Amazon Linux 2

Tipo de instância: t3.micro

Subnet: Pública

IP público: Habilitado

Script de inicialização (User Data)

O script abaixo foi utilizado para instalar e iniciar automaticamente um servidor web:

#!/bin/bash
yum install -y httpd mysql php
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
chkconfig httpd on
service httpd start
Conceitos Aplicados

Amazon VPC

Subnets públicas e privadas

Internet Gateway

NAT Gateway

Route Tables

Security Groups

Provisionamento de instâncias EC2

Automação com User Data

Autor

Leonardo Ferreira

Estudante de Infraestrutura, Redes, Cloud Computing e Segurança da Informação.
