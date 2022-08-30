# Virtual Private Cloud

Previously on the cloud, network space was shared (like a house-share apartment), however organisations wanted specific control and authority to diclose whom can and cannot traffic the network and access resources or specific infrastructure. Therefore they were given their own private network.

![AWS VPC](https://user-images.githubusercontent.com/47668244/187456426-f82a9d08-414d-468c-9678-450d80f78101.png)

### Defintion

A Virtual Private Cloud (VPC) is a virtual network (a segregated range of IPv4 addresses), which is logically isolated from other virtual networks on the AWS cloud.

VPCs allow for us as a DevOps engineers / or an organisation to have control over the traffic on our cloud infrastructure that we're using, by segregating it from infrastructure which we do not own or individuals (requests) which we do not have control of.

![VPCs](https://user-images.githubusercontent.com/47668244/187456485-d0e39b3f-7efa-40b1-9b43-0d6dacab90d2.png)

## Subnet/s

Where the private cloud (network), is divied up, into public and private subnets, the latter of which which allows for external sources to access relevant portions of the VPC. Think of it as a limited public space.

### Public Addresses

### Private Addresses


NACL

Security groups

route tables

### Internet Gateways

The port / access route through which external sources may enter/access the 


## CIDR Blocks 

- simply address/post code

When you create a VPC, you must dictate / specify the range of IPv4 addresses which you wish to segregate. This takes the form ofa Classless Inter-Domain Routing (CIDR) block. For example 10.0.0.0/16, would be the primary CIDR block for your VPC.

### Rules

- An IPv4 address is always 32 bits, with 4 groups of up to 3 decimal digits (from 0-255), separated by full-stops; 10.0.1.0
- An IPv4 CIDR block expands upon this by adding a forwards slash at the end - / followed by a number ranging from 0-32. For example; 10.0.0.0/16
