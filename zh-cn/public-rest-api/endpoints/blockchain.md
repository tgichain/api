# 区块链（Blockchain）

> 获取整个区块链的最新区块和供应

### 请求接口

```text
GET /api/v2/blockchain
```

### 请求示例

```shell
curl https://api.ark.io/api/blockchain
```

### 返回结果

```json
{
  "data": {
    "block": {
      "height": 8051250,
      "id": "16024042256653583473"
    },
    "supply": 14095130200000004
  }
}
```







