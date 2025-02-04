---
subcategory: "Global Accelerator (GA)"
layout: "alicloud"
page_title: "Alicloud: alicloud_ga_accelerators"
sidebar_current: "docs-alicloud-datasource-ga-accelerators"
description: |-
  Provides a list of Global Accelerator (GA) Accelerators to the user.
---

# alicloud_ga_accelerators

This data source provides the Global Accelerator (GA) Accelerators of the current Alibaba Cloud user.

-> **NOTE:** Available since v1.111.0.

## Example Usage

Basic Usage

```terraform
data "alicloud_ga_accelerators" "example" {
  name_regex = "tf"
}

output "first_ga_accelerator_id" {
  value = data.alicloud_ga_accelerators.example.accelerators.0.id
}
```

## Argument Reference

The following arguments are supported:

* `ids` - (Optional, ForceNew, List)  A list of Accelerator IDs.
* `name_regex` - (Optional, ForceNew) A regex string to filter results by Accelerator name.
* `status` - (Optional, ForceNew) The status of the GA instance. Valid values: `active`, `binding`, `configuring`, `deleting`, `finacialLocked`, `init`, `unbinding`.
* `bandwidth_billing_type` - (Optional, ForceNew, Available since v1.218.0) The bandwidth billing method. Default value: `BandwidthPackage`. Valid values:
  - `BandwidthPackage`: billed based on bandwidth plans.
  - `CDT`: billed based on data transfer.
* `output_file` - (Optional) File name where to save data source results (after running `terraform plan`).

## Attributes Reference

The following attributes are exported in addition to the arguments listed above:

* `names` - A list of Accelerator names.
* `accelerators` - A list of Ga Accelerators. Each element contains the following attributes:
  * `accelerator_id` - The ID of the GA instance to query.
  * `accelerator_name` - The Name of the GA instance.
  * `basic_bandwidth_package` - Details of the basic bandwidth package bound to the global acceleration instance.
  	* `bandwidth` - The bandwidth value of the basic bandwidth package.
    * `bandwidth_type` - The bandwidth type of the basic bandwidth package.
    * `instance_id` - Instance ID of the basic bandwidth package.
  * `cen_id` - The cloud enterprise network instance ID bound to the global acceleration instance.
  * `cross_domain_bandwidth_package` - Details of the cross-domain acceleration package bound to the global acceleration instance.
    * `instance_id` - Instance ID of the cross-domain acceleration package.
    * `bandwidth` - Bandwidth value of cross-domain acceleration package.
  * `ddos_id` - DDoS high-defense instance ID that is unbound from the global acceleration instance.
  * `description` - Descriptive information of the global acceleration instance.
  * `dns_name` - CNAME address assigned by Global Acceleration instance.
  * `expired_time` - Time when the global acceleration instance expires.
  * `id` - The ID of the Accelerator.
  * `payment_type` - The billing method of the GA instance. Valid values: `POSTPAY`, `PREPAY`.
  * `second_dns_name` - CNAME of the Global Acceleration Linkage DDoS High Defense Instance.
  * `spec` - The instance type of the GA instance.
  * `status` - The status of the GA instance.
