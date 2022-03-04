# oci-terraform-osok


[![License: UPL](https://img.shields.io/badge/license-UPL-green)](https://img.shields.io/badge/license-UPL-green) [![Quality gate](https://sonarcloud.io/api/project_badges/quality_gate?project=oracle-devrel_terraform-oci-arch-ci-cd)](https://sonarcloud.io/dashboard?id=oracle-devrel_terraform-oci-arch-ci-cd)


## Introduction

This Terraform playbook will automate the installation of the OCI Service Operator for Kubernetes (OSOK) in a Kubernetes cluster deployed on Oracle Cloud Infrastructure (OCI). The Kubernetes cluster can be a customer-managed cluster deployed on virtual machines (VM) or a cluster managed with the Oracle Container Engine for Kubernetes (OKE) service.

### OSOK Supported Services

As part of the installation, this Terraform playbook will install the pre-requisites and the requirements for OSOK to manage the following OCI services.

- MySQL Databse System (MDS)
- Autonomous Database (ATP)
- Oracle Streaming Service
- Oracle Service Mesh

### Installed Components

- [OSOK](https://github.com/oracle/oci-service-operator) in the Kuberntes cluster
- Operator Lifecycle Manager [OLM](https://olm.operatorframework.io/docs/getting-started/) in the Kubernetes Cluster  
- OCI Dynamic Group to contain all Kubernetes worker nodes in the compartment
- OCI Policy to grant the Kuberntes worker nodes permission to manage OSOK supported services
- Kubernetes namespaces for OSOK and OLM
- Kubernetes secret with credentials required by OSOK





## Pre-requisites

- A Kuberntes cluster deployed in OCI 
- [kubectl](https://kubernetes.io/docs/tasks/tools/) installed and using the context for the Kubernetes cluster where OSOK will be deployed]
- [Docker](https://docs.docker.com/engine/install/) installed
- OCI credentials with the required permissions to create Dynamic groups and policies on OCI


##  Getting Started

**1. Clone or download the contents of this repo** 
     
     git clone https://github.com/chiphwang1/oci-terraform-osok.git

**2. Change to the directory that holds the Terraform code** 

      cd ./oci-terraform-osok

**3. Populate the variables.tf file with the required information to deploy OSOK**


**4. To Initialize, plan, and apply the Terraform playbook, run the following commands**

``` 
# terraform initialize
# terraform plan
# terraform apply
    
```   

**5. To uninstall OSOK and associated components.**

```
# terraform destroy
```


     
  **Notes/Issues:**
 


 ## Variables Definitions


| Parameter                          | Description                                                         | Type   | Mandatory |
| ---------------------------------- | ------------------------------------------------------------------- | ------ | --------- |
| `tenancy_ocid` | ocid of your tenenacy | string | yes  |
| `user_ocid` | ocid of your user | string | yes       |
| `private_key_path` | path to the private key file on your system | string | yes       |
| `region` | region where your Kubernetes cluster reside | string | yes       |
| `fingerprint` | finger print of your ocid user credentials | string    | yes       |
| `passphrase`| passphrase for user credentials | string   | yes       |
| `node_compartment_ocid` | ocid of the compartment where the Kubernetes cluster reside | string | yes        |
| `dynamic_group_name` | Name to assign to the dynamic group  | string | yes       |
| `dynamic_group_description`  | description for the dynamic group | string | yes       |
| `policy_description`| Description for the policy | string | yes        |
| `policy_name` | name that will be assigned to the policy | string | yes |
| `kube_config_path` | path to config file to access your Kubernetes cluster| string | yes       |
| `config_context` | context within the kube_config file to use | string | yes |




## Additional Resources

- [OCI Service Operator for Kuberntes (OSOK) deployed in the cluster](https://github.com/oracle/oci-service-operator)
- [OCI Autonomous Database Serice OSOK](https://github.com/oracle/oci-service-operator/blob/main/docs/adb.md)
- [Oracle Autonomous Database](https://www.oracle.com/database/what-is-autonomous-database/)
- [Developing Python Applications for Oracle ATP](https://www.oracle.com/database/technologies/appdev/python/quickstartpython.html)


## License
Copyright (c) 2022 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](LICENSE) for more details.
