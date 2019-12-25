# 区块（Blocks）



## 获取所有区块

### 请求接口 ###

```
GET /api/v2/blocks
```

### 查询参数 ###

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |
| id | string | 区块ID | 否 |
| height | int | 区块高度 | 否 |

### 请求示例1

```shell
curl https://api.ark.io/api/v2/blocks?limit=2
```

### 返回结果1

```json
{
	"meta": {
		"count": 2,
		"pageCount": 640426,
		"totalCount": 1280852,
		"next": "/api/v2/blocks?limit=2&page=2",
		"previous": null,
		"self": "/api/v2/blocks?limit=2&page=1",
		"first": "/api/v2/blocks?limit=2&page=1",
		"last": "/api/v2/blocks?limit=2&page=640426"
	},
	"data": [{
		"id": "10630141091355819109",
		"version": 0,
		"height": 1283476,
		"previous": "14573972898629373888",
		"forged": {
			"reward": 200000000,
			"fee": 0,
			"total": 200000000,
			"amount": 0
		},
		"payload": {
			"hash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			"length": 0
		},
		"generator": {
			"username": "song006",
			"address": "MQfXycApLLteAcAGJguAm687Wk4oJPPQbq",
			"publicKey": "028e6d39a454339f93f2c7d2254bc73443936a81ebd0363dd74249ceb4b665fa23"
		},
		"signature": "3045022100a5130aab3ac27e50912164bc4836c8520b72d181c2919507cf81e918bb407461022062127e69802901265c35dc066ac9f6a35b026c6734950e2f565f76be2146cf1a",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098456,
			"unix": 1577172376,
			"human": "2019-12-24T07:26:16.000Z"
		}
	}, {
		"id": "14573972898629373888",
		"version": 0,
		"height": 1283475,
		"previous": "7928756416190771000",
		"forged": {
			"reward": 200000000,
			"fee": 0,
			"total": 200000000,
			"amount": 0
		},
		"payload": {
			"hash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			"length": 0
		},
		"generator": {
			"username": "shan",
			"address": "MAT3pSecw3zufHcPjfLvbBWRkd8u6TT7kW",
			"publicKey": "0216309a945c44b6552d5d003157f6ae6c634068548610e0c2e8527b4761213256"
		},
		"signature": "3045022100b6a60bf55ea969c073489b212e8a9360661eec5ab22db614c3c9747517e856510220411392a6bf55c3c298a7a65a98a6af35f191bb457dfbfae13ad016de3845d919",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098448,
			"unix": 1577172368,
			"human": "2019-12-24T07:26:08.000Z"
		}
	}]
}
```

### 请求示例2

```shell
curl https://api.ark.io/api/v2/blocks?height=1283475
```
### 返回结果2

```json
{
	"meta": {
		"count": 1,
		"pageCount": 2,
		"totalCount": 101,
		"next": "/api/v2/blocks?height=1283475&page=2&limit=100",
		"previous": null,
		"self": "/api/v2/blocks?height=1283475&page=1&limit=100",
		"first": "/api/v2/blocks?height=1283475&page=1&limit=100",
		"last": "/api/v2/blocks?height=1283475&page=2&limit=100"
	},
	"data": [{
		"id": "14573972898629373888",
		"version": 0,
		"height": 1283475,
		"previous": "7928756416190771000",
		"forged": {
			"reward": 200000000,
			"fee": 0,
			"total": 200000000,
			"amount": 0
		},
		"payload": {
			"hash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			"length": 0
		},
		"generator": {
			"username": "shan",
			"address": "MAT3pSecw3zufHcPjfLvbBWRkd8u6TT7kW",
			"publicKey": "0216309a945c44b6552d5d003157f6ae6c634068548610e0c2e8527b4761213256"
		},
		"signature": "3045022100b6a60bf55ea969c073489b212e8a9360661eec5ab22db614c3c9747517e856510220411392a6bf55c3c298a7a65a98a6af35f191bb457dfbfae13ad016de3845d919",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098448,
			"unix": 1577172368,
			"human": "2019-12-24T07:26:08.000Z"
		}
	}]
}
```



