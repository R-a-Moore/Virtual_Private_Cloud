# Steps to Building a VPC on AWS

![VPCs](https://user-images.githubusercontent.com/47668244/187684716-edce20ab-bf1a-4078-89f2-bb4b153ca13b.png)

## Step 1 - create a VPC

![create new vpc](https://user-images.githubusercontent.com/47668244/187734352-4d1c0918-8ded-474c-a3c2-fc90f9cf0cb0.png)

create vpc, with CIDR block 10.0.0.0/16

aws --> vpc --> click 'create vpc'

- vpc only

- naming convention: `eng122-christian-devops-vpc`

- CIDR block; `10.0.0.0/16`

- no IPv6 CIDR block

- tenancy; default

- add whatever tags you've like (it should )

![vpc settings](https://user-images.githubusercontent.com/47668244/187734387-14a6f6b7-e096-4c81-9eba-067cadb21430.png)


## Step 2 - create internet, for the gateway

sidebar on the left --> internet gateway --> click 'create internet gateway'

naming gateway; `eng122-christian-devops-ig`

option 1: 

click; "attach to VPC"

option 2:

click actions --> attach to vpc --> select vpc & click attach

## Step 3 - create public subnet

![create new subnet](https://user-images.githubusercontent.com/47668244/187734415-583653cd-367b-49cd-a233-3a8fa9df4b33.png)

sidebar on left --> subnets --> create subnet

select vpc to create subnet inside --> name subnet

naming convention: `eng122-christian-subnet-public`

- leave availability zones 'no preference'

- enter ipv4 CIDR block: `10.0.4.0/24`

![subnet settings](https://user-images.githubusercontent.com/47668244/187734461-8460b085-6b67-42c1-939c-6a90e89488f0.png)

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

fill in the destination; `0.0.0.0/0`

fill in the target (type in internet gateway, and the option for the one you've created should appear, select it)

![route table settings](https://user-images.githubusercontent.com/47668244/187734611-49974905-5dca-424c-937c-40dbf5bbc239.png)

Now that we've set up our VPC, we can create or migrate our instances inside it; [like so!](https://aws.amazon.com/premiumsupport/knowledge-center/move-ec2-instance/)

### In Case of Error

there may be the case that you are unable to SSH into your instance, then it may be the case that you haven't allowed the appropriate IPs (i.i, `0.0.0.0/0`) on your route table. 

However, note that this should only be for your public subnets. You don't want to have free access to a private subnet, it negates it being called a 'private subnet' in the first place.
