KOPS
=========
This is a tool that allows you to make k8s clusters on popular cloud providers. It is integrated with both AWS and Google Cloud (in beta).

Note on using Kops:
======================
1. You need to setup an IAM user to use kops with AWS
2. You need to create an s3 bucket to manage Kops state
3. You need to setup a domain name on Route 53 then Kops works with subdomains


TO SETUP IAM USER
=====================
1. Go to IAM on console
2. Go to Users
3. Create New user

TO LINK IAM USER WITH CLI
============================
1. run `aws configure`

USEFUL COMMANDS
==================
- `kops create cluster --name={NAME_OF_CLUSTER} --state=s3://{S3_BUCKET} --zones=eu-west-1a --node-count=2 --node-size=t3.micro --master-size=t3.micro --dns-zone={DNS_ZONE_ON_AWS_ROUTE_53}` creates a cluster with master and slave nodes

- `kops update cluster {NAME_OF_CLUSTER} --yes --state=s3://{S3_BUCKET}` update cluster configuration

- `kops export kubecfg --state=s3://{S3_BUCKET}` export cluster configuration

- incase user credentials are not returned `kops export kubecfg --admin` (!!UNSAFE FOR PRODUCTION!!)

- `kops validate cluster --wait 10m`
- `kops delete cluster --name ${NAME} --yes`