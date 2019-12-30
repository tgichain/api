# 交易(Transactions)



## 创建交易

### 请求接口

```text
POST /api/v2/transactions
```

### 参数内容

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| transactions | array | 要创建的交易列表 | 是 |

### 请求示例

```shell
curl -d "" http://openapi.tgichain.com/api/v2/transactions
```

### 返回结果

```json
{
  "data": {
    "accept": [
      "15d4b3e933b79e5172bbf14c2bd3f92d927394cd8ebd102f18dcc2203af363ca",
      "c48862c4df75a8b0859b559658c757c1c289088488630494fe51613db0747e57",
      "bd10b25444363252e0787e46f5cac90797d08a0c34d507a10d064c94cccf6226"
    ],
    "broadcast": [
      "15d4b3e933b79e5172bbf14c2bd3f92d927394cd8ebd102f18dcc2203af363ca",
      "c48862c4df75a8b0859b559658c757c1c289088488630494fe51613db0747e57",
      "bd10b25444363252e0787e46f5cac90797d08a0c34d507a10d064c94cccf6226"
    ],
    "excess": [],
    "invalid": []
  },
  "errors": null
}
```



## 获取单个交易

### 请求接口

```text
GET /api/v2/transactions/{id}
```

### 路径参数


| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 交易ID | 是 |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions/5a8fbca13bd6cbdd1dc5508598a4c33eeb3c8260a1fe2240887fc1752b47bb51
```

### 返回结果

```json
{
	"data": {
		"id": "5a8fbca13bd6cbdd1dc5508598a4c33eeb3c8260a1fe2240887fc1752b47bb51",
		"blockId": "16723676184022346306",
		"version": 1,
		"type": 0,
		"amount": 20000000000,
		"fee": 10000000,
		"sender": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
		"recipient": "MWcVtmEZpFdPYM7SxdBHhbG4diuJdAN6M6",
		"signature": "304402207dee40f2b093adb1cbd0f1b667c7207a377a70913a0eccdd1427fe3035abeabf02205ed356767b330a4f61ce7d4b23ca7030f71c5ae94c98d2ec744097d05a0f1b7a",
		"confirmations": 141,
		"timestamp": {
			"epoch": 11102694,
			"unix": 1577176614,
			"human": "2019-12-24T08:36:54.000Z"
		}
	}
}
```



## 获取交易列表

### 请求接口

```text
GET /api/v2/transactions
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页数量 | 否 |
| type | int | 交易类型 | 否 |
| blockld | int | 区块ID | 否 |
| id | int | 交易ID | 否 |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions?limit=2
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 13560,
		"totalCount": 27119,
		"next": "/api/v2/transactions?limit=2&page=2",
		"previous": null,
		"self": "/api/v2/transactions?limit=2&page=1",
		"first": "/api/v2/transactions?limit=2&page=1",
		"last": "/api/v2/transactions?limit=2&page=13560"
	},
	"data": [{
		"id": "5a8fbca13bd6cbdd1dc5508598a4c33eeb3c8260a1fe2240887fc1752b47bb51",
		"blockId": "16723676184022346306",
		"version": 1,
		"type": 0,
		"amount": 20000000000,
		"fee": 10000000,
		"sender": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
		"recipient": "MWcVtmEZpFdPYM7SxdBHhbG4diuJdAN6M6",
		"signature": "304402207dee40f2b093adb1cbd0f1b667c7207a377a70913a0eccdd1427fe3035abeabf02205ed356767b330a4f61ce7d4b23ca7030f71c5ae94c98d2ec744097d05a0f1b7a",
		"confirmations": 175,
		"timestamp": {
			"epoch": 11102694,
			"unix": 1577176614,
			"human": "2019-12-24T08:36:54.000Z"
		}
	}, {
		"id": "10c32159034b7f4c2af636e98df6c56833e7bfa2cd16f530ef147710d73cfe39",
		"blockId": "13443407091764644740",
		"version": 1,
		"type": 0,
		"amount": 20000000000,
		"fee": 10000000,
		"sender": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
		"recipient": "MBjF16Eg1HAyEndT1HFSVdQeKaTNBs2HZA",
		"signature": "304402203cc015a575d9cee1813af84f0116814770855b1266a37862bb2b83574c042c59022077f499afd99fe83e510140e624dd1b8c60753acf291b0e1348d9fb30855bcf63",
		"confirmations": 247,
		"timestamp": {
			"epoch": 11102117,
			"unix": 1577176037,
			"human": "2019-12-24T08:27:17.000Z"
		}
	}]
}
```



## 列出所有未确认的交易

未经确认的交易在尚未纳入区块链之前会驻留在内存池中。 通常情况下，会在数分钟内清除内存池，但是在网络负载较高的情况下，低费用的交易将在此处停留相当长的时间。 如果您将交易费用设置为接近零，则代表可能不会接收该交易，并且超时。

### 接口

```text
GET /api/transactions/unconfirmed/
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions/unconfirmed?limit=5&page=1
```

### 返回结果

```json
{
  "meta": {
    "count": 5,
    "pageCount": 8,
    "totalCount": 40,
    "next": "/api/v2/transactions/unconfirmed?limit=5&page=2",
    "previous": null,
    "self": "/api/v2/transactions/unconfirmed?limit=5&page=1",
    "first": "/api/v2/transactions/unconfirmed?limit=5&page=1",
    "last": "/api/v2/transactions/unconfirmed?limit=5&page=8"
  },
  "data": [
    {
      "id": "c94504293d23e3be535a049fdfacba95147f2a87a4ef6682c56801da96befce0",
      "version": 1,
      "type": 0,
      "amount": 70866123,
      "fee": 344000,
      "sender": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
      "recipient": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
      "signature": "30450221008adeff8eb2a780168704d9e210368d81edff79b81aa7b995e43486f3b1e0096502205caef345584319a6294b1f5283c0d17b478b8a9bcdc10570e5a58681b0eae332",
      "vendorField": "Yooooooloooooo",
      "confirmations": 0,
      "timestamp": {
        "epoch": 56388424,
        "unix": 1546489624,
        "human": "2019-01-03T04:27:04.000Z"
      }
    }
    ...
  ]
}
```



## 获取未确认的交易详情

与查询确认交易一样，您可以直接查询未确认交易。

### 请求接口

```text
GET /api/v2/transactions/unconfirmed/{id}
```

### 路径参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 要检索的交易的标识符 | 是 |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions/unconfirmed/5a8fbca13bd6cbdd1dc5508598a4c33eeb3c8260a1fe2240887fc1752b47bb51
```

