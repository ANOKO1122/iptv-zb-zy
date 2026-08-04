# 📺 自用 IPTV 直播源

> 个人自用的 IPTV 直播源。基于 [Guovin/iptv-api](https://github.com/Guovin/iptv-api) 自动**采集 → 测速 → 筛选 → 生成**，通过 Cloudflare Pages 加速订阅，供电视盒子 / 播放器使用。
>
> 本仓库只存放最终结果文件，不包含任何源项目代码。

---

## 🚀 订阅地址

把下面地址粘贴到电视盒子 / 播放器即可观看：

```
https://iptv-zb-zy.pages.dev/output/ipv4/result.m3u      ← 推荐（Cloudflare Pages 加速，更快更稳）
https://raw.githubusercontent.com/ANOKO1122/iptv-zb-zy/master/output/ipv4/result.m3u
```

> 使用 `#genre#` 分类，播放器会按「央视 / 香港 / 凤凰 / 澳门」分组展示。

---

## 📡 包含的频道（共 37 个）

- 🇨🇳 **央视 18 台**：CCTV-1 ~ CCTV-17、CCTV-5+
- 🇭🇰 **香港 9 台**：翡翠台、翡翠4K、明珠台、ViuTV、HOY TV、港台電視 31、港台電視 32、TVB无线新闻、星空卫视
- 🐦 **凤凰 3 台**：凤凰中文、凤凰资讯、凤凰香港
- 🎰 **澳门 7 台**：澳视澳门、澳门资讯、澳门综艺、澳视体育、澳视葡文、澳门卫星、澳門MACAU

---

## ⚙️ 怎么测速的

1. **定时拉取订阅源**：每天自动从两个外部订阅源拉取最新频道列表（大陆 + 香港）。
2. **模板匹配**：按 `config/user_demo.txt` 模板匹配频道，模板里没有的频道不会进入测速与结果。
3. **测速过滤**：对每个频道的源进行测速，过滤条件为：
   - 分辨率 ≥ `1280x720`
   - 速率 ≥ `0.75 M/s`
   - 每个频道最多保留 **2 个**源
4. **白名单免测速**：翡翠台 / 明珠台 / 凤凰 / 澳门等源，因本机直连测速不准（盒子却能流畅播放），加入**白名单直接保留**，不被误筛。
5. **生成并推送**：生成 `output/ipv4/result.m3u`（及 `result.txt`），自动提交推送到本仓库。

> 单次更新约 7 分钟，测速量约 250 条。

---

## 🙏 整合的源（感谢以下项目）

| 来源 | 提供内容 | 链接 |
|------|----------|------|
| **Guovin/iptv-api** | 项目本体：自动采集 / 测速 / 生成框架 | https://github.com/Guovin/iptv-api |
| **doubletree6/tvbox-iptv-subscription** | 大陆央视 / 卫视 / 凤凰（tvbus CDN，国内直连快） | https://github.com/doubletree6/tvbox-iptv-subscription |
| **sammy0101/hk-iptv-auto** | 香港频道（翡翠 / 明珠 / 港台電視 / TVB 等，每日更新） | https://github.com/sammy0101/hk-iptv-auto |
| **澳门广播电视 TDM** | 澳门官方台（澳视澳门 / 澳门资讯等） | https://www.tdm.com.mo |

再次感谢以上开源项目与频道源的维护者们 💙

---

## ⚠️ 说明

- 本仓库仅存放结果文件（`output/ipv4/result.m3u`），**仅供个人自用、学习交流**，请勿用于商业用途。
- 频道源来自公开订阅源，节目版权归原频道所有；如涉及侵权请联系删除。
- 频道源可能随网络环境变化，请以本仓库最新提交为准。
