# 节点(Node)



## 获取节点配置

### 请求接口

```text
GET /api/v2/node/configuration
```

### 请求示例

```shell
curl https://api.ark.io/api/v2/node/configuration
```

### 返回结果

```json
{
	"data": {
		"nethash": "7df0ca065f5aaa61986c407507a0fa90a5820d837218fda5807b85229c376ed4",
		"slip44": 1,
		"wif": 198,
		"token": "TGI",
		"symbol": "T",
		"explorer": "http://0.0.0.0:4200",
		"version": 50,
		"ports": {
			"@arkecosystem/core-p2p": 4102,
			"@arkecosystem/core-api": 4103
		},
		"constants": {
			"height": 20000,
			"reward": 200000000,
			"activeDelegates": 23,
			"blocktime": 8,
			"block": {
				"version": 0,
				"maxTransactions": 150,
				"maxPayload": 6291456
			},
			"epoch": "2019-08-17T20:32:00.058Z",
			"fees": {
				"staticFees": {
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
			},
			"vendorFieldLength": 255
		},
		"feeStatistics": [{
			"type": 0,
			"fees": {
				"minFee": 10000000,
				"maxFee": 10000000,
				"avgFee": 10000000
			}
		}, {
			"type": 3,
			"fees": {
				"minFee": 100000000,
				"maxFee": 100000000,
				"avgFee": 100000000
			}
		}, {
			"type": 2,
			"fees": {
				"minFee": 2500000000,
				"maxFee": 2500000000,
				"avgFee": 2500000000
			}
		}],
		"transactionPool": {
			"maxTransactionAge": 21600,
			"dynamicFees": {
				"enabled": false
			}
		}
	}
}
```



## 获取节点状态

### 请求接口

```text
GET /api/v2/node/status
```

### 请求示例

```shell
curl https://api.ark.io/api/v2/node/status
```

### 返回结果

```json
{
  "data": {
    "synced": true,
    "now": 3034451,
    "blocksCount": 0
  }
}
```



## 获取节点同步状态

与`获取节点状态`接口功能类似，提供节点同步状态信息。

### 请求接口

```text
GET /api/v2/node/syncing
```

### 请求示例

```shell
curl https://api.ark.io/api/v2/node/syncing
```

### 返回结果

```json
{
  "data": {
    "syncing": true,
    "blocks": -36,
    "height": 3034451,
    "id": "5444078994968869529"
  }
}
```

