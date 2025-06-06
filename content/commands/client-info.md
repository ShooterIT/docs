---
acl_categories:
- '@slow'
- '@connection'
arity: 2
categories:
- docs
- develop
- stack
- oss
- rs
- rc
- oss
- kubernetes
- clients
command_flags:
- noscript
- loading
- stale
complexity: O(1)
description: Returns information about the connection.
group: connection
hidden: false
hints:
- nondeterministic_output
linkTitle: CLIENT INFO
since: 6.2.0
summary: Returns information about the connection.
syntax_fmt: CLIENT INFO
syntax_str: ''
title: CLIENT INFO
---
The command returns information and statistics about the current client connection in a mostly human readable format.

The reply format is identical to that of [`CLIENT LIST`]({{< relref "/commands/client-list" >}}), and the content consists only of information about the current client.

## Examples

{{% redis-cli %}}
CLIENT INFO
{{% /redis-cli %}}

## Return information

{{< multitabs id="client-info-return-info" 
    tab1="RESP2" 
    tab2="RESP3" >}}

[Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): a unique string for the current client, as described at the `CLIENT LIST` page.

-tab-sep-

[Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): a unique string for the current client, as described at the `CLIENT LIST` page.

{{< /multitabs >}}
