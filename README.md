# terraform-prime
Super lightweight wrapper over terraform to allow `${var.*****}` inside backends. This allows for flatter folder structure in your terraform projects.

## Getting Started

### Prerequisites
- `terraform` must be installed. `$ brew install terraform`

### Installing
Copy `terraform-prime` to `/usr/local/bin/` and ensure its executable (`chmod u+x /usr/local/bin/terraform-prime`).

Update `bashrc` to include `alias tf=terraform-prime`

## Running the test
Uncomment debug line and run `tf plan master`. Check `terraform` configuration has all variables replaced.

## Deploying
To allow deploying between ... ** TODO
```bash
environments
|- app
|  |- env.production.tfvars
|  |- env.staging.tfvars
|  |- terraform.tfvars
|  |- main.tf
```

### Running
```bash
# tf {action} {environment} [args]
$ tf plan production
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
