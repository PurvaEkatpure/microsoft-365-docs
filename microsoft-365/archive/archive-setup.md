---
title: Set up Microsoft 365 Archive
ms.author: chucked
author: chuckedmonson
manager: jtremper
audience: admin
ms.reviewer: sreelakshmi
ms.date: 04/30/2024
ms.topic: conceptual
ms.service: microsoft-365-archive
ms.custom: archive
search.appverid:
ms.collection:
    - essentials-get-started
ms.localizationpriority:  medium
description: Learn how to set up and configure Microsoft 365 Archive.
---

# Set up Microsoft 365 Archive

Microsoft 365 Archive follows a pay-as-you-go model, and is configured through the Microsoft 365 admin center.

![Diagram showing four steps of the setup process for Microsoft 365 Archive.](../media/m365-archive/archive-setup-diagram.png)

To set up Microsoft 365 Archive, follow these steps:

1. Create an [Azure subscription](/azure/cloud-adoption-framework/ready/azure-best-practices/initial-subscriptions) and [resource group](/azure/azure-resource-manager/management/manage-resource-groups-portal).
2. [Set up pay-as-you-go billing](/microsoft-365/syntex/syntex-azure-billing) for Microsoft Syntex in the Microsoft 365 admin center.
3. [Turn on Microsoft 365 Archive](#set-up-microsoft-365-archive) in the Microsoft 365 admin center.
4. [Manage Microsoft 365 Archive](archive-manage.md) in the SharePoint admin center. 

## Prerequisites

### Licensing

Before you can use Microsoft 365 Archive, you must first link your Azure subscription in [Microsoft Syntex pay-as-you-go](/microsoft-365/syntex/syntex-azure-billing). Microsoft 365 Archive is billed based on the number of gigabytes (GB) archived and number of gigabytes (GB) reactivated. For more information about pricing, see [Pricing model](archive-pricing.md).

To set up pay-as-you-go billing, see [Configure Microsoft Syntex for pay-as-you-go billing at Microsoft Syntex billing](/microsoft-365/syntex/syntex-azure-billing).

> [!NOTE]
> Currently in Microsoft 365 Archive, you are not able to set up pay-as-you-go billing for two regions: US_West or Canada_East.  

### Permissions

You must have Global admin or SharePoint admin permissions to be able to access the Microsoft 365 admin center and set up Microsoft 365 Archive.

## Set up Microsoft 365 Archive

Once pay-as-you-go billing has been enabled for Microsoft Syntex on Microsoft 365 admin center, Microsoft 365 Archive can be enabled.

1. In the Microsoft 365 admin center, select <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Setup**</a>, and then select **Use content AI with Microsoft Syntex**.

2. On the **Use content AI with Microsoft Syntex** page, select **Manage Microsoft Syntex**.

3. On the **Manage Microsoft Syntex** page, select **Archive**.

4. On the **Archive** page, select **Turn on**, and on the confirmation pane, select **Confirm**.

    ![Screenshot of the Microsoft 365 Archive page in the admin center showing how to turn on Archive.](../media/m365-archive/turn-on-archive-admin-center.png)

Microsoft 365 Archive is now enabled for you, and you're able to archive content from the SharePoint admin center.

## Turn off Microsoft 365 Archive

To turn off Microsoft 365 Archive:

1. On the **Manage Microsoft Syntex** page, select **Archive**.

2. On the **Archive** page, select **Turn off**.

When you turn off Microsoft 365 Archive, any further archiving stops. The sites already archived will continue to be in an archive state, and will be billed. The sites can be reactivated with reactivation cost or deleted.
