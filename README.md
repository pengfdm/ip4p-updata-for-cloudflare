# github

‍

# 功能是利用Lucky插件的stun自定义脚本，自动更新域名（ipv6格式）为最新的stun外部访问的ip4p格式。

### 首先感谢及借鉴参考：natmap\wireguard-ip4p（wireguard软件）\Lucky\OpenAI

[https://github.com/heiher/natmap](https://github.com/heiher/natmap)

[https://github.com/HalcyonAzure/wireguard-ip4p](https://github.com/HalcyonAzure/wireguard-ip4p)

---

### 废话部分

起因是用了十六年的ipv4公网被的电信强制收回了（要公网IP只能去拉专线），**就在当地开始禁止携号转网的第二个月**。想想自己的那点需求，无非就是访问家里局域网设备。网页系列“赛博活佛”替换基本都能满足。以前远程局域网下载上传文件，一直用WireGuard接入本地局域网，可以自定义网段，不影响其他网络访问。没了公网ip后，使用过每次登录luck后台，看ip和端口，手动改接入点。逐步找到了“netmap”项目，后来又搜到了“wireguard-ip4p”项目，发现十分贴合自己的使用需求。

理论上只要是支持ip4p格式的软件都能使用，natmap上还有其他支持的项目，欢迎去使用。

---

### ip4p自定义格式介绍：

```bash
2001:0000:0000:0000:0000:XXXX:YYYY:ZZZZ
```

XXXX = 端口(16进制)YYYY = IPv4 高 16 位(16进制)ZZZZ = IPv4 低 16 位(16进制)

具体介绍ip4p详见natmap项目，[https://github.com/heiher/natmap/wiki/faq](https://github.com/heiher/natmap/wiki/faq)

---

## 使用方法：

修改以下内容，引号需要保留。

```bash
API_TOKEN="你的 Cloudflare API Token"     # 必填，dns的apiK，如"aannddidnind"
ZONE_ID="你的 Zone ID"                    # 必填，区域id，如"aannddidnind"
RECORD_ID="你的 DNS 记录 ID"              # 必填，dnsid（通过F12获取），如"aannddidnind"
DOMAIN_NAME="需要解析的域名"              # 必填，如"xyz.xyz.xyz"

ip="${ip}"                              # 选填，转换的IPv4地址，本处采用lucky插件的stun变量
port="${port}"                          # 选填，转换的IPv4端口，本处采用lucky插件的stun变量
```

---

复制到luck插件stun的自定义脚本触发内部。

![image](assets/image-20251201173713-u8z6kyu.png)

使用支持ip4的软件访问该域名即可。

### 致谢

最后强烈谴责电信这种强制切换用户IP的行为，。就是变相的把本应属于家庭用户的资源高价卖给专线用户。

‍
