---
title: IPTABLES / pfctl 学习笔记
categories: Programming
cover: /img/70988770_p1.jpg
thumbnail: /img/70988770_p1.jpg
date: 2022-04-21 20:18:03
updated: 2022-04-21 23:02:12
tags:
 - Linux
 - macOS
 - WireGuard
 - networks
---


全球统考取消了；校内最终考试也改为了线上，按照老师的口径整体的难度也不会很大（exept for econ and bio qwq）。反正，总算有时间为日后大学生活做准备了。

作为一枚不专业的 ACG 爱好者，稳定的获取并观看（不一定最新的）资源的途径是必要的。同时，考虑到留学国家复杂的法律责任，我早早准备了 [Buyvm](buyvm.net) Luxembourg 无限流量出口机。

![因为付费习惯良好，都变成 premier account 叻](/img/buyvm-lu.png)

跨大西洋光缆虽然带宽充足，但是架不住双程至少 200ms 的物理极限延迟。我找到了[这篇文章](https://barrowclift.me/post/wireguard-server-on-macos)，利用 MACos 搭建本地 [WireGuard](wireguard.com) server 并组网，实现安全且私密的观影、做种体验，并让我的老旧 MB（或者 trade-in 换到的 M1 mac mini）继续发光发热～

WireGuard 利用虚拟网卡来封装并转发流量，我们需要配置路由来保证合适的公网出口及流量转发规则。在 Linux 中，这些功能可以由 `IPTABLES` 实现，而在 macOS (FreeBSD) 中，则由 `pfctl` 达成。

<!--more-->

（先写个 intro 吧还是要复习背诵 ex+++ 的科目的咕咕咕咕咕）

## 参考资料

- https://barrowclift.me/post/wireguard-server-on-macos
- https://murusfirewall.com/Documentation/OS%20X%20PF%20Manual.pdf
- https://linux.die.net/man/8/iptables

## 封面来源
- 阿蟬 - log https://pixiv.net/i/70988770 