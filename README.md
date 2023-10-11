# Harvester: Virtual Machine Terraform Module

![Alt text](assets/harvester_logo.png)

Terraform modules which creates Virtual Machines on Harvester HCI

## Requirements

- Harvester HCI Cluster
- kubeconfig file for the cluster

<!-- BEGIN_TF_DOCS -->


## Modules

| Name | Source | Version |
|------|--------|---------|
| harvester_vm | ./modules/harvester-vm | n/a |
| harvester_vm_image | ./modules/harvester-vm-image | n/a |
| harvester_vm_network | ./modules/harvester-vm-network | n/a |



## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| cluster_network_name | Cluster network name | `string` | n/a | yes |
| harvester_kubeconfig_path | Path to the kubeconfig file | `string` | n/a | yes |
| image_display_name | The display name for the OS image | `string` | n/a | yes |
| image_name | The name of the OS image | `string` | n/a | yes |
| image_namespace | The namespace where the image will reside | `string` | n/a | yes |
| image_source_type | Source type for the image (e.g., download, upload) | `string` | n/a | yes |
| image_url | URL from where the image will be downloaded | `string` | n/a | yes |
| network_name | Name of the network | `string` | n/a | yes |
| network_namespace | Namespace of the network | `string` | n/a | yes |
| network_vlan_id | VLAN ID for the network | `string` | n/a | yes |
| user_data | User data for cloud-init configuration | `string` | n/a | yes |
| vm_data | Configuration data for the virtual machine | ```object({ name = string      # Name of the virtual machine hostname = string      # Hostname for the virtual machine namespace = string      # Namespace where the VM will reside description = string      # Description for the VM tags = map(string) # Tags associated with the VM cpus = number      # Number of CPUs for the VM memory = string      # Memory allocation for the VM disks = list(object({     # List of disks for the VM name = string     # Name of the disk size = string     # Size of the disk boot_order = number     # Boot order for the disk })) })``` | n/a | yes |
| image_tags | Tags associated with the image | `map(string)` | `{}` | no |
| network_data | Network data for cloud-init configuration | `string` | `""` | no |

## Outputs

| Name | Description |
|------|-------------|
| image_id | The ID of the VM image |
| network_id | The name of the network |
| vm_id | The ID of the created virtual machine |
<!-- END_TF_DOCS -->

## References

- [Harvester](https://harvesterhci.io/)
- [Terraform](https://www.terraform.io/)
- [Terragrunt](https://terragrunt.gruntwork.io/)
- [Harvester Terraform Module](https://registry.terraform.io/providers/harvester/harvester/latest)
