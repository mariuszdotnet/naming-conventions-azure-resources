# Naming Conventions for Azure Resources

TBD

## Naming Subscriptions

When naming Azure subscriptions, verbose names make understanding the context and purpose of each subscription clear. When working in an environment with many subscriptions, following a shared naming convention can improve clarity.

A recommended pattern for naming subscriptions:

`<service tier>-<product line>-<purpose>-<number>`

| Entity | Length | Casing | Valid Characters | Suggested Pattern | Example |
| --- | --- | --- | --- | --- | --- |
|Subscription |14 |Lower Case |Alphanumeric and hyphen. `<service tier>` - 1 character (p - production, n - non-production), `<product line>` - 3 character acronym (dce - data center extension) , `<purpose>` - 3 character acronym (hub), `<number>` - 4 digits (start with 0001 and increment by 1) |`<service tier>-<product line>-<purpose>-<number>` |`p-dce-hub-0001` |

## Naming Rules and Restrictions

Each resource or service type in Azure enforces a set of naming restrictions and scope; any naming convention or pattern must adhere to the requisite naming rules and scope. For example, while the name of a VM maps to a DNS name (and is thus required to be unique across all of Azure), the name of a VNET is scoped to the Resource Group that it is created within.

In general, avoid having any special characters (`-` or `_`) as the first or last character in any name. These characters will cause most validation rules to fail.

### General

| Entity | Scope | Length | Casing | Valid Characters | Suggested Pattern | Example |
| --- | --- | --- | --- | --- | --- | --- |
|Resource Group |Subscription |1-90 |Lower Case |Alphanumeric, underscore, parentheses, hyphen, period (except at end), and Unicode characters that match the regex documented [here](/rest/api/resources/resourcegroups/createorupdate). |`<service short name>-<environment>-rg` |`profx-prod-rg` |
|Availability Set |Resource Group |1-80 |Lower Case |Alphanumeric, underscore, and hyphen |`<service-short-name>-<context>-as` |`profx-sql-as` |
|Tag |Associated Entity |512 (name), 256 (value) |Case Insensitive |Alphanumeric, special characters except `<`, `>`, `%`, `&`, `\`, `?`, `/`. See limitations [here](/azure/azure-resource-manager/resource-group-using-tags). |`"key" : "value"` |`"department" : "Central IT"` |