### 返回结果

```json
{
	"data": {
		"id": "5a8fbca13bd6cbdd1dc5508598a4c33eeb3c8260a1fe2240887fc1752b47bb51",
		"blockId": "16723676184022346306",
		"version": 1,
		"type": 0,
		"amount": 20000000000,
		"fee": 10000000,
		"sender": "MGQS8VpKBwvS5ML4kahMJd7GGHq3xcwnB6",
		"recipient": "MWcVtmEZpFdPYM7SxdBHhbG4diuJdAN6M6",
		"signature": "304402207dee40f2b093adb1cbd0f1b667c7207a377a70913a0eccdd1427fe3035abeabf02205ed356767b330a4f61ce7d4b23ca7030f71c5ae94c98d2ec744097d05a0f1b7a",
		"confirmations": 0,
		"timestamp": {
			"epoch": 11102694,
			"unix": 1577176614,
			"human": "2019-12-24T08:36:54.000Z"
		}
	}
}
```



## 搜索交易

### 请求接口

```text
POST /api/v2/transactions/search
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 参数内容

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| orderBy | string | 排序 | 否 |
| id | string | 交易ID | 否 |
| blockId | string | 区块ID | 否 |
| type | int | 交易类型 | 否 |
| version | int | 版本 | 否 |
| senderPublicKey | string | 发送人公钥 | 否 |
| senderId | string | 发送人ID | 否 |
| recipientId | string | 接收者ID | 否 |
| ownerId | string | 拥有者ID | 否 |
| vendorFieldHex | string | 备注字段HEX | 否 |
| timestamp | object | 时间戳 | 否 |
| timestamp.from | int | 时间戳起始 | 否 |
| timestamp.to | int | 时间戳截止 | 否 |
| amount | object | 数量 | 否 |
| amount.from | int | 数量起始 | 否 |
| amount.to | int | 数量截止 | 否 |
| fee | object | 费用 | 否 |
| fee.from | int | 费用起始 | 否 |
| fee.to | int | 费用截止 | 否 |

### 请求示例

```shell
curl --data 'amount={ "from": 100000000000000,"to":100000100000000 }' http://openapi.tgichain.com/api/v2/transactions/search
```

### 返回结果

```json
{
	"meta": {
		"count": 4,
		"pageCount": 2,
		"totalCount": 104,
		"next": "/api/v2/transactions/search?page=2&limit=100",
		"previous": null,
		"self": "/api/v2/transactions/search?page=1&limit=100",
		"first": "/api/v2/transactions/search?page=1&limit=100",
		"last": "/api/v2/transactions/search?page=2&limit=100"
	},
	"data": [{
		"id": "3bbf6d58fb8469feaa85c5334ac0e7b6a4555e511c33926aad2501ce71caa41a",
		"blockId": "3005435412133744444",
		"version": 1,
		"type": 0,
		"amount": 100000000000000,
		"fee": 10000000,
		"sender": "MA2wSg7gnx2yusWFYkmkZvBYoJKBWymejb",
		"recipient": "MKMAaFjCNhUiD51ZZQ7AovLLzHAXTbwbqH",
		"signature": "3045022100c1e0a25ee879e31a6e788323a786565de179316ce618e8f3c2cb8e775c8efe100220083dcd35059729d5742ab4c874b25d3bc959cdf3b31121129a226fecfec82d6c",
		"confirmations": 110997,
		"timestamp": {
			"epoch": 10226809,
			"unix": 1576300729,
			"human": "2019-12-14T05:18:49.000Z"
		}
	}
  ...
  ]
}
```



## 获取交易类型

交易类型是特定于网络的。ARK目前支持八种不同的类型，但如果出于业务目的需要，BridgeChains可以定义更多或更少的内容。

### 请求接口

```text
GET /api/v2/transactions/types
```

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions/types
```

### 返回结果

```json
{
  "data": {
    "Transfer": 0,
    "SecondSignature": 1,
    "DelegateRegistration": 2,
    "Vote": 3,
    "MultiSignature": 4,
    "Ipfs": 5,
    "TimelockTransfer": 6,
    "MultiPayment": 7,
    "DelegateResignation": 8
  }
}
```



## 获取交易费用（非动态）

静态交易费用高于动态交易费用

### 请求接口

```text
GET /api/v2/transactions/fees
```

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/transactions/fees
```

### 返回结果

```json
{
  "data": {
    "transfer": 10000000,
    "secondSignature": 500000000,
    "delegateRegistration": 2500000000,
    "vote": 100000000,
    "multiSignature": 500000000,
    "ipfs": 0,
    "timelockTransfer": 0,
    "multiPayment": 0,
    "delegateResignation": 0
  }
}
```
