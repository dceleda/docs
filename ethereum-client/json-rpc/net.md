# Net module

## net\_listening

| Invocation |
| :--- |
| `{"method":"net_listening","params":[]}` |

| This method doesn't have parameters. |
| :--- |


| Returned type | Description |
| :--- | :--- |
| `Boolean` |  |

{% tabs %}
{% tab title="Example request of net\_listening" %}
```text
curl --data '{"method":"net_listening","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```
{% endtab %}

{% tab title="Example response of net\_listening" %}
```yaml
{
  "jsonrpc": "2.0",
  "result": true,
  "id": 1
}
```
{% endtab %}
{% endtabs %}

## net\_localAddress

| Invocation |
| :--- |
| `{"method":"net_localAddress","params":[]}` |

| This method doesn't have parameters. |
| :--- |


| Returned type | Description |
| :--- | :--- |
| `Address` |  |

{% tabs %}
{% tab title="Example request of net\_localAddress" %}
```text
curl --data '{"method":"net_localAddress","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```
{% endtab %}

{% tab title="Example response of net\_localAddress" %}
```yaml
{
  "jsonrpc": "2.0",
  "result": 0x247b5f5f007fb5d50de13cfcbd4460db21c12bcb,
  "id": 1
}
```
{% endtab %}
{% endtabs %}

## net\_localEnode

| Invocation |
| :--- |
| `{"method":"net_localEnode","params":[]}` |

| This method doesn't have parameters. |
| :--- |


| Returned type | Description |
| :--- | :--- |
| `String` |  |

{% tabs %}
{% tab title="Example request of net\_localEnode" %}
```text
curl --data '{"method":"net_localEnode","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```
{% endtab %}

{% tab title="Example response of net\_localEnode" %}
```yaml
{
  "jsonrpc": "2.0",
  "result": enode://a9cfa3cb16b537e131b0f141b5ef0c0ab9bf0dbec7799c3fc7bf8a974ff3e74e9b3258951b285dfed07ab395049bcd65fed96116bb92561612682551ec458497@18.193.43.58:30303,
  "id": 1
}
```
{% endtab %}
{% endtabs %}

[See also CLI net.localEnode](https://docs.nethermind.io/nethermind/nethermind-utilities/cli/net#net-localenode)

## net\_peerCount

| Invocation |
| :--- |
| `{"method":"net_peerCount","params":[]}` |

| This method doesn't have parameters. |
| :--- |


| Returned type | Description |
| :--- | :--- |
| `Quantity` |  |

{% tabs %}
{% tab title="Example request of net\_peerCount" %}
```text
curl --data '{"method":"net_peerCount","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```
{% endtab %}

{% tab title="Example response of net\_peerCount" %}
```yaml
{
  "jsonrpc": "2.0",
  "result": 0x11,
  "id": 1
}
```
{% endtab %}
{% endtabs %}

[See also CLI net.peerCount](https://docs.nethermind.io/nethermind/nethermind-utilities/cli/net#net-peercount)

## net\_version

| Invocation |
| :--- |
| `{"method":"net_version","params":[]}` |

| This method doesn't have parameters. |
| :--- |


| Returned type | Description |
| :--- | :--- |
| `String` |  |

{% tabs %}
{% tab title="Example request of net\_version" %}
```text
curl --data '{"method":"net_version","params":[],"id":1,"jsonrpc":"2.0"}' -H "Content-Type: application/json" -X POST localhost:8545
```
{% endtab %}

{% tab title="Example response of net\_version" %}
```yaml
{
  "jsonrpc": "2.0",
  "result": 4,
  "id": 1
}
```
{% endtab %}
{% endtabs %}

[See also CLI net.version](https://docs.nethermind.io/nethermind/nethermind-utilities/cli/net#net-version)

