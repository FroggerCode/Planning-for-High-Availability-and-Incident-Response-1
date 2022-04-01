# Infrastructure

## AWS Zones
Identify your zones here

## Servers and Clusters

### Table 1.1 Summary
| Asset         | Purpose                                       			| Size       | Qty      | DR                            |        
|---------------|-------------------------------------------------------------|------------|----------|-------------------------------|
| EC2 Instance1 | App server in the primary region us-east-2 			| t3.micro   | 3        | Deployed in us-east-2		 |
| EC2 Instance2 | App server in secondary region us-west-1	 			| t3.micro   | 3        | Deployed in us-west for DR	 |
| EKS Cluster1  | Kubernetes monitoring cluster for us-east-2			| t3.medium  | 2 nodes  | Replicated in us-west-1	 |
| EKS Cluster2  | Kubernetes monitoring cluster for us-west-1			| t3.medium  | 2 nodes  | Deployed in us-west-1 for DR  |
| VPC		    | Logically isolated virtual network with IPs in av zones	|			     | Deployed in us-east-2         |
| VPC		    | Logically isolated virtual network with IPs in av zones	|			     | Deployed in us-west-1 for DR  |
| Load Balancer | Distribute traffic between the 3 EC2 instance in us-east-2  |                      | Deployed in us-east-2         |                        
| Load Balancer | Distribute traffic between the 3 EC2 instance in us-west-1  |                      | Deployed in us-west-1         |
| RDS Cluster1  | Primary database in us-east-2						| db.t2.small| 2 nodes | Deployed in us-east-2		 |
| RDS Cluster2  | Secondary database for georeplication in us-west-1		| db.t2.small| 2 nodes | Replicated in us-west-1 for DR|

### Descriptions
EC2 Instances - Virtual machines that handle run the applications.
EKS Cluster   - Nodes that are setup to monitor the EC2 instances using prometheus grafana to create dashboards and metrics.
VPC 		  - Virtual Private Cloud that allows AWS users to define logically isolated network to deploy in specific regions/zones for high availability.
Load Balancer - Distributes traffic dynamically between all EC2 app instances to prevent stress/high load.
RDS Cluster   - database that are highly available in two separate regions for georeplication.

## DR Plan
### Pre-Steps:
Verify all resources are available in both regions.
Check the load balancer configs
Verify the us-west-1 cluster is up to date and has been replicated



## Steps:
During a DR scenario that affects the primary region us-east-2 services would need to be switched over to the secondary region to achieve quick recovery.
1. Load Balancers to point to DR site
2. Database cluster will be swapped us-east-2 becomes the secondary us-west-1 becomes the primary
3. Validate the backup EC2 instance is pointed at the the new primary DB cluster in us-west-1.
4. Check Grafana to ensure traffic is moving in the US-west-1 region.
