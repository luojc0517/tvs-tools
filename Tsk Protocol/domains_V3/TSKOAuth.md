# 技能账号授权管理

## uniAccess管理接口

依赖于腾讯云小微TVS [unieAccess](https://github.com/TencentDingdang/tvs-tools/blob/master/doc/uniAccess%E6%8E%A5%E5%8F%A3%E8%83%BD%E5%8A%9B.md)通道能力，在使用uniAccess时需要通过设置`payload.domain`和`payload.intent`路由到不同接口，并且需要填充符合叮当规范的账号、设备信息。账号开放授权管理接口包括：

| domain    |    intent    | 接口说明 |
|-----------|--------------|---------|
| tsk_oauth | get_bind_state | 查询技能的账号绑定状态 |

### get_bind_state
DMSDK查询音箱的账号绑定状态。

#### request

+ 请求数据示例
```json
{
    "operType": "get_bind_state",
    "skillId": "caabf231-e655-11e7-8130-68cc6ea8c1f8",
    "deviceBaseInfo": {
        "appKey": "",
        "appAccessToken": "",
        "guid": "",
        "dsn": ""
    }
}
```

+ 参数说明

| 参数 | 说明 | 参数类型 | 必填 |
|------|-----|----------|----|
| `operType` | 操作类型，值同`payload.intent`，固定为`get_bind_state` | `string` | YES |
| `skillId` | 技能ID，QQ音乐技能填：`caabf231-e655-11e7-8130-68cc6ea8c1f8` | `string` | YES |
| `deviceBaseInfo` | 音箱设备信息 | `object` | YES |
| `deviceBaseInfo.appKey` | 音箱在开放平台申请的AppKey | `string` | YES |
| `deviceBaseInfo.appAccessToken` | 音箱在开放平台申请的AccessToken | `string` | YES |
| `deviceBaseInfo.guid` | 音箱的guid | `string` | YES |
| `deviceBaseInfo.dsn` | 音箱的dsn | `string` | YES |

#### response

```json
{
    "error": {
        "code": 0,
        "msg": ""
    },
    "accountBaseInfo": {
        "acctId": "1234567890123456",
        "acctType": "QQMusicOpenId",
        "appId": "13214567"
    }
}
```

+ 参数说明

| 参数 | 说明 | 参数类型 |
|------|-----|----------|
| `error` | 业务错误信息 | `object` |
| `error.code` | 业务错误码，请参照[说明](#业务错误码) | `int` |
| `error.msg` | 业务错误信息（Debug） | `string` |
| `accountBaseInfo` | 音箱绑定的账号信息 | `object` |
| `accountBaseInfo.acctType` | 音箱绑定的账号类型，可选值有：`QQOpenId`，`WechatOpenId`，`QQMusicOpenId` | `string` |
| `accountBaseInfo.appId` | 音箱绑定的帐号对应的应用ID | `string` |
| `accountBaseInfo.acctId` | 音箱绑定的帐号唯一ID（一般是OpenId） | `string` |

> 注意：账号类型`QQOpenId`/`WechatOpenId`将逐步替换为`QQMusicOpenId`

#### 如何使用？
1. 查到绑定状态是否说明授权成功？

> 授权的有效性与有效期、权限、用户的变更等相关，查到授权关系仅仅代表用户授权过，授权有效性需要在具体业务场景下使用才能校验是否有效。

2. 如何用来判断当前用户是否已经使用QQ音乐APP授权过？

> 可通过这些组合条件判断：`error.code == 0 && accountBaseInfo.acctType == “QQMusicOpenId”`

### 业务错误码

| 错误码 | 描述 |
| ------ | --- |
| `0`    | 成功 |
| `-1`   | 失败 |
| `-2`   | 频率限制 |
| `-101` | 请求端账号信息校验不通过 |
| `-102` | 请求数据不合法 |