## 获取单个区块

根据区块ID或区块高度查询区块。

### 请求接口

```text
GET /api/blocks/{id|height}
```

### 请求参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| {id\|height} | string | 要检索的区块ID或高度 | 是 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/blocks/14573972898629373888
```

```shell
curl https://api.ark.io/api/v2/blocks/1283475
```

### 返回结果

```json
{
	"data": {
		"id": "14573972898629373888",
		"version": 0,
		"height": 1283475,
		"previous": "7928756416190771000",
		"forged": {
			"reward": 200000000,
			"fee": 0,
			"total": 200000000,
			"amount": 0
		},
		"payload": {
			"hash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
			"length": 0
		},
		"generator": {
			"username": "shan",
			"address": "MAT3pSecw3zufHcPjfLvbBWRkd8u6TT7kW",
			"publicKey": "0216309a945c44b6552d5d003157f6ae6c634068548610e0c2e8527b4761213256"
		},
		"signature": "3045022100b6a60bf55ea969c073489b212e8a9360661eec5ab22db614c3c9747517e856510220411392a6bf55c3c298a7a65a98a6af35f191bb457dfbfae13ad016de3845d919",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098448,
			"unix": 1577172368,
			"human": "2019-12-24T07:26:08.000Z"
		}
	}
}
```



## 获取区块的交易

### 接口

```text
GET /api/blocks/{id|height}/transactions
```

### 路径参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| {id\|height} | string | 区块ID或高度 | 是 |

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/blocks/2773147314821565087/transactions
```

### 返回结果

```json
{
	"meta": {
		"count": 1,
		"pageCount": 2,
		"totalCount": 101,
		"next": "/api/v2/blocks/2773147314821565087/transactions?page=2&limit=100",
		"previous": null,
		"self": "/api/v2/blocks/2773147314821565087/transactions?page=1&limit=100",
		"first": "/api/v2/blocks/2773147314821565087/transactions?page=1&limit=100",
		"last": "/api/v2/blocks/2773147314821565087/transactions?page=2&limit=100"
	},
	"data": [{
		"id": "c2499fb8d65c34282e0da2facf43255f7e73cee86bfcff69ed55dd14be299dd8",
		"blockId": "2773147314821565087",
		"version": 1,
		"type": 0,
		"amount": 5106790000000,
		"fee": 10000000,
		"sender": "MS2RnsMmrPk6UGnnc5nJ59EtVDr9GUSoDP",
		"recipient": "M9mey7hRk3z93UtyYPXw3KYVd2rFgcUm5o",
		"signature": "30440220378f3e46459bc1948eb4d8a5d976a45b25abe2eb2c1f6eb831b05fc2ebfb008502200936949629ef5777ece19ec875d44b3a07173decc7ae6ded9990a80b67a80c1c",
		"confirmations": 240,
		"timestamp": {
			"epoch": 11097158,
			"unix": 1577171078,
			"human": "2019-12-24T07:04:38.000Z"
		}
	}]
}
```



## 搜索所有区块

可以使用搜索资源过滤特定区块。在节点端过滤区块要比大负载请求并在客户端过滤有效负载有效得多。

### 请求接口

