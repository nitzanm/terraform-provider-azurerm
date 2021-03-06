---
layout: "azurerm"
page_title: "Azure Resource Manager: azurerm_private_dns_cname_record"
sidebar_current: "docs-azurerm-resource-private-dns-cname-record"
description: |-
  Manages a Private DNS CNAME Record.
---

# azurerm_private_dns_cname_record

Enables you to manage DNS CNAME Records within Azure Private DNS.

## Example Usage

```hcl
resource "azurerm_resource_group" "test" {
  name     = "acceptanceTestResourceGroup1"
  location = "West US"
}

resource "azurerm_private_dns_zone" "test" {
  name                = "mydomain.com"
  resource_group_name = "${azurerm_resource_group.test.name}"
}

resource "azurerm_private_dns_cname_record" "test" {
  name                = "test"
  zone_name           = "${azurerm_private_dns_zone.test.name}"
  resource_group_name = "${azurerm_resource_group.test.name}"
  ttl                 = 300
  record              = "contoso.com"
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the DNS CNAME Record.

* `resource_group_name` - (Required) Specifies the resource group where the resource exists. Changing this forces a new resource to be created.

* `zone_name` - (Required) Specifies the Private DNS Zone where the resource exists. Changing this forces a new resource to be created.

* `TTL` - (Required) The Time To Live (TTL) of the DNS record in seconds.

* `record` - (Required) The target of the CNAME.

* `tags` - (Optional) A mapping of tags to assign to the resource.

## Attributes Reference

The following attributes are exported:

* `id` - The Private DNS CNAME Record ID.

## Import

Private DNS CName Records can be imported using the `resource id`, e.g.

```shell
terraform import azurerm_private_dns_cname_record.test /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.Network/privateDnsZones/zone1/CName/myrecord1
```
