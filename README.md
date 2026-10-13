# 电信 VPS 推荐：认准 AS4809 回程，香港/日本/美西机房怎么挑、入门机月付多少

在家里或公司用电信宽带，打开一台海外服务器上的网站，白天还行，一到晚高峰就开始转圈、丢包、图片加载一半卡住。搜「电信 VPS 推荐」的人，卡的就是这一步：机器本身不贵，问题是数据从海外回你这条电信线，走的是哪条路。

所以这篇文章不按商家排行榜写，先从线路讲起。搞懂电信出海的三档路由之后，你会发现很多"便宜大碗"的机器为什么用起来难受，也会明白为什么 DMIT 这种报价明显偏高的商家长年被放在推荐名单里。

## 电信出口分三档，价差全在这里

电信的国际出口大致是这么分的：

**163 骨干网（AS4134）** 是最普通的通道，绝大多数低价 VPS 走这条。它本身没坏，只是国际出口带宽长期紧张，晚高峰拥塞是结构性的，不是商家"没优化好"。

**CN2 GT** 属于 CN2 的普通产品，去程有时能走 CN2，回程绕回 163 的情况很常见。名字里有 CN2，实际体验跟纯 163 差距有限，这也是很多"CN2 优化"宣传注水的地方。

**CN2 GIA（AS4809）** 是电信的国际精品网，去程回程都跑这条骨干，带宽成本高、资源有限，能拿到 GIA 的商家本来就不多。对电信用户来说，回程是不是 GIA，比机房在哪个城市更重要——因为回程决定了你下载、看视频、刷网页的实际体感。

联通和移动各有对应的高端线：联通 **9929（CUII）**、移动 **CMIN2（AS58807）**。所以你在套餐页面上会看到"三网优化"这种说法，意思通常是三家的回程各走各自的好路。真正要看的是回程方向，单向优化和双向优化的差距，实际用起来很明显。

## 香港、东京、洛杉矶，物理距离决定下限

线路解决的是"堵不堵"，地理位置解决的是"能有多快"。这两个变量叠加，才有了选机房的取舍。

| 机房 | 大陆访问延迟区间 | 电信方向线路 | 入门月付参考 |
| --- | --- | --- | --- |
| 中国香港 | 约 20–50ms | 去程 CN2 GIA 直连香港 CTG，三网回程经香港 CTG 接 CN2 GIA | 约 $39.90 起 |
| 日本东京 | 约 50–80ms | 三网回程 CN2 GIA，联通走 9929，移动走 CMI | 约 $21.90 起 |
| 美国洛杉矶 | 约 150ms 上下 | 电信去程 GIA（AS4809），三网回程 GIA（AS4809） | 约 $10.90 起 |

延迟数字来自公开的第三方测速与整理，不同城市、不同时段会有波动，当区间看就行，别当承诺看。

这里的结论不复杂：香港最快也最贵，洛杉矶最便宜但延迟摆在那，东京卡在中间。如果你的业务是面向国内用户、对响应速度敏感，香港是首选；如果只是需要海外 IP、能接受一百多毫秒，洛杉矶的性价比明显更好。有一个场景经常被忽略——需要日本 IP（日区业务、日系平台账号、面向日本买家的独立站），又不希望大陆访问速度难看到不能用的地步，东京是唯一能同时满足这两个条件的位置。

