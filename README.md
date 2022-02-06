# aws-planetiler
Launches an EC2 instance on AWS and processes OpenStreetMap data with Planetiler

## GitHub Secrets

 * [AWS_ACCESS_KEY_ID](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
 * [AWS_SECRET_ACCESS_KEY](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
 * AWS_REGION - the AWS datacenter region. E.g. `eu-west-1`
 * AWS_IMAGE_ID - the [Linux AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/finding-an-ami.html). E.g. `ami-1a2b3c4d`
 * AWS_INSTANCE_TYPE - the [instance type](https://aws.amazon.com/ec2/instance-types/). E.g. `t2.micro`
 * AWS_KEY_NAME - the name of the [EC2 key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). E.g. `planetiler-key-pair`
 * AWS_SSH_PRIVATE_KEY - the ssh private key of `AWS_KEY_NAME`. E.g. content of `planetiler-key-pair.pem`
 * AWS_SECURITY_GROUP_IDS - the [security group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) id. Make sure to [enable ssh access](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#SG_Changing_Group_Membership). E.g. `sg-1a2b3c4d`
 * AWS_SUBNET_ID - the [subnet id](https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-subnets.html). E.g. `subnet-1a2b3c4d`
