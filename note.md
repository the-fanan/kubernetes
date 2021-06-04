THINGS TO INSTALL
=====================
1. Kops (Minikube can be used if you want to just test locally)
2. AWS CLI [Install](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-mac.html#cliv2-mac-install-confirm)
3. Kubectl

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

TO LINK IAM USER WIT CLI
============================
1. run `aws configure`



create `cluster with kops: kops create cluster --name=fanankubernetes.com.ng --state=s3://kops-state-1lt --zones=eu-west-1a --node-count=2 --node-size=t3.micro --master-size=t3.micro --dns-zone=fanankubernetes.com.ng`

then `kops update cluster fanankubernetes.com.ng --yes --state=s3://kops-state-1lt`

then `kops export kubecfg --state=s3://kops-state-1lt`

incase user credentials are not returned `kops export kubecfg --admin`

then `kubectl get nodes`

`kubectl run hellow-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080`




