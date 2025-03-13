---
LinkTitle: Bring your own Cloud
Title: Redis Cloud Bring your own Cloud
alwaysopen: false
categories:
- docs
- operate
- rc
description: Describes how to provision your Redis Cloud subscription to use an existing
  cloud provider account.
bannerText: This article is for Redis Cloud Bring your Own Cloud (BYOC). If you're interested in Redis Cloud BYOC, [contact sales](https://redis.io/meeting/).
bannerChildren: true
hideListLinks: true
weight: 80
aliases:
  - /operate/rc/how-to/view-edit-cloud-account
  - /operate/rc/cloud-accounts
  - /operate/rc/cloud-integrations/aws-cloud-accounts
---

Redis Cloud Bring your own Cloud (BYOC) allows organizations to use their own cloud infrastructure to deploy Redis Cloud.

By default, Redis is responsible for the infrastructure that runs Redis Cloud. However, if your organization has specific requirements, you may want to have more control over your data residency or security options. Redis Cloud BYOC lets you fulfill these requirements while keeping the managed service experience of Redis Cloud. Like standard Redis Cloud, Redis handles deployment, scaling, monitoring, and support, so you can focus on building applications while Redis manages the backend.

If you're interested in Redis Cloud BYOC, [contact sales](https://redis.io/meeting/).

## Benefits of Redis Cloud BYOC

Redis Cloud BYOC has some benefits over standard Redis Cloud:

- **Full Data Control**: All data stays within your environment, giving you complete control over data security and reducing risks associated with data sovereignty.
- **Simplified Compliance**: BYOC simplifies adherence to regulatory standards like GDPR, HIPAA, and compliance frameworks like SOC 2 and PCI DSS since data remains within the your own cloud account.
- **Maximize Cloud Commitments**: Infrastructure costs are billed directly through your cloud provider account, enabling you to fully utilize existing commitments.
- **Separation of Costs**: Customers pay Redis only for licensing and management, while infrastructure costs go directly to the cloud provider, offering clear visibility into each cost stream.
- **Instant Access Control**: You can revoke Redis’ access to your environment at any time, offering complete control over data and infrastructure.

## Redis Cloud BYOC Use cases

Consider using Redis Cloud BYOC if you have specific organizational needs or requirements, such as:

- **Data Residency and Compliance**: Organizations operating in heavily regulated industries (such as finance, healthcare, and government) can use Redis Cloud BYOC to meet strict data residency and sovereignty requirements, ensuring sensitive data remains within their controlled environments.
- **Cloud spend optimization**: Companies with significant cloud provider commitments can use Redis Cloud BYOC to optimize their cloud spend. Since infrastructure costs are billed directly through the cloud provider, customers can fully utilize existing cloud provider discounts, improving cost efficiency.
- **Enhanced Security and Control**: Redis Cloud BYOC is ideal for organizations that require a higher degree of security and control over their data. By keeping data within your own cloud account and leveraging existing security policies, tools, and procedures on your cloud’s security infrastructure, you are able to minimize external access to your data, and adhere to more strict organizational security guidelines.

## Set up Redis Cloud BYOC

To set up Redis Cloud BYOC on Amazon Web Services (AWS):

1. [Create the Identity and Access Management (IAM) resources]({{< relref "/operate/rc/subscriptions/bring-your-own-cloud/iam-resources" >}}) needed to let Redis create, monitor, and maintain deployment infrastructure.

1. [Set your AWS Account as a BYOC Cloud account]({{< relref "/operate/rc/subscriptions/bring-your-own-cloud/cloud-account-settings" >}}) on Redis Cloud.


