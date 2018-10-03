# terraform-prime
Super lightweight wrapper over terraform to allow `${var.*****}` inside backends. This allows for flatter folder structure in your terraform projects.

- [hashcorp/terraform#13022](https://github.com/hashicorp/terraform/issues/13022)
- [hashcorp/terraform#17288](https://github.com/hashicorp/terraform/issues/17288)

## Getting Started

### Prerequisites
- `terraform` must be installed. `$ brew install terraform`

### Installing
Copy `terraform-prime` to `/usr/local/bin/` and ensure its executable (`chmod u+x /usr/local/bin/terraform-prime`).

Update `bashrc` to include `alias tf=terraform-prime`

## Running the test
Run `tf test production`. Check `terraform` configuration has all variables replaced.

## Running
To allow deploying between ... ** TODO
```bash
environments
|- app
|  |- env.production.tfvars
|  |- env.staging.tfvars
|  |- terraform.tfvars
|  |- main.tf
```

env.production.tfvars
```hcl-terraform
environment=production
```

terraform.tfvars
```hcl-terraform
name=appname
profile=codename
```

main.tf
```hcl-terraform
terraform {
  backend "s3" {
    bucket         = "terraform-state-${var.name}"
    key            = "${var.environment}/account/terraform.tfstate"
    region         = "us-east-1"
    profile        = "${var.profile}"
    dynamodb_table = "terraform-state-${var.name}"
  }
}

...
```
### Running
```bash
$ tf init staging
# tf {action} {environment} [args]
$ tf plan staging
# clear current env cache
$ tf clear
# clear and init env
$ tf switch production
```

## Built With
- bash
- [terraform](https://www.terraform.io/)

## Contributing

## Versioning

## Authors
- [will Farrell](https://github.com/willfarrell)

## License
This project is licensed under the MIT License - see the [LICENSE]() file for details

## TODO
- [ ] Streamline installation (brew?)
- [ ] recursively check for tfvars in parent dirs
