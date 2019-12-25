# 代表（Delegates）



## 获取所有代表

您可以通过这个接口分页获取所有代表。默认会返回所有的代表，而不仅仅是前51个代表。

如果代表节点处于离线状态，则仍然通过此API返回；代表与实际节点无关，只与公链上注册的钱包有关。

### 请求接口

```text
GET /api/v2/delegates
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 将返回的页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例1

```shell
curl https://api.ark.io/api/v2/delegates
```
### 返回结果1

```json
{
	"meta": {
		"count": 82,
		"pageCount": 1,
		"totalCount": 82,
		"next": null,
		"previous": null,
		"self": "/api/v2/delegates?page=1&limit=100",
		"first": "/api/v2/delegates?page=1&limit=100",
		"last": "/api/v2/delegates?page=1&limit=100"
	},
	"data": [{
		"username": "liang",
		"address": "MLP6vhdVYD1aodrUWjZWCvzVSzscRqxaE1",
		"publicKey": "025f44882dc97bc50a1df03308bf1226bc09ff8f8b73888feb94148d9d51221c4f",
		"votes": 463665101276020,
		"rank": 1,
		"blocks": {
			"produced": 52014,
			"last": {
				"id": "3615722167853021711",
				"height": 1283624,
				"timestamp": {
					"epoch": 11099640,
					"unix": 1577173560,
					"human": "2019-12-24T07:46:00.000Z"
				}
			}
		},
		"production": {
			"approval": 0.66
		},
		"forged": {
			"fees": 11400000000,
			"rewards": 10402800000000,
			"total": 10414200000000
		}
	},
	...
	]
}
```

### 请求示例2
```shell
curl "https://api.ark.io/api/v2/delegates?page=5&limit=2"
```

### 请求结果2

```json
{
	"meta": {
		"count": 2,
		"pageCount": 41,
		"totalCount": 82,
		"next": "/api/v2/delegates?page=6&limit=2",
		"previous": "/api/v2/delegates?page=4&limit=2",
		"self": "/api/v2/delegates?page=5&limit=2",
		"first": "/api/v2/delegates?page=1&limit=2",
		"last": "/api/v2/delegates?page=41&limit=2"
	},
	"data": [{
		"username": "microsof",
		"address": "MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv",
		"publicKey": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3",
		"votes": 140648688242040,
		"rank": 9,
		"blocks": {
			"produced": 42727,
			"last": {
				"id": "5400742734018714186",
				"height": 1283658,
				"timestamp": {
					"epoch": 11099912,
					"unix": 1577173832,
					"human": "2019-12-24T07:50:32.000Z"
				}
			}
		},
		"production": {
			"approval": 0.2
		},
		"forged": {
			"fees": 10880000000,
			"rewards": 8482800000000,
			"total": 8493680000000
		}
	}, {
		"username": "tony",
		"address": "MGwex9hKkCDNuf98pDgzSoCb9YG2EG9EeS",
		"publicKey": "021c775be6d73a8949bb98368a05007f54d6f11fa3ac6dbe2472ce42dbebed47d6",
		"votes": 138963553230980,
		"rank": 10,
		"blocks": {
			"produced": 53593,
			"last": {
				"id": "7755519973188598577",
				"height": 1283653,
				"timestamp": {
					"epoch": 11099872,
					"unix": 1577173792,
					"human": "2019-12-24T07:49:52.000Z"
				}
			}
		},
		"production": {
			"approval": 0.2
		},
		"forged": {
			"fees": 14820000000,
			"rewards": 10655800000000,
			"total": 10670620000000
		}
	}]
}
```



## 获取单个代表

可以通过用户名、地址和公钥查询特定的代表。

### 请求接口

```text
GET /api/v2/delegates/{username|address|publicKey}
```

### 请求参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| {username\|address\|publicKey} | string | 代表标识符（用户名，地址，公钥） | 是 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/delegates/microsof
```

```shell
curl https://api.ark.io/api/v2/delegates/MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv
```

```shell
curl https://api.ark.io/api/v2/delegates/032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3
```
### 返回结果

```json
{
	"data": {
		"username": "microsof",
		"address": "MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv",
		"publicKey": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3",
		"votes": 140648888242040,
		"rank": 9,
		"blocks": {
			"produced": 42728,
			"last": {
				"id": "4965240926439365075",
				"height": 1283689,
				"timestamp": {
					"epoch": 11100160,
					"unix": 1577174080,
					"human": "2019-12-24T07:54:40.000Z"
				}
			}
		},
		"production": {
			"approval": 0.2
		},
		"forged": {
			"fees": 10880000000,
			"rewards": 8483000000000,
			"total": 8493880000000
		}
	}
}
```



## 获取代表的区块

### 请求接口

