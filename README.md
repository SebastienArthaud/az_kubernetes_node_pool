<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_azurerm"></a> [azurerm](#requirement\_azurerm) | >= 3.11, < 5.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | >= 3.11, < 5.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [azurerm_kubernetes_cluster_node_pool.my_aks_node_pool](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/kubernetes_cluster_node_pool) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_kubernetes_cluster_id"></a> [kubernetes\_cluster\_id](#input\_kubernetes\_cluster\_id) | ID du cluster AKS ou ce node pool sera attaché | `string` | n/a | yes |
| <a name="input_pool_pod_subnet_id"></a> [pool\_pod\_subnet\_id](#input\_pool\_pod\_subnet\_id) | ID du subnet ou les pods du default node pool sera déployé | `string` | n/a | yes |
| <a name="input_pool_subnet_id"></a> [pool\_subnet\_id](#input\_pool\_subnet\_id) | ID du subnet ou le default node pool sera déployé | `string` | n/a | yes |
| <a name="input_pool_auto_scaling_enabled"></a> [pool\_auto\_scaling\_enabled](#input\_pool\_auto\_scaling\_enabled) | la scalabilité du node pool système sera-t-elle automatique ? | `bool` | `false` | no |
| <a name="input_pool_capacity_reservation_group_id"></a> [pool\_capacity\_reservation\_group\_id](#input\_pool\_capacity\_reservation\_group\_id) | Specifies the ID of the Capacity Reservation Group where this Node Pool should exist. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_pool_eviction_policy"></a> [pool\_eviction\_policy](#input\_pool\_eviction\_policy) | The Eviction Policy which should be used for Virtual Machines within the Virtual Machine Scale Set powering this Node Pool. Possible values are Deallocate and Delete. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_pool_host_encryption_enabled"></a> [pool\_host\_encryption\_enabled](#input\_pool\_host\_encryption\_enabled) | Should the nodes in this Node Pool have host encryption enabled? Changing this property requires specifying temporary\_name\_for\_rotation. | `bool` | `false` | no |
| <a name="input_pool_host_group_id"></a> [pool\_host\_group\_id](#input\_pool\_host\_group\_id) | The fully qualified resource ID of the Dedicated Host Group to provision virtual machines from. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_pool_kubelet_disk_type"></a> [pool\_kubelet\_disk\_type](#input\_pool\_kubelet\_disk\_type) | The type of disk used by kubelet. Possible values are OS and Temporary. Changing this property requires specifying temporary\_name\_for\_rotation. | `string` | `null` | no |
| <a name="input_pool_labels"></a> [pool\_labels](#input\_pool\_labels) | labels à ajouter au niveau des nodes dans le cluster | `map(string)` | `null` | no |
| <a name="input_pool_max_count"></a> [pool\_max\_count](#input\_pool\_max\_count) | The maximum number of nodes which should exist in this Node Pool. If specified this must be between 1 and 1000. | `number` | `null` | no |
| <a name="input_pool_max_pods"></a> [pool\_max\_pods](#input\_pool\_max\_pods) | Nombre de pod qui peuvent tourner sur chaque node du node pool | `number` | `null` | no |
| <a name="input_pool_min_count"></a> [pool\_min\_count](#input\_pool\_min\_count) | The minimum number of nodes which should exist in this Node Pool. If specified this must be between 1 and 1000. | `number` | `null` | no |
| <a name="input_pool_mode"></a> [pool\_mode](#input\_pool\_mode) | Should this Node Pool be used for System or User resources? Possible values are System and User. Defaults to User. | `string` | `"User"` | no |
| <a name="input_pool_name"></a> [pool\_name](#input\_pool\_name) | Nom du node pool systèle créé | `string` | `"agentpool"` | no |
| <a name="input_pool_node_count"></a> [pool\_node\_count](#input\_pool\_node\_count) | The initial number of nodes which should exist in this Node Pool. If specified this must be between 1 and 1000. | `number` | `null` | no |
| <a name="input_pool_node_public_ip_enabled"></a> [pool\_node\_public\_ip\_enabled](#input\_pool\_node\_public\_ip\_enabled) | Should each node have a Public IP Address? Changing this property requires specifying temporary\_name\_for\_rotation. | `bool` | `false` | no |
| <a name="input_pool_node_public_ip_prefix_id"></a> [pool\_node\_public\_ip\_prefix\_id](#input\_pool\_node\_public\_ip\_prefix\_id) | Resource ID for the Public IP Addresses Prefix for the nodes in this Node Pool. node\_public\_ip\_enabled should be true. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_pool_node_taints"></a> [pool\_node\_taints](#input\_pool\_node\_taints) | A list of Kubernetes taints which should be applied to nodes in the agent pool (e.g key=value:NoSchedule). | `list(string)` | `null` | no |
| <a name="input_pool_orchestrator_version"></a> [pool\_orchestrator\_version](#input\_pool\_orchestrator\_version) | upgrade). AKS does not require an exact patch version to be specified, minor version aliases such as 1.22 are also supported. - The minor version's latest GA patch is automatically chosen in that case. More details can be found here : https://learn.microsoft.com/en-us/azure/aks/supported-kubernetes-versions?tabs=azure-cli#alias-minor-version | `string` | `null` | no |
| <a name="input_pool_os_disk_size_gb"></a> [pool\_os\_disk\_size\_gb](#input\_pool\_os\_disk\_size\_gb) | The Agent Operating System disk size in GB. Changing this property requires specifying temporary\_name\_for\_rotation. | `number` | `null` | no |
| <a name="input_pool_os_disk_type"></a> [pool\_os\_disk\_type](#input\_pool\_os\_disk\_type) | The type of disk which should be used for the Operating System. Possible values are Ephemeral and Managed. Defaults to Managed. Changing this property requires specifying temporary\_name\_for\_rotation. | `string` | `"Managed"` | no |
| <a name="input_pool_os_sku"></a> [pool\_os\_sku](#input\_pool\_os\_sku) | Specifies the OS SKU used by the agent pool. Possible values are AzureLinux, Ubuntu, Windows2019 and Windows2022. If not specified, the default is Ubuntu if OSType=Linux or Windows2019 if OSType=Windows. And the default Windows OSSKU will be changed to Windows2022 after Windows2019 is deprecated. Changing this from AzureLinux or Ubuntu to AzureLinux or Ubuntu will not replace the resource, otherwise temporary\_name\_for\_rotation must be specified when attempting a change. | `string` | `"ubuntu"` | no |
| <a name="input_pool_os_type"></a> [pool\_os\_type](#input\_pool\_os\_type) | The Operating System which should be used for this Node Pool. Changing this forces a new resource to be created. Possible values are Linux and Windows. Defaults to Linux. | `string` | `"Linux"` | no |
| <a name="input_pool_outbound_nat_enabled"></a> [pool\_outbound\_nat\_enabled](#input\_pool\_outbound\_nat\_enabled) | Should the Windows nodes in this Node Pool have outbound NAT enabled? Defaults to true. Changing this forces a new resource to be created. | `bool` | `true` | no |
| <a name="input_pool_priority"></a> [pool\_priority](#input\_pool\_priority) | The Priority for Virtual Machines within the Virtual Machine Scale Set that powers this Node Pool. Possible values are Regular and Spot. Defaults to Regular. Changing this forces a new resource to be created. | `string` | `"Regular"` | no |
| <a name="input_pool_proximity_placement_group_id"></a> [pool\_proximity\_placement\_group\_id](#input\_pool\_proximity\_placement\_group\_id) | The ID of the Proximity Placement Group. Changing this forces a new resource to be created. | `string` | `null` | no |
| <a name="input_pool_scale_down_mode"></a> [pool\_scale\_down\_mode](#input\_pool\_scale\_down\_mode) | Specifies the autoscaling behaviour of the Kubernetes Cluster. Allowed values are Delete and Deallocate. | `string` | `"Delete"` | no |
| <a name="input_pool_tags"></a> [pool\_tags](#input\_pool\_tags) | tags utilisés pour le node pool système | `map(string)` | `null` | no |
| <a name="input_pool_vm_size"></a> [pool\_vm\_size](#input\_pool\_vm\_size) | VM Size des VMs créées dans ce node pool système | `string` | `"Standard_DS2_v2"` | no |
| <a name="input_pool_zones"></a> [pool\_zones](#input\_pool\_zones) | Specifies a list of Availability Zones in which this Kubernetes Cluster should be located. temporary\_name\_for\_rotation must be specified when changing this property. | `list(string)` | `null` | no |

## Outputs

No outputs.
<!-- END_TF_DOCS -->