DMIT 在三个机房都有 CN2 GIA 产品线，具体哪条线哪个机房还在售，直接看库存比较快：👉 [查看 DMIT 当前在售机房与库存](https://www.dmit.io/aff.php?aff=12046)

## 推荐的机器为什么总是 DMIT

绕不开这家，是因为它在几个具体指标上不太一样。

DMIT 是美国纽约注册的公司，主要做洛杉矶、香港、东京三地机房，持有自己的 AS（AS906）。这个细节的实际意义在于：带宽是它自己跟三大运营商签下来的，不是从上家手里转卖。线路出问题时溯源快，也不存在"上游超卖"这类没法解释的掉速。业内流传的一个侧面证据是，某些知名商家的一部分 CN2 GIA 带宽就是从 DMIT 采购的——这是第三方测评里提到的说法，可以当作参考，不必当结论。

硬件上全系 KVM 虚拟化配 AMD EPYC 处理器，磁盘 IO 在第三方 yabs 测试里能跑到 1GB/s 上下，建站、跑数据库都不至于卡在磁盘上。网络策略上有一条比较实在的规则：流量跑超后限速不停机。Pro 和 EB 系列超量后降到 4–10Mbps 继续用，T1 系列能降到 100–500Mbps。网站突然被打或者被爬，不会因为流量爆了就整站挂掉。

也有该说的缺点。香港 Pro 起步就要 $39.90/月，比洛杉矶同配置贵了近三倍，预算紧的人不用硬上。Pro 和 EB 系列长期处于缺货状态，热门配置经常要等补货。另外有第三方测评提到，DMIT 做宿主机升级维护时通知不够及时，对可用性要求写进合同的业务需要留意这一点。

## DMIT 全套餐价格对比

价格和库存随平台世代调整得比较频繁，下面按当前在售的 AS3 平台整理（AMD EPYC 7003 系列）。更早的 AN4 产品线已经下架，AN5 平台（EPYC 9005）线路和配置与 AS3 一致，CPU 性能更强、报价略高，部分套餐只在官网有货。

### 洛杉矶 Premium（三网回程 CN2 GIA）

电信用户的首选，电信去程走 GIA（AS4809），联通去程直连 AS4837，移动去程经香港移动 AS58453，三网回程统一走 GIA。默认 1 个 IPv4 + 1 个 IPv6 /64，双向计费流量。

| 套餐 | vCPU | 内存 | 存储 | 月流量 / 带宽 | 超量后 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AS3.Pro.TINY | 1 核 | 2GB | 20GB SSD | 1000GB / 1Gbps | 4Mbps 不限量 | $10.90 | [入手 TINY 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.Pocket | 2 核 | 2GB | 40GB SSD | 1500GB / 4Gbps | 4Mbps 不限量 | $16.90 | [入手 Pocket 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.STARTER | 2 核 | 2GB | 80GB SSD | 3000GB / 10Gbps | 4Mbps 不限量 | $34.90 | [入手 STARTER 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MINI | 4 核 | 4GB | 80GB SSD | 5000GB / 10Gbps | 8Mbps 不限量 | $62.90 | [入手 MINI 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MICRO | 4 核 | 4GB | 160GB SSD | 7000GB / 10Gbps | 8Mbps 不限量 | $87.90 | [入手 MICRO 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MEDIUM | 6 核 | 8GB | 160GB SSD | 14000GB / 10Gbps | 10Mbps 不限量 | $199.90 | [入手 MEDIUM 方案](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |

### 洛杉矶 Eyeball（CMIN2 / 9929 方向）

同样是三网优化，但走的是另一套组合：电信在 AS9929 与 AS58807 之间做负载分配，联通主要走 AS9929，移动主要走 AS58807。同等价格下给的流量明显更多，适合流量吃得多、线路要求略低于 GIA 的场景。

| 套餐 | vCPU | 内存 | 存储 | 月流量 / 带宽 | 超量后 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AS3.EB.TINY | 1 核 | 2GB | 20GB SSD | 1500GB / 2Gbps | 4Mbps 不限量 | $10.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.Pocket | 2 核 | 2GB | 40GB SSD | 3000GB / 4Gbps | 4Mbps 不限量 | $16.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.STARTER | 2 核 | 2GB | 80GB SSD | 5000GB / 10Gbps | 4Mbps 不限量 | $34.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MINI | 4 核 | 4GB | 80GB SSD | 10000GB / 10Gbps | 8Mbps 不限量 | $62.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MICRO | 4 核 | 4GB | 160GB SSD | 14000GB / 10Gbps | 8Mbps 不限量 | $87.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MEDIUM | 6 核 | 8GB | 160GB SSD | 30000GB / 10Gbps | 10Mbps 不限量 | $199.90 | [查看 EB 套餐与库存](https://www.dmit.io/aff.php?aff=12046) |

### 洛杉矶 Tier 1（国际 BGP，无大陆优化）

走纯国际互联，不对中国大陆方向做加速。价格是全线最低的，超量后限速的余量也更大。面向海外用户的项目、需要美国 IP 但不在意回国速度的场景，选这条。

| 套餐 | vCPU | 内存 | 存储 | 月流量 / 带宽 | 超量后 | 价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.AS3.T1.WEE | 1 核 | 1GB | 20GB SSD | 1000GB / 4Gbps | 100Mbps 不限量 | $36.90/年 | [选 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.T1.TINY | 1 核 | 1GB | 20GB SSD | 2000GB / 4Gbps | 200Mbps 不限量 | $6.90/月 | [选 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.T1.STARTER | 2 核 | 2GB | 40GB SSD | 4000GB / 10Gbps | 200Mbps 不限量 | $12.90/月 | [选 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.T1.MINI | 2 核 | 4GB | 80GB SSD | 8000GB / 10Gbps | 200Mbps 不限量 | $21.90/月 | [选 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.T1.MICRO | 4 核 | 4GB | 120GB SSD | 16000GB / 10Gbps | 500Mbps 不限量 | $32.90/月 | [选 T1 入门款](https://www.dmit.io/aff.php?aff=12046) |

### 香港 Premium（三网回程经香港 CTG 接 CN2 GIA）

线路最短，延迟最低。电信去程经 CN2 GIA 直连香港 CTG，联通去程经 AS4837、AS10099 进港，移动去程走 CMI，三网回程统一经香港 CTG 接入国内 CN2 GIA。价格也是全线最高的一档。

| 套餐 | vCPU | 内存 | 存储 | 月流量 / 带宽 | 月付价格 | 购买 |
| --- | --- | --- | --- | --- | --- | --- |
| HKG.AS3.Pro.TINY | 1 核 | 1GB | 20GB SSD | 500GB / 1Gbps | $39.90 | [查香港 Pro 库存](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.STARTER | 1 核 | 2GB | 40GB SSD | 1000GB / 1Gbps | $79.90 | [查香港 Pro 库存](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MINI | 2 核 | 2GB | 60GB SSD | 1500GB / 1Gbps | $126.90 | [查香港 Pro 库存](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MICRO | 2 核 | 4GB | 80GB SSD | 2000GB / 1Gbps | $179.90 | [查香港 Pro 库存](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MEDIUM | 4 核 | 4GB | 160GB SSD | 2500GB / 1Gbps | $239.90 | [查香港 Pro 库存](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |

### 日本东京 Premium

三网回程 CN2 GIA，联通走 AS9929 精品网，移动走 CMI，去程同样经过优化。入门款 TYO.Pro.TINY 为 1 核 / 1GB / 20GB SSD / 500GB 月流量 / 1Gbps，月付 $21.90——比香港同级便宜近一半，比洛杉矶贵一倍，延迟正好卡在两者之间。更高配置的报价 DMIT 调整过几轮，以购物车实时显示为准：👉 [查看东京 Pro 实时价格](https://www.dmit.io/aff.php?aff=12046)

东京的 Eyeball 系列已经下架，官网现在只有 Pro 和 T1 两条线。

## 按需求对号入座

**个人博客、小站、轻量代理节点，用电信宽带。** LAX.AS3.Pro.TINY，$10.90/月。1000GB 双向流量对个人站够用，1Gbps 端口，回程 GIA。这是整个推荐清单里性价比最平衡的一台。

**面向国内用户的正式业务，网站有一定并发。** 洛杉矶 Pro 的 Pocket 或 STARTER。STARTER 给了 10Gbps 端口和 3000GB 流量，$34.90/月；如果访客主要在国内一线城市、对首屏时间要求高，把这个预算挪到香港 Pro TINY 更直接，代价是流量只有 500GB。

**流量吃得多，线路要求没那么极致。** 洛杉矶 EB 系列。同样的 $34.90，STARTER 给 5000GB，比 Pro 多出 2000GB。移动用户在这条线上体验尤其好。

**需要日本 IP。** TYO.Pro.TINY，$21.90/月。想要日本 IP 又不介意大陆访问速度的场景，T1 系列也能用，年付 $36.90 起。

**主要面向海外用户。** T1 系列，年付 $36.90 的 WEE 就够，超量后降到 100Mbps 继续跑，不至于因为一次流量高峰被停机。

**不想为线路多付钱。** 说句实话，如果你的宽带是电信但只用来偶尔登录后台，不对延迟敏感，T1 就够了，不必为 GIA 买单。

## 下单前值得知道的几件事

**流量是双向计费的。** 上传加下载合并计算。跑分发、做镜像、挂大量同步任务的，先把带宽账算清楚。

**超量策略分系列。** Pro 和 EB 超量后降到 4–10Mbps 不限量；T1 能降到 100–500Mbps。看你更怕停机还是更怕变慢。

**换 IP 政策。** IP 被墙可以免费申请更换，每 15 天一次；主动要求换 IP 收 $5。对纯建站影响不大，对 IP 质量敏感的场景要提前知道这个频率限制。

**退款窗口。** 公开说明是购买 3 天内且流量使用不超过 30GB 可全额退款（扣除支付手续费），3 到 30 天按剩余时间比例退。建议先用支付宝月付跑一个周期测线路，不满意再决定要不要转年付。

**优惠码要自己验证。** DMIT 会放一些循环折扣码，但基本都绑定产品线和付款周期，月付通常享受不到。下单时在结算页填码点 Validate Code 验证是否仍有效，别信第三方整理的过期码。

**付款方式对国内用户友好。** 支持支付宝、微信支付和 PayPal，有中文客服。

## 常见问题

**CN2 GIA 和 CMIN2 该选哪个？** 看你家宽带。电信用户选 Pro（GIA），移动用户 CMIN2 的体感可能反而更顺。联通用户在 EB 系列走 9929，也合适。

**为什么同配置的机器，电信用户和联通用户评价差这么多？** 因为回程线路不同。一台机器对某一家运营商优化好，不代表对三家都好，这在任何商家身上都成立。

**洛杉矶 Pro TINY 的 1000GB 流量够用吗？** 个人博客、小型 API、中转节点基本够。跑视频或做下载站，直接看 EB 系列或者往上走配置。

**会不会买了就缺货？** 会。Pro 和 EB 属于限量产品，补货时间不固定。不急的话可以先月付，急的话看到有货就别拖。👉 [进 DMIT 官网确认今天的库存状态](https://www.dmit.io/aff.php?aff=12046)

一句话收尾：电信用户挑 VPS，先确认回程是不是 CN2 GIA，再看机房放在香港、东京还是洛杉矶——顺序反了，钱容易白花。
