# 钱包（Wallets）



## 钱包列表

获取所有钱包，包括空钱包。

### 请求接口

```text
GET /api/wallets
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets?page=5&limit=2
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 7717,
		"totalCount": 15433,
		"next": "/api/v2/wallets?page=6&limit=2",
		"previous": "/api/v2/wallets?page=4&limit=2",
		"self": "/api/v2/wallets?page=5&limit=2",
		"first": "/api/v2/wallets?page=1&limit=2",
		"last": "/api/v2/wallets?page=7717&limit=2"
	},
	"data": [{
		"address": "MFwkVTQon6G6xp4pnHAqmniqbagmxryAQf",
		"publicKey": "0204c7035db946028b0ab5f1e27dae50c8cf89f9ee55907bdf114bcc9f9147a89b",
		"username": null,
		"secondPublicKey": null,
		"balance": 265835500000000,
		"isDelegate": false,
		"vote": null
	}, {
		"address": "MUzMKJ6t4zs265My5yhy15EdG6cSQL8Cup",
		"publicKey": "02ac2e3c6e4da33542b2a62a0651db127109502ae90dceb6d1a37f9fcf9bdb5d1a",
		"username": null,
		"secondPublicKey": null,
		"balance": 264840000000000,
		"isDelegate": false,
		"vote": null
	}]
}
```



## 获取单个钱包

### 请求接口

```text
GET /api/v2/wallets/{id}
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 钱包ID（地址） | 是 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf
```

### 返回结果

```json
{
	"data": {
		"address": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"publicKey": "0326b38d0fc0fe8f6b9bdaba84ca765bf321ec601ab049285a0a363435bc1348de",
		"username": null,
		"secondPublicKey": null,
		"balance": 39000000,
		"isDelegate": false,
		"vote": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"
	}
}
```



## 获取钱包全部交易列表

获取钱包的所有交易（包含交易和发送）

### 请求接口

```text
GET /api/v2/wallets/{id}/transactions
```

### 路径参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 钱包ID（地址） | 是 |

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 请求示例

 ```shell
curl https://api.ark.io/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions
 ```

### 返回结果

```json
{
	"meta": {
		"count": 42,
		"pageCount": 1,
		"totalCount": 42,
		"next": null,
		"previous": null,
		"self": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions?page=1&limit=100",
		"first": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions?page=1&limit=100",
		"last": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions?page=1&limit=100"
	},
	"data": [{
		"id": "2cd81e2a8c88d1daf88ddb1ff0a32dc9f819a603a84bf9d74adf493db394a8c3",
		"blockId": "15171999033203642825",
		"version": 1,
		"type": 0,
		"amount": 10509000000000,
		"fee": 10000000,
		"sender": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"recipient": "MJPFqsVfCtWaNsMa8R3MUsxzCvfi7QwfDM",
		"signature": "304402202da1d303452a405e31fdb56a4cbad3ac4819a8e7fae95f543b706524540583ad0220566bcd8b0d65ce9fe9c9ba9e90e858771d78773ef4ad905d975d6ef1893c0714",
		"confirmations": 129538,
		"timestamp": {
			"epoch": 10074362,
			"unix": 1576148282,
			"human": "2019-12-12T10:58:02.000Z"
		}
	}
  ...
 ]
}
```



## 获取钱包已接收的交易列表

### 请求接口

```text
GET /api/v2/wallets/{id}/transactions/received
```

### 查询路径

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 钱包ID（地址） | 是 |

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/received
```

### 返回结果

```json
{
	"meta": {
		"count": 21,
		"pageCount": 1,
		"totalCount": 21,
		"next": null,
		"previous": null,
		"self": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/received?page=1&limit=100",
		"first": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/received?page=1&limit=100",
		"last": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/received?page=1&limit=100"
	},
	"data": [{
		"id": "5935cf9536f4fcedfc452db4d3e90c7557d09e57cf94df957b58d97e232119c1",
		"blockId": "10119752929100693652",
		"version": 1,
		"type": 0,
		"amount": 20600000000,
		"fee": 10000000,
		"sender": "MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv",
		"recipient": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"signature": "304402206a4e1f053f36f0c23687780625b0091de7495d7a0187fbb02d29c6cf3414690e02205913f8e93b21f5160c6a913e180ba588b3a8766da1e2ccf9dbb2b5d795b57ce9",
		"confirmations": 180566,
		"timestamp": {
			"epoch": 9631203,
			"unix": 1575705123,
			"human": "2019-12-07T07:52:03.000Z"
		}
	}
	...
	]
}
```



## 获取钱包已发送的交易列表

> 请注意，如果钱包地址是代表，那么钱包的余额不等于总输入-总输出。必须把交易费用和伪造块的总报酬加到他们的余额中。

### 接口

```text
GET /api/v2/wallets/{id}/transactions/sent
```

### 查询路径

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 要检索的钱包标识符 | 是 |

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/sent
```

### 返回结果

