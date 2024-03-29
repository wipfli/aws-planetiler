# Workflow
Launches an EC2 instance on AWS and processes OpenStreetMap data with [Planetiler](https://github.com/onthegomap/planetiler)

OpenStreetMap stores and distributes data in a custom [file format](https://wiki.openstreetmap.org/wiki/OSM_file_formats).  [Planetiler](https://github.com/onthegomap/planetiler) transforms OpenStreetMap data into [Mapbox vector tiles](https://docs.mapbox.com/data/tilesets/guides/vector-tiles-introduction/) which can be consumed by map client libraries like [MapLibre GL JS](https://github.com/maplibre/maplibre-gl-js). To process data at the full planet scale, Planetiler requires a machine with 128 GB memory, 500 GB storage, and 32 CPUs. Rendering the planet should take 1 to 3 hours with these machine specs. 

The [`aws-planetiler.yml`](./.github/workflows/aws-planetiler.yml) workflow does the following three things:

 * Launch an [EC2](https://aws.amazon.com/ec2/) instance on AWS
 * Run planetiler
 * Copy rendered planet to `s3://planetiler/planet.mbtiles`

## GitHub Secrets

[GitHub secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets) are used to store configuration details.

The AWS EC2 instance on which Planetiler runs requires the following configuration details:

 * [`AWS_ACCESS_KEY_ID`](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
 * [`AWS_SECRET_ACCESS_KEY`](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)
 * `AWS_REGION` - the AWS datacenter region. E.g. `eu-west-1`
 * `AWS_IMAGE_ID` - the [Linux AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/finding-an-ami.html). E.g. `ami-1a2b3c4d`
 * `AWS_INSTANCE_TYPE` - the [instance type](https://aws.amazon.com/ec2/instance-types/). E.g. `m5d.8xlarge`
 * `AWS_KEY_NAME` - the name of the [EC2 key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html). E.g. `planetiler-key-pair`
 * `AWS_SSH_PRIVATE_KEY` - the ssh private key of `AWS_KEY_NAME`. E.g. content of `planetiler-key-pair.pem`
 * `AWS_SECURITY_GROUP_IDS` - the [security group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) id. Make sure to [enable ssh access](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#SG_Changing_Group_Membership). E.g. `sg-1a2b3c4d`
 * `AWS_SUBNET_ID` - the [subnet id](https://docs.aws.amazon.com/cli/latest/reference/ec2/describe-subnets.html). E.g. `subnet-1a2b3c4d`
