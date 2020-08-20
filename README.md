# Azure Network Connectivity and Name Resolution
This file contains commands from the demos in Cloud Academy's _Azure Network Connectivity and Name Resolution_ course.  

### Introduction
[Azure Free Trial](https://azure.microsoft.com/free)  

### Azure DNS
```
nslookup www.contoso.net <name_server>.azure-dns.com
```

### Private Domains
From https://docs.microsoft.com/en-us/azure/dns/private-dns-getstarted-cli  

Create a resource group:  
```
az group create --name MyAzureResourceGroup --location "East US"
```
Create a virtual network:  
```
az network vnet create \
  --name myAzureVNet \
  --resource-group MyAzureResourceGroup \
  --location eastus \
  --address-prefix 10.2.0.0/16 \
  --subnet-name backendSubnet \
  --subnet-prefix 10.2.0.0/24
```
Create a private DNS zone:  
```
az network private-dns zone create -g MyAzureResourceGroup \
   -n private.contoso.com

az network private-dns link vnet create -g MyAzureResourceGroup -n MyDNSLink \
   -z private.contoso.com -v myAzureVNet -e true
```
Create 2 VMs:  
```
az vm create \
 -n myvm1 \
 --admin-username test-user \
 -g MyAzureResourceGroup \
 -l eastus \
 --subnet backendSubnet \
 --vnet-name myAzureVnet \
 --generate-ssh-keys \
 --image UbuntuLTS

az vm create \
 -n myvm2 \
 --admin-username test-user \
 -g MyAzureResourceGroup \
 -l eastus \
 --subnet backendSubnet \
 --vnet-name myAzureVnet \
 --generate-ssh-keys \
 --image UbuntuLTS
```

### Conclusion
support@cloudacademy.com