```text
POST /api/v2/blocks/search
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回页的编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 内容参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 区块ID | 否 |
| version | int | 区块版本 | 否 |
| previousBlock | int | 前一个区块ID | 否 |
| payloadHash | string | payload的哈希值 | 否 |
| generatorPublicKey | string | 区块制造者的公钥 | 否 |
| blockSignature | string | 区块签名 | 否 |
| timestamp | object | 区块创建的时间戳范围。从第一块区块创建的秒数来计算。 | 否 |
| timestamp.from | int | 区块创建时间起始 | 否 |
| timestamp.to | int | 区块创建时间截止 | 否 |
| height | object | 区块的高度范围，第一个区块的高度是1 | 否 |
| height.from | int | 区块高度起始 | 否 |
| height.to | int | 区块高度截止 | 否 |
| numberOfTransactions | object | 区块交易数量 | 否 |
| numberOfTransactions.from | int | 区块交易数量起始 | 否 |
| numberOfTransactions.to | int | 区块交易数量截止 | 否 |
| totalAmount | object | 区块内交易总额，包括区块奖励、交易费用和交易金额 | 否 |
| totalAmount.from | int | 区块交易总额起始 | 否 |
| totalAmount.to | int | 区块交易总额截止 | 否 |
| totalFee | object | 区块内所有交易费用总和 | 否 |
| totalFee.from | int | 区块内所有交易费用总和起始 | 否 |
| totalFee.to | int | 区块内所有交易费用总和截止 | 否 |
| reward | object | 区块交易奖励 | 否 |
| reward.from | int | 区块奖励范围起始 | 否 |
| reward.to | int | 区块奖励范围截止 | 否 |
| payloadLength | object | payload长度 | 否 |
| payloadLength.from | int | 区块有效payload长度必须大于或等于这个值 | 否 |
| payloadLength.to | int | 区块有效payload长度必须小于或等于这个值 | 否 |

### 请求示例

```shell
curl --data 'numberOfTransactions={ "from": 2, "to": 5 }' https://api.ark.io/api/v2/blocks/search?limit=2
```
### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 2583,
		"totalCount": 5165,
		"next": "/api/v2/blocks/search?limit=2&page=2",
		"previous": null,
		"self": "/api/v2/blocks/search?limit=2&page=1",
		"first": "/api/v2/blocks/search?limit=2&page=1",
		"last": "/api/v2/blocks/search?limit=2&page=2583"
	},
	"data": [{
		"id": "5316954617032410169",
		"version": 0,
		"height": 1271863,
		"previous": "4610935101755089936",
		"forged": {
			"reward": 200000000,
			"fee": 50000000,
			"total": 250000000,
			"amount": 399322300000000
		},
		"payload": {
			"hash": "edd826880b1fee53022435c04b845d39ff4bc374caf96ce5f6105787351deb04",
			"length": 160
		},
		"generator": {
			"username": "tgic3",
			"address": "MUGv35V4KL43riiyyyfvFhSXiT3EdZ5LRt",
			"publicKey": "025e18c537633b629a8598aefc21cf10ab72e632e306d0af1e30726a99232e96de"
		},
		"signature": "3045022100fe95ddcff1c39fa6bfdaf914f49479ed45788b1a67a8965e28982738d762f3fe022076f0eb9faa2e877dd765fd92797ead0a4710224a1068d60efff7a6c478259196",
		"transactions": 5,
		"timestamp": {
			"epoch": 11005000,
			"unix": 1577078920,
			"human": "2019-12-23T05:28:40.000Z"
		}
	}, {
		"id": "3005306188126403981",
		"version": 0,
		"height": 1266038,
		"previous": "14465704379557346327",
		"forged": {
			"reward": 200000000,
			"fee": 20000000,
			"total": 220000000,
			"amount": 50000000000
		},
		"payload": {
			"hash": "38459ae09515f8b4a9c86e8389f2eb8d3596cd6c33230a7888a3e41e3a19a9ba",
			"length": 64
		},
		"generator": {
			"username": "bingo",
			"address": "MTNf8k3jUpnzJA6zbkC7meGZW8FgesAjY5",
			"publicKey": "02e3bed151c131a9b518994ee1ceb05780a585d8c63017fbaf636bb92ed4ce86ee"
		},
		"signature": "30440220020561405eba2832bc78f0da66b63cc2a6f596ccd841f226513e63711605b92002204b1a086a3b9cf0496c8dbb68ffef9b10f09eb136bb6ff88152ae80277806d9da",
		"transactions": 2,
		"timestamp": {
			"epoch": 10957552,
			"unix": 1577031472,
			"human": "2019-12-22T16:17:52.000Z"
		}
	}]
}
```