```text
GET /api/v2/delegates/{username|address|publicKey}/blocks
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| {username\|address\|publicKey} | string | 要检索的代表标识符 | 是 |

### 路径参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 要返回的页面编号 | 否 |
| limit | int | 每页的资源数量 | 否 |

### 请求示例

```shell
curl "https://api.ark.io/api/v2/delegates/microsof/blocks?page=5&limit=2"
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 20646,
		"totalCount": 41292,
		"next": "/api/v2/delegates/microsof/blocks?page=6&limit=2",
		"previous": "/api/v2/delegates/microsof/blocks?page=4&limit=2",
		"self": "/api/v2/delegates/microsof/blocks?page=5&limit=2",
		"first": "/api/v2/delegates/microsof/blocks?page=1&limit=2",
		"last": "/api/v2/delegates/microsof/blocks?page=20646&limit=2"
	},
	"data": [{
		"id": "6257497957022957519",
		"version": 0,
		"height": 1283511,
		"previous": "8813890528428322941",
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
			"username": "microsof",
			"address": "MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv",
			"publicKey": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"
		},
		"signature": "3045022100ee20e8a78bb3e35200c63062a809a814a01aabd9f240e3b319eb4446905867ed02201f9483c94f2f41ef687dc976bfc3c76365aa594939e052da02bfe0f00d6ea4d2",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098736,
			"unix": 1577172656,
			"human": "2019-12-24T07:30:56.000Z"
		}
	}, {
		"id": "746401161285900763",
		"version": 0,
		"height": 1283489,
		"previous": "15336826928577783002",
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
			"username": "microsof",
			"address": "MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv",
			"publicKey": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"
		},
		"signature": "3044022007b444d55fa2ce1477c84bb72920821c21ed85a79c71a3880a3f3e4798b0067402205a76ddac4f40498bd98a8c650c55103ff8825388d8c776a69a54763ab441b258",
		"transactions": 0,
		"timestamp": {
			"epoch": 11098560,
			"unix": 1577172480,
			"human": "2019-12-24T07:28:00.000Z"
		}
	}]
}
```



## 获取代表的选民

### 请求接口

```text
GET /api/delegates/{username|address|publicKey}/voters
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| {username\|address\|publicKey} | string | 要检索的代表标识符 | 是 |

### 路径参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/delegates/MR7E7tr2M4tQ3PdV8JcpSefiyDw8SdeeNv/voters?page=5&limit=2
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 7,
		"totalCount": 13,
		"next": "/api/v2/delegates/microsof/voters?page=6&limit=2",
		"previous": "/api/v2/delegates/microsof/voters?page=4&limit=2",
		"self": "/api/v2/delegates/microsof/voters?page=5&limit=2",
		"first": "/api/v2/delegates/microsof/voters?page=1&limit=2",
		"last": "/api/v2/delegates/microsof/voters?page=7&limit=2"
	},
	"data": [{
		"address": "MPJNqMbPCgYhkhNjmHYSnnYoGZ6xo7SyLJ",
		"publicKey": "031d7631d5314f023a1402ad9f94789d8bc69376d7457fcbd74d5b0287e951ca59",
		"username": "qss",
		"secondPublicKey": null,
		"balance": 7000000000,
		"isDelegate": true,
		"vote": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"
	}, {
		"address": "MKUq3eooqqAxvLyHjT4Keq3fuRrXS7iptf",
		"publicKey": "0326b38d0fc0fe8f6b9bdaba84ca765bf321ec601ab049285a0a363435bc1348de",
		"username": null,
		"secondPublicKey": null,
		"balance": 39000000,
		"isDelegate": false,
		"vote": "032370229ca464d1b6c1265c998dbdae5c7c4a7212e771df987dc1eca2247308a3"
	}]
}
```



## 搜索代表

### 请求接口

```text
POST /api/v2/delegates/search
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 参数内容

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| address | string | 代表地址 | 否 |
| publicKey | string | 代表公钥 | 否 |
| username | string | 代表用户名 | 否 |
| usernames | array | 代表用户名组 | 否 |
| approval | object | 代表批准率 | 否 |
| approval.from | float | 批准率下限 | 否 |
| approval.to | float | 批准率上限 | 否 |
| forgedFees | object | 锻造费用 | 否 |
| forgedFees.from | int | 锻造费用起始 | 否 |
| forgedFees.to | int | 锻造费用截止 | 否 |
| forgedRewards | object | 锻造奖励 | 否 |
| forgedRewards.from | int | 锻造奖励起始 | 否 |
| forgedRewards.to | int | 锻造奖励截止 | 否 |
| forgedTotal | object | 锻造总量 | 否 |
| forgedTotal.from | int | 锻造总量起始 | 否 |
| forgedTotal.to | int | 锻造总量截止 | 否 |
| producedBlocks | object | 生成区块数 | 否 |
| producedBlocks.from | int | 生成区块数的起始 | 否 |
| producedBlocks.to | int | 生成区块数的截止 | 否 |
| voteBalance | object | 投票金额 | 否 |
| voteBalance.from | int | 投票金额下限 | 否 |
| voteBalance.to | int | 投票金额上限 | 否 |

### 请求示例

```shell
curl --data 'producedBlocks={ "from": 60000 }' https://api.ark.io/api/v2/delegates/search
```
### 返回结果

```json
{
	"meta": {
		"count": 1,
		"pageCount": 1,
		"totalCount": 1,
		"next": null,
		"previous": null,
		"self": "/api/v2/delegates/search?page=1&limit=100",
		"first": "/api/v2/delegates/search?page=1&limit=100",
		"last": "/api/v2/delegates/search?page=1&limit=100"
	},
	"data": [{
		"username": "tgic",
		"address": "MH6UfwP5dc8q9oqPWyDUtR6ZhMVxdeJgNZ",
		"publicKey": "02e25f2a71ece0c45edaa354c09e26177fc72c460e25d17248b015ded70672f92c",
		"votes": 261094516779080,
		"rank": 2,
		"blocks": {
			"produced": 60221,
			"last": {
				"id": "251073909296918343",
				"height": 1283884,
				"timestamp": {
					"epoch": 11101720,
					"unix": 1577175640,
					"human": "2019-12-24T08:20:40.000Z"
				}
			}
		},
		"production": {
			"approval": 0.37
		},
		"forged": {
			"fees": 23980000000,
			"rewards": 11839400000000,
			"total": 11863380000000
		}
	}]
}
```




