# **AZURE TERRAFORM - GET STARTED**
### **Requirements**
1. [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
2. [Azure CLI logged in](https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli)
3. [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
### **How To**
> In this example we will using Azure **rbac** to authenticate our terraform
1. Use this command to get your subscription id
```
az account list --output table
```
2. Use this command to create rbac role(replace "your_subscription_id" with yours)
```
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/your_subscription_id"
```
3. Here is output for rbac, save **appId**, **password**, and **tenant**
```
{
  "appId": "---",
  "displayName": "---",
  "name": "---",
  "password": "---",
  "tenant": "---"
}
```
4. Create new file with name **terraform.tfvars**, write information below inside that file
```
subscription_id = "your_subscription_id"
client_id       = "appId"
client_secret   = "password"
tenant_id       = "tenant"
```
5. Init Terraform
```
terraform init
```
6. Apply Terraform
```
terraform apply -input=false -auto-approve
```
