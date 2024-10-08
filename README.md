# devopsified-MERN-web-app

A Web Application has 3 tiers.

Example: MERN Stack Application(Javascript family): 
- Database: MongoDB: Database ExpressJS, 
- Front-end/Presentation layer: ReactJS
- Back-end/Business-logic layer: NodeJS(using Framework "Express JS")NodeJS is used for servering and deployment part. 


<<<Architecture>>>

Part 1: 
Automated Infra

(using Jenkins and ArgoCD, this MERN Stack Application will be deployed on
EKS Cluster)

> On an Ec2 instance, we will install Jenkins and Terraform. Using Jenkins we will runs terraform scripts which will create private VPC on AWS. 

> Within VPC, an EKS Cluster will be created which will have 2 nodes(Worker Node 1 and Worker Node2)and a Jump server to connect to EKS Cluster to perform an Administrative activities on cluster. 
> Only Jump server will have access to EKS Cluster and no-one else.


Part 2: 
Implement a Comprehensive CI/CD using Jenkins and ArgoCD. 

-Jenkins CI part will have multiple stages as: 
> checkout code from Git-repo.
> Code Quality Analysis using SonarQube and also do Gating
> Dependency Check using OWASP
> File Scan 
> Build Docker image
> Pushing to ECR private Repo(instead of public registry like DockerHub)
> ECR Image scan i.e Docker image scan using Trivy
> Update the new version of image which is pushed to ECR, to K8s manifests
> Docker file for Front-end,back-end. Not for DB because MongoDB docker image is already available publicly. 

- CD
> Deploy the K8s manifest onto EKS Cluster using ArgoCD.


Part 3: 
> How to use custom domain and integrate it with Route 53 of AWS. 
> Setup Prometheus and use it as a Data-source to visualize complete observability metrics using Grafana. 
  

