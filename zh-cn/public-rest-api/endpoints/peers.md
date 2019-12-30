# 节点(Peers)



## 获取所有Peer节点

获取所有已知 `Peer`节点，仅显示公共节点。

### 接口

```text
GET /api/v2/peers
```

### 查询参数

| 名称    | 类型   | 描述                   | 是否必填 |
| :------ | :----- | :--------------------- | :------- |
| page    | int    | 将返回页面编号         | 否       |
| limit   | int    | 每页的资源数量         | 否       |
| port    | int    | 筛选资源的端口         | 否       |
| status  | string | 筛选资源的状态         | 否       |
| os      | string | 用于过滤资源的操作系统 | 否       |
| version | string | 筛选资源的节点版本     | 否       |
| orderBy | string | 资源排序所依据的列     | 否       |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/peers?limit=1
```



```json
{
	"meta": {
		"count": 1,
		"pageCount": 26,
		"totalCount": 26,
		"next": "/api/v2/peers?limit=1&page=2",
		"previous": null,
		"self": "/api/v2/peers?limit=1&page=1",
		"first": "/api/v2/peers?limit=1&page=1",
		"last": "/api/v2/peers?limit=1&page=26"
	},
	"data": [{
		"ip": "114.115.141.56",
		"port": 4102,
		"version": "2.3.22",
		"height": 1284086,
		"status": 200,
		"os": "linux",
		"latency": 12
	}]
}
```



## 获取单个Peer

通过IP地址可以查询到单个`Peer`。但是，如果`Peer`禁用了其公共API，那么只能通过 `P2P` 内部API才能访问它们。

### 接口

```text
GET /api/v2/peers/{ip}
```

### 查询参数

| 名称 | 类型   | 描述                   | 是否必填 |
| :--- | :----- | :--------------------- | :------- |
| ip   | string | 要检索的对等点的IP地址 | 是       |

### 请求示例

```shell
curl http://openapi.tgichain.com/api/v2/peers/114.115.141.56
```

### 返回参数

```json
{
	"data": {
		"ip": "114.115.141.56",
		"port": 4102,
		"version": "2.3.22",
		"height": 1284093,
		"status": 200,
		"os": "linux",
		"latency": 8
	}
}
```


