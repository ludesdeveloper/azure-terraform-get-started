# **AZURE TERRAFORM - GET STARTED**
### **Requirements**
1. [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)
2. [Azure CLI logged in](https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli)
3. [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)
### **How To**
> In this example we will using Azure **rbac** to authenticate our terraform. [Several ways to login azure via terraform](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/service_principal_client_secret)
1. Clone repository
```
git clone https://github.com/ludesdeveloper/azure-terraform-get-started.git
```
2. Change directory
```
cd azure-terraform-get-started
```
3. Use this command to get your subscription id
```
az account list --output table
```
4. Use this command to create rbac role(replace "your_subscription_id" with yours)
```
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/your_subscription_id"
```
5. Here is output for rbac, save **appId**, **password**, and **tenant**
```
{
  "appId": "---",
  "displayName": "---",
  "name": "---",
  "password": "---",
  "tenant": "---"
}
```
6. Create new file with name **terraform.tfvars**, write information below inside that file
```
subscription_id = "your_subscription_id"
client_id       = "appId"
client_secret   = "password"
tenant_id       = "tenant"
```
7. Init Terraform
```
terraform init
```
8. Apply Terraform
```
terraform apply -input=false -auto-approve
```
