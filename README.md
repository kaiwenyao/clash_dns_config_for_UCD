# clash_dns_config_for_UCD

适用于 Clash Verge Rev 的 DNS 覆写配置（设置 → DNS 覆写）。

## 主要字段

###   default-nameserver: 默认名称服务器

```yaml
system
```

### Nameserver: 名称服务器

```yaml
https://1.1.1.1/dns-query, https://223.5.5.5/dns-query, https://8.8.8.8/dns-query
```

### Proxy-server-nameserver 代理服务器名称服务器

```yaml
https://1.1.1.1/dns-query, https://8.8.8.8/dns-query
```

### fallback 回落名称服务器

```yaml
https://1.1.1.1/dns-query
```

## 完整配置

以下为完整的 DNS 覆写配置（对应 Clash Verge Rev 的 `dns_config.yaml`），可直接粘贴到 DNS 覆写的 YAML 编辑器中：

```yaml
dns:
  enable: true
  listen: :53
  ipv6: true
  prefer-h3: false
  respect-rules: false
  use-hosts: false
  use-system-hosts: false

  # 增强模式：fake-ip
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  fake-ip-range6: fdfe:dcba:9876::1/64
  fake-ip-filter-mode: blacklist
  fake-ip-filter:
  - '*.lan'
  - '*.local'
  - '*.arpa'
  - 'time.*.com'
  - 'ntp.*.com'
  - 'time.*.com'
  - '+.market.xiaomi.com'
  - localhost.ptlogin2.qq.com
  - '*.msftncsi.com'
  - www.msftconnecttest.com

  # 默认名称服务器
  default-nameserver:
  - system

  # 名称服务器
  nameserver:
  - https://1.1.1.1/dns-query
  - https://223.5.5.5/dns-query
  - https://8.8.8.8/dns-query

  # 代理服务器名称服务器
  proxy-server-nameserver:
  - https://1.1.1.1/dns-query
  - https://8.8.8.8/dns-query

  # 直连名称服务器
  direct-nameserver: []
  direct-nameserver-follow-policy: false

  # 回落名称服务器
  fallback:
  - https://1.1.1.1/dns-query
  fallback-filter:
    geoip: true
    geoip-code: CN
    ipcidr:
    - 240.0.0.0/4
    - 0.0.0.0/32
    domain:
    - +.google.com
    - +.facebook.com
    - +.youtube.com
```
