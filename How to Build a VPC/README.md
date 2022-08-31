# Steps to Building a VPC on AWS

![VPCs](https://user-images.githubusercontent.com/47668244/187684716-edce20ab-bf1a-4078-89f2-bb4b153ca13b.png)

## Step 1 - create a VPC

create vpc, with CIDR block 10.0.0.0/16

aws --> vpc --> click 'create vpc'

- vpc only

- naming convention: `eng122-christian-devops-vpc`

- CIDR block; `10.0.0.0/16`

- no IPv6 CIDR block

- tenancy; default

- add whatever tags you've like (it should )

assign your own ip for the CIDR - 10.0.4.0/24

## Step 2 - create internet, for the gateway

sidebar on the left --> internet gateway --> click 'create internet gateway'

naming gateway; `eng122-christian-devops-ig`

option 1: 

click; "attach to VPC"

option 2:

click actions --> attach to vpc --> select vpc & click attach

## Step 3 - create public subnet

sidebar on left --> subnets --> create subnet

select vpc to create subnet inside --> name subnet

naming convention: `eng122-christian-subnet-public`

- leave availability zones 'no preference'

- enter ipv4 CIDR block: `10.0.4.0/24`

## Step 4 - Route Table

Subnet doenst know where to connect to it

sidebar on left --> route tables --> create route table 

naming convention `eng122-christian-devops-rt`

select appropriate vpc


### Make Rules

However Now the route table is floating, it doesn't know where to connect to the subnet

edit routes / subnet association --> edit subnet associations --> select appropriate subnet we've create --> save associations

However, now it's only connected to the VPC, it doesn't give access to the internet gateway

edit routes --> add routes --> 

fill in the destination; `0.0.0.0/16`

fill in the target (type in internet gateway, and the option for the one you've created should appear, select it)

Now that we've set up our VPC, we can create or migrate our instances inside it; [like so!](https://aws.amazon.com/premiumsupport/knowledge-center/move-ec2-instance/)
