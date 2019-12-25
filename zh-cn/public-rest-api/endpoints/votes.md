# 投票（Votes）

投票是一种特定的交易类型。 钱包地址可以给代表投票， 也可以自己投票。

> 代表不会从他的选民投票中获取币，他们产生的块的数量与他们的投票权重成正比。



## 获取全部投票

### 请求接口

```text
GET /api/v2/votes
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| page | int | 页面编号 | 否 |
| limit | int | 每页的数量 | 否 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/votes?page=5&limit=2
```

### 返回结果

```json
{
	"meta": {
		"count": 2,
		"pageCount": 360,
		"totalCount": 720,
		"next": "/api/v2/votes?page=6&limit=2",
		"previous": "/api/v2/votes?page=4&limit=2",
		"self": "/api/v2/votes?page=5&limit=2",
		"first": "/api/v2/votes?page=1&limit=2",
		"last": "/api/v2/votes?page=360&limit=2"
	},
	"data": [{
		"id": "a414a646e658d9094084e7b29533038657109503b0023dad806e702d338e0e0d",
		"blockId": "1659939974944751299",
		"version": 1,
		"type": 3,
		"amount": 0,
		"fee": 100000000,
		"sender": "MNDUMxj5qoqkK8Kk3wJovjQiMBz2BtKweb",
		"recipient": "MNDUMxj5qoqkK8Kk3wJovjQiMBz2BtKweb",
		"signature": "3045022100a985a5c7353b2c312ad6c574877bb4c272d12e5d218d3d39a1808b3eebcc0341022027eddef0f87fa66085cfb8fd66436bf0c8767358c168c2e8db9e2dabdb965545",
		"asset": {
			"votes": ["+030e8bfc124ae0e0e4f7999aa35f2d185884540bb4cf29fd9fe4022ce03648cf3a"]
		},
		"confirmations": 27971,
		"timestamp": {
			"epoch": 10944977,
			"unix": 1577018897,
			"human": "2019-12-22T12:48:17.000Z"
		}
	}, {
		"id": "13e83d207a062bbd5ffeba833d285664608e8e20a5fd6caf42d830883aa24f90",
		"blockId": "10185843270403804789",
		"version": 1,
		"type": 3,
		"amount": 0,
		"fee": 100000000,
		"sender": "MEzJ2RUyTtDBRC8HxXCxtzV8d9UwESysFb",
		"recipient": "MEzJ2RUyTtDBRC8HxXCxtzV8d9UwESysFb",
		"signature": "3045022100b7f48183fabdf21e6499841b6fe8ab74ab5bba0502248b691917af5c1636136b02203677ef3d8df00b5dae8705f37296c9c05c365d01977d5c41b723f601137ef6be",
		"asset": {
			"votes": ["-036a883d17cae33f1e255fb491c706895669a8e4024dee862f4aa77740b9c176d3"]
		},
		"confirmations": 27994,
		"timestamp": {
			"epoch": 10944783,
			"unix": 1577018703,
			"human": "2019-12-22T12:45:03.000Z"
		}
	}]
}
```



## 获取单个投票

可以使用投票的事务ID获取单个投票。投票的信息在`assets`字段，数组中每个项的第一个字符表示它是增加投票+，还是取消投票 -，后跟代表的公钥。

### 请求接口

```text
GET /api/v2/votes/{id}
```

### 查询参数

| 名称 | 类型 | 描述 | 是否必填 |
| :--- | :--- | :--- | :--- |
| id | string | 投票ID | 是 |

### 请求示例

```shell
curl https://api.ark.io/api/v2/votes/13e83d207a062bbd5ffeba833d285664608e8e20a5fd6caf42d830883aa24f90
```

### 返回结果

```json
{
	"data": {
		"id": "13e83d207a062bbd5ffeba833d285664608e8e20a5fd6caf42d830883aa24f90",
		"blockId": "10185843270403804789",
		"version": 1,
		"type": 3,
		"amount": 0,
		"fee": 100000000,
		"sender": "MEzJ2RUyTtDBRC8HxXCxtzV8d9UwESysFb",
		"recipient": "MEzJ2RUyTtDBRC8HxXCxtzV8d9UwESysFb",
		"signature": "3045022100b7f48183fabdf21e6499841b6fe8ab74ab5bba0502248b691917af5c1636136b02203677ef3d8df00b5dae8705f37296c9c05c365d01977d5c41b723f601137ef6be",
		"asset": {
			"votes": ["-036a883d17cae33f1e255fb491c706895669a8e4024dee862f4aa77740b9c176d3"]
		},
		"confirmations": 28018,
		"timestamp": {
			"epoch": 10944783,
			"unix": 1577018703,
			"human": "2019-12-22T12:45:03.000Z"
		}
	}
}
```
