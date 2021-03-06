### 1. 接口描述
本接口 (GetDeviceShadow) 用于查询虚拟设备信息。

接口请求域名：`iotcloud.api.qcloud.com`

### 2. 输入参数

以下请求参数列表仅列出了接口请求参数，其它参数见 [公共请求参数](https://cloud.tencent.com/document/api/213/6976) 页面。

| 参数名称       | 必选   | 类型     | 描述                             |
| ---------- | ---- | ------ | ------------------------------ |
| productID  | 是    | String | 产品ID                           |
| deviceName | 是    | String | 设备名称。命名规则：[a-zA-Z0-9:_-]{1,48} |

### 3. 输出参数

| 参数名称      | 类型       | 描述                                       |
| --------- | -------- | ---------------------------------------- |
| code      | Int      | 公共错误码。0 表示成功，其他值表示失败，详见[公共错误码](https://cloud.tencent.com/document/product/634/12279)页面 |
| codeDesc  | String   | 返回码描述                                    |
| message   | String   | 模块错误信息描述，格式为 "（模块错误码）模块错误信息" ，详见本页面的[模块错误码](#module_error_info) |
| state     | Object   | 虚拟设备当前状态                                 |
| metadata  | Object   | 虚拟设备属性的元信息，包括创建时间或者最后修改时间                |
| timestamp | DateTime | 服务器返回时间                                  |
| version   | Long     | 当前虚拟设备的版本号                               |

### 4. 示例

输入
<pre>
  https://iotcloud.api.qcloud.com/index.php?Action=GetDeviceShadow
  &deviceName=apple
  &productID=ABCDE12345
  &<<a href="https://cloud.tencent.com/document/api/213/6976">公共请求参数</a>>
</pre>

输出
```json
{
    "data":{
      "payload":{
          "state": {
              "reported": {
                  "red": "red"
              }
          }
          "metadata": {
              "reported": {
                  "red": {
                      "timestamp": 1509092895971
                  }
              }
          },
          "timestamp": 1509440846572,
          "version": 4
      }
      "result":0,
      "timestamp":1509440846582,
      "type":"get"
	}
    "message": "",
    "codeDesc": "Success",
    "code": 0
}
```
<span id = "module_error_info"></span>
### 5. 模块错误码

| 模块错误码 | 描述              |
| ----- | --------------- |
| 5000  | 请求中缺少关键字段信息     |
| 5001  | shadow不存在       |
| 5100  | 内部服务器错误，请联系技术人员 |




