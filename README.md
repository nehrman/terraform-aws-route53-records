# AWS Route53 Records Terraform Module 

A Terraform module which allows creation and management of simple routing policy for Amazon Route53 Records.

This type of resource is supported :
- [ROUTE53 RECORDS - aws_route53_record](https://www.terraform.io/docs/providers/aws/r/route53_record.html)

# Features

The goal of this module is to give a standard way of creating and managing ROUTE53 Records.
The module supports, at the moment, only simple routing policy with :

- Zone ID
- Instance Names
- Instance IPs
- Record Type 
- Record TTL

## Terraform versions

Support of Terraform 0.12 is not yet implemented. (WIP)

If you are using Terraform 0.11 you can use versions `v1.*`.

## Usage

Simple DNS Record example : 

```hcl
data "aws_route53_zone" "zone" {
    name = "my-v-world.com"
}

module "aws_record_bastion" {
  source        = "app.terraform.io/<ORG_NAME>/route53-records/aws"
  zone_id       = "${data.aws_route53_zone.zone.zone_id}"
  instance_name = ["bastion"]
  instance_ip   = ["10.0.10.24"]
  record_type   = "A"
  record_ttl    = "300"
}
```

## Authors

* **Nicolas Ehrman** - *Initial work* - [Hashicorp](https://www.hashicorp.com)



