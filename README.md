# README

Creating infrastructure using Terraform and Ansible

### Install Ansible
1. Run the following commands:
```
# For Ubuntu/Debian-based systems
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### Generate a key-pair
1. Navigate to the `.ssh` folder of your home directory (ex: `~/.ssh`)
2. Run the following command to generate a key pair:
```
ssh-keygen -t ed25519 -f "aws"
```
- `-t` is the encryption method
- `-f` is the filename for your keys (our keys will be named `aws`) 
After running this command, you should see two new files in your `.ssh` folder: `aws.pub` (public key) and `aws` (private key)

### Add public key to AWS
1. Navigate to the `scripts` folder of the project directory (ex: `<insert_some_path_here>/acit-4640-lab_wk7/scripts`)
2. Run the following command to execute the import key script
```
./import_lab_key "~/.ssh/aws.pub"
```
We are passing in the `aws.pub` public key we made earlier as an argument into the script `import_lab_key` for it to add the key to our AWS account

### Perform Terraform configurations
1. Navigate to the `terraform` folder of the project directory (ex: `<insert_some_path_here>/acit-4640-lab_wk7/terraform)
2. Run the following terraform commands:

Initialize directory to run other terraform commands and install required plugins (for communicating with cloud service providers)
```
terraform init
```
After running this command, you should see a message in your terminal similar to "Terraform has been successfully initialized!"

Format the terraform file (`main.tf`) to match a standard style for consistency
```
terraform fmt
```

Check the infrastructure specifications from the terraform file for syntax errors
```
terraform validate
```

See what kinds of steps terraform would make to create the infrastructure described in the terraform file
```
terraform plan 
```

Create the infrastructure as described by the output of the `terraform plan` command
```
terraform apply
```

After running this command, you should see something similar to this:
```
Apply complete! Resources: 12 added, 0 changed, 0 destroyed.

Outputs:
instance_ip_addr = {
  "dns_name" = "ec2-35-92-238-140.us-west-2.compute.amazonaws.com"
  "dns_name-2" = "ec2-52-38-40-68.us-west-2.compute.amazonaws.com"
  "public_ip" = "35.92.238.140"
  "public_ip-2" = "52.38.40.68"
}
```

### Check Ansible playbook syntax
1. Navigate to the `ansible` folder of the project directory (ex: `<insert_some_path_here>/acit-4640-lab_wk7/ansible`)
2. Run the following command:
```
ansible-playbook playbook.yml --syntax-check
```

### Execute Ansible playbook
1. Navigate to the `ansible` folder of the project directory (ex: `<insert_some_path_here>/acit-4640-lab_wk7/ansible`)
2. Run the following command:
```
ansible-playbook -i inventory playbook.yml
```
After running the command, if your playbook syntax is valid then you should see something like: "playbook: playbook.yml"

### Nginx Home Page Screenshot
Couldn't make it in time `:(`
