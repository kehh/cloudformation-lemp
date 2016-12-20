# CloudFormation LEMP

This project contains AWS CloudFormation templates for a LEMP stack configuration that meets the following requirements:

* High availability
* Web load balancing
* Auto-scaling (unfinished!)
* Administrative access via a bastion host
* Public and private subnets in a VPC

## Design

The VPC template creates public and private subnets in two different availability zones. The public subnets have a route to the Internet via an Internet gateway. The private subnets have a route to Internet via a single NAT gateway.

The Bastion template creates an SSH entry point to the network.

The App template creates a public ELB, an auto-scaling group of app/web servers and an RDS instance.

## Configuration

Rather than take an overwhelming number of parameters, these templates are designed to be forked for your project before starting work. Once you have your own fork,

1. Customize the mappings for settings like subnetworks, instance types, and AMIs. These project-specific settings are captured in the Mappings objects in the templates
1. Customize the bootstrap script to suit your deployment. The example bootstrap script deploys the latest WordPress but you almost certainly will want to do something more useful
1. Create your release S3 bucket
1. Copy files to your release bucket. The application template expects to find the bootstrap script at {release bucket}/{release id}/bootstrap

## Usage

1. Deploy 1-VPC.template as a stack
1. Deploy 2-Bastion.template as a stack
1. Deploy 3-App.template as a stack

## Contributing

Bug reports and pull requests are welcome on GitHub at [thecoderhythm/cloudformation-lemp](https://github.com/thecoderhythm/cloudformation-lemp)