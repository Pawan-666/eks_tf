
### VPC as the Core:
All resources (subnets, internet gateway, NAT gateways, route tables) are created within or attached to the VPC (aws_vpc.main).

Subnets:

Private Subnets: Created for internal resources; they use private route tables with NAT gateways for outbound internet access.
Public Subnets: Created for resources needing direct internet access; they automatically assign public IPs and use the public route table.


Internet & NAT Gateways:

The Internet Gateway attached to the VPC provides internet connectivity for public subnets.
NAT Gateways (deployed in public subnets and assigned Elastic IPs) enable private subnets to communicate with the internet securely.


Route Tables & Associations:

Public subnets are tied to a single public route table that directs traffic to the Internet Gateway.
Each private subnet is tied to its own route table, which directs traffic to the corresponding NAT gateway.
This setup is a typical configuration for an EKS cluster where you need both public endpoints (for load balancers and other public services) and private subnets (for worker nodes or other internal resources), while still allowing private resources to access the internet via NAT.







