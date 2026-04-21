To create a Virtual Machine using Terraform on Azure Cloud with input and output variable files.

⚙️ Requirements
Terraform installed
Azure CLI installed
Azure student account
Logged in using:
az login
📘 Theory

Terraform is an Infrastructure as Code (IaC) tool used to create and manage cloud resources using configuration files.

📁 Project Structure
terraform-vm/
│── main.tf
│── variables.tf
│── terraform.tfvars
│── outputs.tf
🧾 1. main.tf (Core Infrastructure)
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = var.resource_group_name
  location = var.location
}

resource "azurerm_virtual_network" "vnet" {
  name                = "myVnet"
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name
  address_space       = ["10.0.0.0/16"]
}

resource "azurerm_subnet" "subnet" {
  name                 = "mySubnet"
  resource_group_name  = azurerm_resource_group.rg.name
  virtual_network_name = azurerm_virtual_network.vnet.name
  address_prefixes     = ["10.0.1.0/24"]
}

resource "azurerm_network_interface" "nic" {
  name                = "myNIC"
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name

  ip_configuration {
    name                          = "internal"
    subnet_id                     = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic"
  }
}

resource "azurerm_linux_virtual_machine" "vm" {
  name                = var.vm_name
  resource_group_name = azurerm_resource_group.rg.name
  location            = azurerm_resource_group.rg.location
  size                = "Standard_B1s"

  admin_username      = var.admin_username
  admin_password      = var.admin_password
  disable_password_authentication = false

  network_interface_ids = [
    azurerm_network_interface.nic.id
  ]

  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Standard_LRS"
  }

  source_image_reference {
    publisher = "Canonical"
    offer     = "UbuntuServer"
    sku       = "18.04-LTS"
    version   = "latest"
  }
}
🧾 2. variables.tf (Input Variables)
variable "resource_group_name" {
  type        = string
  description = "Resource Group Name"
}

variable "location" {
  type        = string
  description = "Azure Region"
}

variable "vm_name" {
  type        = string
  description = "Virtual Machine Name"
}

variable "admin_username" {
  type        = string
  description = "VM Username"
}

variable "admin_password" {
  type        = string
  description = "VM Password"
}
🧾 3. terraform.tfvars (Input Values)
resource_group_name = "myTerraformRG"
location            = "centralindia"
vm_name             = "myTerraformVM"
admin_username      = "azureuser"
admin_password      = "Password@1234"
🧾 4. outputs.tf (Output Variables)
output "resource_group_name" {
  value = azurerm_resource_group.rg.name
}

output "vm_name" {
  value = azurerm_linux_virtual_machine.vm.name
}

output "vm_public_ip" {
  value = azurerm_linux_virtual_machine.vm.public_ip_address
}
🚀 Execution Steps (IMPORTANT FOR LAB)

Run these in terminal:

1. Initialize Terraform
terraform init
2. Validate configuration
terraform validate
3. Apply infrastructure
terraform apply

Type:

yes
4. View outputs
terraform output
5. Destroy resources (optional)
terraform destroy
📌 Output
Resource Group created
Virtual Machine deployed
Outputs displayed (VM name, IP)
🧾 Result

Terraform successfully created and managed an Azure Virtual Machine using Infrastructure as Code.

📘 Conclusion

Terraform simplifies cloud infrastructure creation by using declarative configuration files and supports reproducibility and automation.