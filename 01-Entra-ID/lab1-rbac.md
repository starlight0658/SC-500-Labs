# Lab 1  Azure RBAC

## Objective

Create a Microsoft Entra user and assign Azure RBAC permissions using the principle of least privilege.

## What is a Resource Group?

A Resource Group is a logical container that holds related Azure resources such as virtual machines, storage accounts, Key Vaults, and virtual networks.

## What is RBAC?

Role-Based Access Control (RBAC) is Azure's authorization system. It determines what actions users can perform on Azure resources.

## Azure RBAC Roles

### Reader
- View resources only.
- Cannot make changes.

### Contributor
- Create, modify, and delete resources.
- Cannot assign permissions.

### Owner
- Full control.
- Can assign Azure RBAC roles.

## Why I Assigned Reader

The test user only needed to view resources in the Resource Group. Following the principle of least privilege, Reader was the appropriate role instead of Owner.

## Lab Summary

- Created a Microsoft Entra user.
- Created the Resource Group `rg-sc500-lab`.
- Assigned the Reader role.
- Verified the assignment with Azure PowerShell.