# 联通余量

## Surge Module

[联通余量](https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/10010.sgmodule)

## Scripts

Surge 和 Loon 仅在 WiFi 下继续执行

```
[MITM]
hostname = m.client.10010.com

[Script]
# Surge
联通余量: Cookie = type=http-request,pattern=^https?:\/\/m\.client\.10010\.com\/servicequerybusiness,requires-body=1,max-size=0,timeout=30,script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/cookie.js,debug=true
联通余量: 查询 = type=cron,cronexp=*/5 * * * *,timeout=30,script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/check.js,wake-system=true

# Loon
http-request ^https?:\/\/m\.client\.10010\.com\/servicequerybusiness script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/cookie.js, tag=联通余量Cookie
cron "*/5 * * * *" script-path=https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/check.js

# QuanX(未测试 不清楚如何判断当前网络是否为 WiFi)
^https?:\/\/m\.client\.10010\.com\/servicequerybusiness url script-request-header https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/cookie.js
*/5 * * * * https://raw.githubusercontent.com/xream/scripts/main/surge/modules/10010/check.js, tag=联通余量查询
```

## 获取 Cookie

登录中国联通 app, 打开余量查询, 获取 Cookie

## Scriptable

### BoxJs 订阅(可跳过)

使用 [BoxJs](https://chavyleung.gitbook.io/boxjs) 添加 [订阅](https://raw.githubusercontent.com/xream/scripts/main/boxjs/boxjs.json) 后, Scriptable 脚本可支持缓存 Cookie

### 脚本

依赖: [「小件件」开发环境.js](https://raw.githubusercontent.com/xream/scripts/main/scriptable/「小件件」开发环境.js)

[联通余量.js](https://raw.githubusercontent.com/xream/scripts/main/scriptable/10010/联通余量.js)

![小组件设置](https://i.loli.net/2021/07/22/3mnxdtJ8TFMfazu.jpg)

## 预览

![小组件](https://i.loli.net/2021/07/22/vFj9uLMp6BbZmWP.jpg)

![通知](https://i.loli.net/2021/07/22/n8JeRBoYXc51O97.jpg)

![其他](https://i.loli.net/2021/07/22/MguJz9LR8QlDqok.jpg)
