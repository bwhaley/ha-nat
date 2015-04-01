# Packer template
A packer template to configure an HA NAT instance.

## Usage
Make sure to have [Packer](https://packer.io/) installed, then:

    export AMI_NAME="ha-nat" # What name to use for this AMI for viewing in the web console
    export AWS_ACCESS_KEY_ID=<your access key>
    export AWS_SECRET_ACCESS_KEY=<your secret key>
    export AWS_DEFAULT_REGION=us-east-1
    export SUBNET_ID=subnet-abcd1234 # VPC subnet ID for packer-created instance
    export BASE_AMI=ami-abcd1234 # [Ubuntu cloud image](https://cloud-images.ubuntu.com/trusty/). Use 64-bit HVM SSD
    export VPC_ID=vpc-abcd1234 # VPC ID for packer-created instance 
 
    /usr/local/bin/packer build \
        -var 'description=HA-NAT' \ 
        -var "aws_access_key=${AWS_ACCESS_KEY_ID}" \
        -var "aws_secret_key=${AWS_SECRET_ACCESS_KEY}" \
        -var "region=${AWS_DEFAULT_REGION}" \
        -var base_ami="${BASE_AMI}" \
        -var "subnet_id=${SUBNET_ID}" \
        -var "vpc_id=${VPC_ID}" \
        -var "ami_name=${AMI_NAME}" \
        packer/ha-nat.json


