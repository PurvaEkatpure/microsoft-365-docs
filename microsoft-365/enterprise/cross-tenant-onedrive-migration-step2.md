---
title: OneDrive Cross-tenant OneDrive migration Step 2
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
ms.date: 10/13/2023
recommendations: true
audience: ITPro
ms.topic: article
ms.service: microsoft-365-migration
ms.localizationpriority: high
ms.collection:
- SPMigration
- M365-collaboration
- m365initiative-migratetom365
search.appverid: MET150
description: "Step 2 of the OneDrive Cross-tenant migration feature"
---
# Step 2: Establishing trust between the source and target tenants

This is Step 2 in a solution designed to complete a Cross-tenant OneDrive migration. To learn more, see [Cross-tenant OneDrive migration overview](cross-tenant-onedrive-migration.md).

- Step 1: [Connect to the source and the target tenants](cross-tenant-onedrive-migration-step1.md)
- **Step 2: [Establish trust between the source and the target tenant](cross-tenant-onedrive-migration-step2.md)**
- Step 3: [Verify trust has been established](cross-tenant-onedrive-migration-step3.md)
- Step 4: [Precreate users and groups](cross-tenant-onedrive-migration-step4.md)
- Step 5: [Prepare identity mapping](cross-tenant-onedrive-migration-step5.md)
- Step 6: [Start a Cross-tenant OneDrive migration](cross-tenant-onedrive-migration-step6.md)
- Step 7: [Post migration steps](cross-tenant-onedrive-migration-step7.md)

After connecting to the source and target tenant, the next step in performing a cross-tenant OneDrive migration is establishing trust between the tenants.

To establish trust, each SharePoint tenant administrator must run specific commands on both source and target tenants. Once the trust has been requested, the administrator of the target tenant will receive an email informing them that another tenant is trying to establish a trust relationship.

> [!NOTE]
> The "trust" command is specific to SharePoint. It only grants permission for the SharePoint administrator on the source tenant to execute OneDrive Migration operations to the identified target tenant.
>
> Granting trust *doesn't* give the administrator any visibility, permission, or ability to collaborate between the source tenant and the target tenant.

> [!IMPORTANT]
> If you are Microsoft 365 Multi-Geo customer, you must establish trust between each geography involved in your migration project.

## Before you begin

Before running the trust commands, obtain the cross-tenant host URLs for both the source and target tenants. You'll need these URLs when establishing the trust relationship between source-to-target and target-to-source.

**To obtain the cross-tenant host URLs:**

On both the source and target tenants, run:

```powershell
Get-SPOCrossTenantHostURL
```

*Example:* Run command on Source tenant:

 :::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-hosturl-source.png" alt-text="example of how to obtain host url for source":::

*Example:* Run command on target tenant:

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-hosturl-target.png" alt-text="example of how to obtain host url for target":::

## Run the trust commands

These commands send a request to the tenant with whom you want to establish trust.

1. On the source tenant, run this command to send a trust request to the target tenant:

   ```powershell
   Set-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>
   ```

2. On the target tenant, run this command to send a trust request to the source tenant:

   ```powershell
   Set-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Source -PartnerCrossTenantHostUrl <SOURCECrossTenantHostUrl>
   ```

### Parameter definitions

|Parameter|Definition|
|---|---|
|PartnerRole|Roles of the partner tenant you're establishing trust with.  Use *source* if partner tenant is the source of the OneDrive migrations, and *target* if the partner tenant is the Destination.
|PartnerCrossTenantHostURL|The cross-tenant host URL of the partner tenant. The partner tenant can determine this for you by running: *Get-SPOCrossTenantHostURL* on each of the tenants.|

## Sample trust email

The following in an example of the email that is sent to global admins:

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-trust-email.png" alt-text="example of trust email":::

**Subject:**  SPO Tenant [https://a830edad9050849mnaus093022-my.sharepoint.com/] [setuporupdate] Organization Relation [Scenario=MnA, Role=Source] with us

**Message:**  SPO Tenant [https://a830edad9050849mnaus093022-my.sharepoint.com/] [setuporupdate] Organization Relation [Scenario=MnA, Role=Source] with us

## Step 3: [Verify that trust has been established](cross-tenant-onedrive-migration-step3.md)
