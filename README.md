# multi-cloud-kubernetes-cluster
This is to create a multi-cloud cluster by kubeadm using aws client vpn endpoint to put all instances on the same network in order to secure the trafic
The master is an aws ec2  
The workers are the clients of the vpn gcp vm and a local machine  
#### The infrastructure
<p align="center">
  <img src="ifra.gif" width="600" title="hover text">
</p>

### The requirements:
1- AWS account is mandatory to create the vpn endpoint, a GCP account is necessary but not mandatory  
2- Pre-deployed aws ec2:t2.micro not recomended (kubernetes requirements for cpu and memory) but it works if (--ignore-preflight-errors=Mem --ignore-preflight-errors=NumCpu) is specified in kubeadm init  
3- Pre-deployed GCP instance necessary but not mandatory  
4- AWS access key and secret acess key  
inside scripts you will find the documentation pages for each line
####Step 0 
Clone this repo  
```  
git clone https://github.com/devops-and-more/multi-cloud-kubernetes-cluster.git
```
####Step 1
Generate the certificates/keys for server/client of the vpn endpoint using script1.sh, the script will upload them using aws cli wich will be installed by the script also, it will propmt your aws access/secret keys, make sure to use the region of your aws ec2  
```
chmod +x script1.sh
./script1.sh
```
#####Note: script1 is diffrent than the doc in line that begins with command find, this line is equivalent to multiple line in the doc
#####Step2

