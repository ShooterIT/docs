---
title: Redis products
description: Operate any Redis, from Redis Enterprise to Redis Cloud
linkTitle: Operate
hideListLinks: true
---

| <div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #80DBFF"></div> Redis Cloud | <div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #DCFF1E"></div> Redis Software |
|:-----------|:--------------|
| <ul><li> [Get started with Redis Cloud]({{< relref "/operate/rc/rc-quickstart" >}}) </li><li> [Create a database]({{< relref "/operate/rc/databases/create-database" >}}) </li><li> [Connect to your database]({{< relref "/operate/rc/databases/connect" >}}) </li><li>[REST API]({{< relref "/operate/rc/api/" >}})</li></ul> | <ul><li> [Install Redis Software]({{< relref "/operate/rs/installing-upgrading" >}}) </li><li> [Set up a new cluster]({{< relref "/operate/rs/clusters/new-cluster-setup" >}}) </li><li> [Create a database]({{< relref "/operate/rs/databases/create" >}}) </li><li> [Connect to your database]({{< relref "/operate/rs/databases/create" >}}) </li><li>[REST API]({{< relref "/operate/rs/references/rest-api/" >}})</li></ul> |
| <div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #C795E3"></div> **Redis Community Edition** | <div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #8A99A0"></div> **Redis for Kubernetes** |
| <ul><li> [Install Redis community edition]({{< relref "/operate/oss_and_stack/install/install-redis" >}}) </li><li> [Install Redis Stack]({{< relref "/operate/oss_and_stack/install/install-stack" >}}) </li><li> [Manage Redis]({{< relref "/operate/oss_and_stack/management" >}}) </li></ul> | <ul><li> [Deploy Redis for Kubernetes]({{< relref "/operate/kubernetes/deployment" >}}) </li><li> [Architecture]({{< relref "/operate/kubernetes/architecture" >}}) </li><li> [API Reference]({{< relref "/operate/kubernetes/reference" >}}) </li></ul> |
| <div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #FD4439"></div> **Redis Insight** | |
| <ul><li> [Install Redis Insight]({{< relref "/operate/redisinsight/install" >}}) </li><li> [Use Redis Insight]({{< relref "/develop/tools/insight" >}}) </li></ul> | |

## Product features

### High availability and durability

<!-- | Feature | RC        | RS         | CE       | K8s          | -->
| | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #80DBFF"></div> Redis</nobr> Cloud | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #DCFF1E"></div> Redis</nobr> Software | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #C795E3"></div> Redis</nobr> Community Edition | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #8A99A0"></div> Redis for</nobr> Kubernetes |
|:-----------|:--------------|:-----------|:--------------|:--------------|
| Clustering | [Clustering]({{< relref "/operate/rc/databases/configuration/clustering" >}}) | RS Link | [Scale with Redis Cluster]({{< relref "/operate/oss_and_stack/management/scaling" >}}) | K8s Link |
| Replication | [Replication]({{< relref "/operate/rc/databases/configuration/high-availability" >}}) | RS Link | [Replication]({{< relref "/operate/oss_and_stack/management/replication" >}}) | K8s Link |
| Active-Active geo-distribution | [Active-Active Redis]({{< relref "/operate/rc/databases/configuration/active-active-redis" >}}) | RS Link |  | K8s Link |
| Rolling upgrades | | RS Link |  | K8s Link |
| Redis Flex/Auto tiering | [Create a Redis Flex database]({{< relref "/operate/rc/databases/create-database/create-flex-database" >}}) | RS Link |  | K8s Link |
| Persistence | [Data persistence]({{< relref "/operate/rc/databases/configuration/data-persistence" >}}) | RS Link | [Persistence]({{< relref "/operate/oss_and_stack/management/replication" >}}) | K8s Link |
| Recovery | Automatic | RS Link | [Manual failover]({{< relref "/operate/oss_and_stack/management/scaling#manual-failover" >}}) | K8s Link |
| Backups | [Back up a database]({{< relref "/operate/rc/databases/back-up-data" >}}) | RS Link | [Persistence]({{< relref "/operate/oss_and_stack/management/replication" >}}) | K8s Link |


### Logging and Monitoring

<!-- | Feature | RC        | RS         | CE       | K8s          | -->
| | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #80DBFF"></div> Redis</nobr> Cloud | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #DCFF1E"></div> Redis</nobr> Software | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #C795E3"></div> Redis</nobr> Community Edition | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #8A99A0"></div> Redis for</nobr> Kubernetes |
|:-----------|:--------------|:-----------|:--------------|:--------------|
| Monitoring | [Monitor performance]({{< relref "/operate/rc/databases/monitor-performance" >}}) | RS Link | [INFO]({{< relref "/commands/info" >}}), [MONITOR]({{< relref "/commands/monitor" >}}), and [LATENCY DOCTOR]({{< relref "/commands/latency-doctor" >}})<br/>[Analysis with Redis Insight]({{< relref "/develop/tools/insight#database-analysis" >}}) | K8s Link |
| Logging | [System logs]({{< relref "/operate/rc/logs-reports/system-logs" >}}) | RS Link | `/var/log/redis/redis.log`<br/>[SLOWLOG]({{< relref "/commands/slowlog" >}})<br/>[Keyspace notifications]({{< relref "/develop/use/keyspace-notifications" >}}) | K8s Link |
| Alerts | [Alerts]({{< relref "/operate/rc/databases/view-edit-database#alerts-section" >}}) | RS Link | [Pub/sub with Redis Sentinel]({{< relref "/operate/oss_and_stack/management/sentinel#pubsub-messages" >}}) | K8s Link |
| Support | [Contact support](https://redis.io/support/) | RS Link |  | K8s Link |

### Security

<!-- | Feature | RC        | RS         | CE       | K8s          | -->
| | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #80DBFF"></div> Redis</nobr> Cloud | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #DCFF1E"></div> Redis</nobr> Software | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #C795E3"></div> Redis</nobr> Community Edition | <nobr><div class="h-3 w-3 rounded-md border border-redis-pen-600 inline-block mr-1" style="background-color: #8A99A0"></div> Redis for</nobr> Kubernetes |
|:-----------|:--------------|:-----------|:--------------|:--------------|
| Transport Layer Security (TLS) | [TLS]({{<relref "/operate/rc/security/database-security/tls-ssl">}}) | RS Link | [TLS]({{< relref "/operate/oss_and_stack/management/security/encryption" >}}) | K8s Link |
| Role-based access control (RBAC) | [Role-based access control]({{<relref "/operate/rc/security/access-control/data-access-control/role-based-access-control">}}) | RS Link | [Access control list]({{< relref "/operate/oss_and_stack/management/security/acl" >}}) | K8s Link |
| Lightweight Directory Access Protocol (LDAP) |  | RS Link |  | K8s Link |
| Single sign-on (SSO) | [SAML SSO]({{< relref "/operate/rc/security/access-control/saml-sso" >}}) |  |  |  |
| Self-signed certificates |  | RS Link | [Certificate configuration]({{< relref "/operate/oss_and_stack/management/security/encryption" >}}) | K8s Link |
| Internode encryption | [Encryption at rest]({{< relref "/operate/rc/security/encryption-at-rest" >}}) | RS Link |  | K8s Link |
| Auditing |  | RS Link | [Keyspace notifications]({{< relref "/develop/use/keyspace-notifications" >}}) | K8s Link |

