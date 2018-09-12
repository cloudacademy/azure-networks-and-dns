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
az network dns zone create -g MyAzureResourceGroup \
   -n contoso.local \
  --zone-type Private \
  --registration-vnets myAzureVNet
```

### Conclusion
support@cloudacademy.com
