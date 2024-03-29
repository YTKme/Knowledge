# Terraform

## General Command

### Command: init
* [Documentation](https://www.terraform.io/cli/commands/init)

```bash
# Initialize a working directory
terraform -chdir="<directory/>" init
```

### Command: refresh
* [Documentation](https://www.terraform.io/cli/commands/refresh)

```bash
# Read the current setting and update
# The `-auto-approve` is optional
terraform -chdir="<directory/>" refresh -var-file="<directory/filename.tfvars>" [--auto-approve]
```

### Command: plan
* [Documentation](https://www.terraform.io/cli/commands/plan)

```bash
# Create an execution plan
terraform -chdir="<directory/>" plan -var-file="<directory/filename.tfvars>"
```

### Command: apply
* [Documentation](https://www.terraform.io/cli/commands/apply)

```bash
# Execute the action proposed
# The `-auto-approve` is optional
terraform -chdir="<directory/>" apply -var-file="<directory/filename.tfvars>" [-auto-approve]
```

### Command: destroy
* [Documentation](https://www.terraform.io/cli/commands/destroy)

```bash
# Destroy all remote object
# The `-auto-approve` is optional
terraform -chdir="<directory/>" destroy -var-file="<directory/filename.tfvars>" [--auto-approve]
```

### Command: fmt
* [Documentation](https://www.terraform.io/cli/commands/fmt)

```bash
# Rewrite Terraform configuration files to a canonical format and style
terraform -chdir="<directory/>" fmt
# Alternatively...
terraform fmt "<directory/>"
```