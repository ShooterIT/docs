---
acl_categories:
- '@write'
- '@stream'
- '@fast'
arguments:
- display_text: key
  key_spec_index: 0
  name: key
  type: key
- display_text: nomkstream
  name: nomkstream
  optional: true
  since: 6.2.0
  token: NOMKSTREAM
  type: pure-token
- arguments:
  - arguments:
    - display_text: maxlen
      name: maxlen
      token: MAXLEN
      type: pure-token
    - display_text: minid
      name: minid
      since: 6.2.0
      token: MINID
      type: pure-token
    name: strategy
    type: oneof
  - arguments:
    - display_text: equal
      name: equal
      token: '='
      type: pure-token
    - display_text: approximately
      name: approximately
      token: '~'
      type: pure-token
    name: operator
    optional: true
    type: oneof
  - display_text: threshold
    name: threshold
    type: string
  - display_text: count
    name: count
    optional: true
    since: 6.2.0
    token: LIMIT
    type: integer
  name: trim
  optional: true
  type: block
- arguments:
  - display_text: auto-id
    name: auto-id
    token: '*'
    type: pure-token
  - display_text: id
    name: id
    type: string
  name: id-selector
  type: oneof
- arguments:
  - display_text: field
    name: field
    type: string
  - display_text: value
    name: value
    type: string
  multiple: true
  name: data
  type: block
arity: -5
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
- write
- denyoom
- fast
complexity: O(1) when adding a new entry, O(N) when trimming where N being the number
  of entries evicted.
description: Appends a new message to a stream. Creates the key if it doesn't exist.
group: stream
hidden: false
hints:
- nondeterministic_output
history:
- - 6.2.0
  - Added the `NOMKSTREAM` option, `MINID` trimming strategy and the `LIMIT` option.
- - 7.0.0
  - Added support for the `<ms>-*` explicit ID form.
key_specs:
- RW: true
  begin_search:
    spec:
      index: 1
    type: index
  find_keys:
    spec:
      keystep: 1
      lastkey: 0
      limit: 0
    type: range
  notes: UPDATE instead of INSERT because of the optional trimming feature
  update: true
linkTitle: XADD
since: 5.0.0
summary: Appends a new message to a stream. Creates the key if it doesn't exist.
syntax_fmt: "XADD key [NOMKSTREAM] [<MAXLEN | MINID> [= | ~] threshold\n  [LIMIT\_\
  count]] <* | id> field value [field value ...]"
syntax_str: "[NOMKSTREAM] [<MAXLEN | MINID> [= | ~] threshold [LIMIT\_count]] <* |\
  \ id> field value [field value ...]"
title: XADD
---
Appends the specified stream entry to the stream at the specified key.
If the key does not exist, as a side effect of running this command the
key is created with a stream value. The creation of stream's key can be
disabled with the `NOMKSTREAM` option.

An entry is composed of a list of field-value pairs.
The field-value pairs are stored in the same order they are given by the user.
Commands that read the stream, such as [`XRANGE`]({{< relref "/commands/xrange" >}}) or [`XREAD`]({{< relref "/commands/xread" >}}), are guaranteed to return the fields and values exactly in the same order they were added by `XADD`.

`XADD` is the *only Redis command* that can add data to a stream, but 
there are other commands, such as [`XDEL`]({{< relref "/commands/xdel" >}}) and [`XTRIM`]({{< relref "/commands/xtrim" >}}), that are able to
remove data from a stream.

## Specifying a Stream ID as an argument

A stream entry ID identifies a given entry inside a stream.

The `XADD` command will auto-generate a unique ID for you if the ID argument
specified is the `*` character (asterisk ASCII character). However, while
useful only in very rare cases, it is possible to specify a well-formed ID, so
that the new entry will be added exactly with the specified ID.

IDs are specified by two numbers separated by a `-` character:

    1526919030474-55

Both quantities are 64-bit numbers. When an ID is auto-generated, the
first part is the Unix time in milliseconds of the Redis instance generating
the ID. The second part is just a sequence number and is used in order to
distinguish IDs generated in the same millisecond.

You can also specify an incomplete ID, that consists only of the milliseconds part, which is interpreted as a zero value for sequence part.
To have only the sequence part automatically generated, specify the milliseconds part followed by the `-` separator and the `*` character:

```
> XADD mystream 1526919030474-55 message "Hello,"
"1526919030474-55"
> XADD mystream 1526919030474-* message " World!"
"1526919030474-56"
```

IDs are guaranteed to be always incremental: If you compare the ID of the
entry just inserted it will be greater than any other past ID, so entries
are totally ordered inside a stream. In order to guarantee this property,
if the current top ID in the stream has a time greater than the current
local time of the instance, the top entry time will be used instead, and
the sequence part of the ID incremented. This may happen when, for instance,
the local clock jumps backward, or if after a failover the new master has
a different absolute time.

When a user specified an explicit ID to `XADD`, the minimum valid ID is
`0-1`, and the user *must* specify an ID which is greater than any other
ID currently inside the stream, otherwise the command will fail and return an error. Usually
resorting to specific IDs is useful only if you have another system generating
unique IDs (for instance an SQL table) and you really want the Redis stream
IDs to match the one of this other system.

## Capped streams

`XADD` incorporates the same semantics as the [`XTRIM`]({{< relref "/commands/xtrim" >}}) command - refer to its documentation page for more information.
This allows adding new entries and keeping the stream's size in check with a single call to `XADD`, effectively capping the stream with an arbitrary threshold.
Although exact trimming is possible and is the default, due to the internal representation of streams it is more efficient to add an entry and trim stream with `XADD` using **almost exact** trimming (the `~` argument).

For example, calling `XADD` in the following form:

    XADD mystream MAXLEN ~ 1000 * ... entry fields here ...
 
Will add a new entry but will also evict old entries so that the stream will contain only 1000 entries, or at most a few tens more.

## Additional information about streams

For further information about Redis streams please check our
[introduction to Redis Streams document]({{< relref "/develop/data-types/streams" >}}).

## Examples

{{% redis-cli %}}
XADD mystream * name Sara surname OConnor
XADD mystream * field1 value1 field2 value2 field3 value3
XLEN mystream
XRANGE mystream - +
{{% /redis-cli %}}

## Return information

{{< multitabs id="xadd-return-info" 
    tab1="RESP2" 
    tab2="RESP3" >}}

One of the following:
* [Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): The ID of the added entry. The ID is the one automatically generated if an asterisk (`*`) is passed as the _id_ argument, otherwise the command just returns the same ID specified by the user during insertion.
* [Nil reply](../../develop/reference/protocol-spec#bulk-strings): if the NOMKSTREAM option is given and the key doesn't exist.

-tab-sep-

One of the following:
* [Bulk string reply](../../develop/reference/protocol-spec#bulk-strings): The ID of the added entry. The ID is the one automatically generated if an asterisk (`*`) is passed as the _id_ argument, otherwise the command just returns the same ID specified by the user during insertion.
* [Null reply](../../develop/reference/protocol-spec#nulls): if the NOMKSTREAM option is given and the key doesn't exist.

{{< /multitabs >}}
