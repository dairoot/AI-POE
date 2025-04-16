
## 环境变量

<table>
  <tr align="left">
    <th>分类</th>
    <th>变量名</th>
    <th>类型</th>
    <th>默认值</th>
    <th>描述</th>
  </tr>
  <tr align="left">
    <td rowspan="2">镜像后台</td>
    <td><code>ADMIN_USERNAME</code></td>
    <td><code>String</code></td>
    <td><code>None</code></td>
    <td>管理后台账号</td>
  </tr>
  <tr align="left">
    <td><code>ADMIN_PASSWORD</code></td>
    <td><code>String</code></td>
    <td><code>None</code></td>
    <td>管理后台密码</td>
  </tr>
   <tr align="left">
    <td rowspan="2">系统变量</td>
    <td><code>PROXY_URL_POOL</code></td>
    <td><code>String</code></td>
    <td><code>None</code></td>
    <td>代理池链接，多个代理用逗号分隔<br><code>http://username:password@ip:port,</code><br/><code>socks5://username:password@ip:port,</code><br/><code>socks5h://username:password@ip:port</code></td>
   </tr>
     <tr align="left">
    <td><code>AUTH_CODE</code></td>
    <td><code>String</code></td>
    <td><code>None</code></td>
    <td> 激活授权码 </code></td>
  </tr>
  </tr>
  
</table>



## 聊天 API 接口

POST: /v1/chat/completions

- 请求头:

| 字段            | 类型     | 默认值 | 必填 | 描述                                                                                                                                                |
| --------------- | -------- | ------ | ---- | ---------------- |
| `Authorization` | `string` | `None` | `是` | `Bearer ${ AUTHORIZATION }` 后台配置的API秘钥 |



- 请求参数:

| 参数名            | 类型    | 是否必须 | 描述                                                               |
| ----------------- | ------- | -------- | ------------------------------------------------------------------ |
| model             | string  | 是       | 模型名称  |
| messages          | array   | 是       | 消息内容                                                           |
| stream            | boolean | 否       | 是否开启流式返回                                                   |



- 模型介绍:

| 模型             | 描述                                                                                                                                                |
| --------------- |  ---------------- |
| `grok-2`  | - |
| `grok-3`  | - |
| `grok-3-thinking`  | - |
| `grok-3-deepsearch`  | - |
| `grok-3-deepersearch`  | - |
| `claude-sonnet-3.7`  | - |
| `claude-sonnet-3.7-reasoner`  | - |
| `claude-haiku-3.5`  | - |
| `claude-sonnet-3.5`  | - |
| `claude-opus-3`  | - |


聊天接口请求示例：

```bash
export Authorization=GrokToken 或者 环境变量的Authorization
export yourUrl=http://127.0.0.1:50005


curl --location "${yourUrl}/v1/chat/completions" \
--header 'Content-Type: application/json' \
--header "Authorization: Bearer ${Authorization}" \
--data '{
     "stream": true,
     "model": "grok-2",
     "messages": [{"role": "user", "content": "你好呀!"}],
   }'
```