```json
{
	"meta": {
		"count": 24,
		"pageCount": 1,
		"totalCount": 24,
		"next": null,
		"previous": null,
		"self": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/sent?page=1&limit=100",
		"first": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/sent?page=1&limit=100",
		"last": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/transactions/sent?page=1&limit=100"
	},
	"data": [{
		"id": "2cd81e2a8c88d1daf88ddb1ff0a32dc9f819a603a84bf9d74adf493db394a8c3",
		"blockId": "15171999033203642825",
		"version": 1,
		"type": 0,
		"amount": 10509000000000,
		"fee": 10000000,
		"sender": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"recipient": "MJPFqsVfCtWaNsMa8R3MUsxzCvfi7QwfDM",
		"signature": "304402202da1d303452a405e31fdb56a4cbad3ac4819a8e7fae95f543b706524540583ad0220566bcd8b0d65ce9fe9c9ba9e90e858771d78773ef4ad905d975d6ef1893c0714",
		"confirmations": 129419,
		"timestamp": {
			"epoch": 10074362,
			"unix": 1576148282,
			"human": "2019-12-12T10:58:02.000Z"
		}
	}
   ...
  ]
}
```



## 获取钱包的投票列表

### 请求接口

```text
GET /api/v2/wallets/{id}/votes
```

### 查询路径

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 钱包ID（地址） | 是 |

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets/top?page=5&limit=2
```

###返回结果

```json
{
	"meta": {
		"count": 3,
		"pageCount": 1,
		"totalCount": 3,
		"next": null,
		"previous": null,
		"self": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/votes?page=1&limit=100",
		"first": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/votes?page=1&limit=100",
		"last": "/api/v2/wallets/MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf/votes?page=1&limit=100"
	},
	"data": [{
		"id": "b27834b2378baabab4296c6f7193d9f6c17fb0862ee18c1e100fcc1686e6cc2c",
		"blockId": "9236870716921448156",
		"version": 1,
		"type": 3,
		"amount": 0,
		"fee": 100000000,
		"sender": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"recipient": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"signature": "304402206507e0c3ccd56400efb1e81d2bf6264816924ed4aa4f872bc3d1b47189239d0b022031df374f3d2e9ea34f0ebe1f8ad96580ecfb316df1bbca65a96ccb177d1a226d",
		"asset": {
			"votes": ["+032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"]
		},
		"confirmations": 819267,
		"timestamp": {
			"epoch": 4273427,
			"unix": 1570347347,
			"human": "2019-10-06T07:35:47.000Z"
		}
	}
	...
	]
}
```



## 获取热门钱包

### 请求接口

```text
GET /api/v2/wallets/top
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/wallets/top?page=5&limit=2
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 7716,
		"totalCount": 15432,
		"next": "/api/v2/wallets/top?page=6&limit=2",
		"previous": "/api/v2/wallets/top?page=4&limit=2",
		"self": "/api/v2/wallets/top?page=5&limit=2",
		"first": "/api/v2/wallets/top?page=1&limit=2",
		"last": "/api/v2/wallets/top?page=7716&limit=2"
	},
	"data": [{
		"address": "MFwkVTQon6G6xp4pnHAqmniqbagmxryAQf",
		"publicKey": "0204c7035db946028b0ab5f1e27dae50c8cf89f9ee55907bdf114bcc9f9147a89b",
		"username": null,
		"secondPublicKey": null,
		"balance": 265835500000000,
		"isDelegate": false,
		"vote": null
	}, {
		"address": "MUzMKJ6t4zs265My5yhy15EdG6cSQL8Cup",
		"publicKey": "02ac2e3c6e4da33542b2a62a0651db127109502ae90dceb6d1a37f9fcf9bdb5d1a",
		"username": null,
		"secondPublicKey": null,
		"balance": 264840000000000,
		"isDelegate": false,
		"vote": null
	}]
}
```



## 搜索钱包

### 请求接口

```text
POST /api/v2/wallets/search
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 参数内容

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| address | string | 钱包地址 | 否 |
| publicKey | string | 钱包公钥 | 否 |
| secondPublicKey | string | 钱包二次公钥 | 否 |
| vote | string | 投票 | 否 |
| username | string | 用户名 | 否 |
| balance | object | 余额 | 否 |
| balance.from | int | 余额起始 | 否 |
| balance.to | int | 余额截止 | 否 |
| votebalance | object | 投票余额 | 否 |
| votebalance.from | int | 投票余额起始 | 否 |
| votebalance.to | int | 投票余额截止 | 否 |

### 请求示例

```shell
 curl --data 'balance={"from":100000000000,"to":100100000000}' https://api.ark.io/api/v2/wallets/search
```

### 返回结果

```json
{
	"meta": {
		"count": 24,
		"pageCount": 1,
		"totalCount": 24,
		"next": null,
		"previous": null,
		"self": "/api/v2/wallets/search?page=1&limit=100",
		"first": "/api/v2/wallets/search?page=1&limit=100",
		"last": "/api/v2/wallets/search?page=1&limit=100"
	},
	"data": [{
		"address": "MMbPAiZGA7dGWtduLbAJ9x1XDRYht1CfEz",
		"publicKey": null,
		"username": null,
		"secondPublicKey": null,
		"balance": 100100000000,
		"isDelegate": false,
		"vote": null
	 }
   ...
	]
}
```
