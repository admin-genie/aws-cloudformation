# AWS CloudFormation
📌실습 링크
[![Naver Blog Badge](https://img.shields.io/badge/Naver%20Blog-03C75A?style=flat&logo=Naver&logoColor=white)](https://blog.naver.com/genie290/223488576372)
---
## 1. 생성 리소스 요약
- 1 VPC
- 6 Subnets (2 Public, 4 Private)
- 1 Internet Gateway
- 1 NAT Gateway (with Elastic IP)
- 2 Route Tables (Public, Private)
- 6 Subnet Route Table Associations

## 2. 설정
#### VPC
- VPC (my-vpc-16) : CIDR 블록 10.1.0.0/16

#### Subnet
- Public Subnet A (my-public-subnet-a-16) : CIDR 10.1.1.0/26 in us-west-2a
- Public Subnet C (my-public-subnet-c-16) : CIDR 10.1.1.64/26 in us-west-2c
- Private Subnet App A (my-private-subnet-app-a-16) : CIDR 10.1.1.128/27 in us-west-2a
- Private Subnet App C (my-private-subnet-app-c-16) : CIDR 10.1.1.160/27 in us-west-2c
- Private Subnet DB A (my-private-subnet-db-a-16) : CIDR 10.1.1.192/27 in us-west-2a
- Private Subnet DB C (my-private-subnet-db-c-16) : CIDR 10.1.1.224/27 in us-west-2c

#### IGW & NAT
- Internet Gateway (IGW) : my-igw-16 (Attachigw 연결)
- Elastic IP (EIP) : my-eip-16
- NAT Gateway (NGW) : my-ngw-16 (Public Subnet A에 위치)

#### RT
- Public Route Table (my-public-rt-16)
  - Public Route : 인터넷 게이트웨이를 통해 외부와 연결 (0.0.0.0/0)
  - Public Subnet A, C와 연결됨
- Private Route Table (my-private-rt-16)
  - Private Route : NAT 게이트웨이를 통해 외부와 연결 (0.0.0.0/0)
  - Private Subnet App A, App C, DB A, DB C와 연결됨

#### RT Associations
- Public Subnets
  - PublicSubnetARTAssociation → Public Subnet A와 Public Route Table 연결
  - PublicSubnetCRTAssociation → Public Subnet C와 Public Route Table 연결
- Private Subnets
  - PrivateSubnetAppARTAssociation → Private Subnet App A와 Private 
  - Route Table 연결
  - PrivateSubnetAppCRTAssociation → Private Subnet App C와 Private 
  - Route Table 연결
  - PrivateSubnetDbARTAssociation → Private Subnet DB A와 Private 
  - Route Table 연결
  - PrivateSubnetDbCRTAssociation → Private Subnet DB C와 Private Route Table 연결

#### AWS my-vpc-16 리소스 맵 화면
![AWS CloudFormtaion](https://github.com/user-attachments/assets/8f90ee6a-3cf8-40d9-a6a3-a9eb20959f6e)
