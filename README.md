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

> 使用 `#genre#` 分类，播放器会按「央视 / 凤凰 / 香港 / 澳门 / 台湾」分组展示。

---

## 📡 包含的频道（共 91 个）

- 🇨🇳 **央视**：CCTV-1 ~ CCTV-17、CCTV-5+、CGTN（doubletree6 源）
- 🐦 **凤凰系列**：凤凰中文 / 资讯 / 香港 + 高清 / 卫视台变体
- 🇭🇰 **香港**：翡翠台、翡翠4K、翡翠台北美版、明珠台、TVB翡翠台、华丽翡翠台、TVB明珠台、港台電視 31/32、TVB无线新闻 / 星河 / Plus / 千禧经典、无线新闻、ViuTV / VIUTV1 / J2 / HOY TV
- 🎰 **澳门**（第三方源）：澳门卫视、澳视澳门、澳视卫星
- 📡 **台湾 / 其他**：台视新闻、TVBS新闻台、三立戏剧、大立电视台、星空卫视、美亚电影、纬来精采、人间卫视、韩国电影、广州综合、南国都市、广东珠江/体育、海峡卫视 等

> 来源：核心香港台（翡翠/明珠/凤凰/TVB/ViuTV）来自 suxiang 的**「港澳代理」分组**（jdshipin 代理线路，直连流畅）；港台電視/台湾台/影视台等来自「港澳台频道」分组；央视来自 doubletree6。

---

## ⚙️ 怎么测速的

1. **定时拉取订阅源**：每天自动从两个外部订阅源拉取最新频道列表（大陆 + 香港）。
2. **模板匹配**：按 `config/user_demo.txt` 模板匹配频道，模板里没有的频道不会进入测速与结果。
3. **测速过滤**：对每个频道的源进行测速，过滤条件为：
   - 分辨率 ≥ `1280x720`
   - 速率 ≥ `0.4 M/s`（港澳台海外小分片源测速虚低，故门槛放低）
   - 每个频道最多保留 **2 个**源
4. **白名单例外**：仅 `jdshipin`（翡翠/明珠/凤凰/TVB 等代理线路）加白名单免测速——用户实测 2~4 M/s 流畅，但 iptv-api 并发分片测速测不准（平均 0.00），只能白名单保住；其余港澳台源全部实测速。
5. **生成并推送**：生成 `output/ipv4/result.m3u`（及 `result.txt`），自动提交推送到本仓库。

> 单次更新约 9~12 分钟，测速量约 460 条。

---

## 🙏 整合的源（感谢以下项目）

| 来源 | 提供内容 | 链接 |
|------|----------|------|
| **Guovin/iptv-api** | 项目本体：自动采集 / 测速 / 生成框架 | https://github.com/Guovin/iptv-api |
| **doubletree6/tvbox-iptv-subscription** | 大陆央视 / 卫视 / 凤凰（tvbus CDN，国内直连快） | https://github.com/doubletree6/tvbox-iptv-subscription |
| **suxuang/myIPTV** | 港澳台频道（「港澳代理」+「港澳台频道」两个分组：翡翠/明珠/凤凰/TVB/港台/台湾等） | https://github.com/suxuang/myIPTV |

再次感谢以上开源项目与频道源的维护者们 💙

---

## ⚠️ 说明

- 本仓库仅存放结果文件（`output/ipv4/result.m3u`），**仅供个人自用、学习交流**，请勿用于商业用途。
- 频道源来自公开订阅源，节目版权归原频道所有；如涉及侵权请联系删除。
- 频道源可能随网络环境变化，请以本仓库最新提交为准。
