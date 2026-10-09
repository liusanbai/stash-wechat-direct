# WeChat Direct | Stash Override

微信 / 腾讯系域名强制直连，解决开 VPN 后微信图片、视频加载慢的问题。

## 功能

- 微信 / 腾讯系域名（`qq.com`、`wechat.com`、`qpic.cn`、`tencent.com` 等）全部走 DIRECT
- DNS 策略：微信域名指定走国内 DoH（阿里 `dns.alidns.com` + 腾讯 `doh.pub`），确保解析到国内 CDN 节点
- fake-ip-filter：微信域名排除出 fake-ip，返回真实 IP，确保 GEOIP / CIDR 规则正确匹配
- 适用于国际版微信（海外服务器）及国内微信

## 安装

在 Stash 中：

1. 配置 → 覆写 → `+` → 从 URL 下载
2. 填入：

```
https://github.com/liusanbai/stash-wechat-direct/releases/latest/download/WeChat-Direct.stoverride
```

3. 确认覆写已启用
4. 回首页点重载

## 覆盖的域名

| 分类 | 域名 |
|---|---|
| 微信核心 | `weixin.qq.com`、`wechat.com`、`weixinbridge.com`、`servicewechat.com` |
| 图片 CDN | `qpic.cn`（含 `mmbiz`/`mmbiz2-4`）、`qlogo.cn` |
| 腾讯 CDN | `gtimg.com`、`qcloud.com`、`myqcloud.com`、`tencent.com` |
| QQ 通用 | `qq.com`、`qqmail.com` |
| 微信短链 | `szshort`、`szextshort`、`szminorshort.weixin.qq.com` |
| 视频 CDN | `video.qq.com`、`livevideo.qq.com`、`v.qq.com` |

## 验证

安装后打开 Stash → 请求日志 → 微信里点一张图 → 确认策略列为 `DIRECT`。

## 技术依据

- [Stash Override 文档](https://stash.wiki/en/configuration/override) — rules 数组 prepend 到原配置最前面
- [Stash 配置样例](https://stash.wiki/configuration/example-config) — nameserver-policy / fake-ip-filter

## License

MIT
