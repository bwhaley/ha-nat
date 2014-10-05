# Packer template
A packer template that runs an Ansible provisioner.

## Usage
Run from the root of the repo.

    /usr/local/bin/packer build -var 'description=NAT AMI Ansible 1.7.1 Ubuntu 14.04 EBS HVM' -var "aws_access_key=${AWS_ACCESS_KEY_ID}" -var "aws_secret_key=${AWS_SECRET_ACCESS_KEY}"  -var "region=${AWS_DEFAULT_REGION}" -var base_ami="${UBUNTU_CLOUD_AMI}" -var "subnet_id=${SUBNET_ID}" -var "vpc_id=${VPC_ID}" -var "ami_name=NAT" packer/ha-nat.json

Variables:

* `AMI_NAME` - What name to use for this AMI for viewing in the web console
* `AWS_ACCESS_KEY_ID` - Access key for packer IAM
* `AWS_SECRET_ACCESS_KEY` - Secret key for packer IAM
* `AWS_DEFAULT_REGION` - Region for new AMI
* `SUBNET_ID` - VPC subnet ID for packer-created instance
* `UBUNTU_CLOUD_AMI` - [Ubuntu cloud image](https://cloud-images.ubuntu.com/trusty/). Must be of type HVM SSD.
* `VPC_ID` - VPC ID for packer-created instance
