---
title: 1月16日笔记
date: 2025-01-16
lastMod: 2025-01-16
category: 日记
tags: [ubuntu, MCU]
---

## 上午

系统爆了

#### 症状:图形界面进不去

- 原因 尝试更换de为KDE displayServer为 wayland时包的依赖关系出现问题
- 尝试更换lib版本 直接导致X11依赖出现问题

具体问题具体分析
尝试调log无果 只知道 window server shutdown
怀疑是X11依赖原因

```shell
# 不建议用apt修复 可以用aptitute 修复依赖问题会比较灵活 后续可以试试
sudo apt --fix-broken install # 发现依赖问题，但修复失败

# 下载这两个20.04古老版本的libxkbcommon0 和 dev
wget http://launchpadlibrarian.net/463824483/libxkbcommon0_0.10.0-1_amd64.deb
wget http://launchpadlibrarian.net/463824473/libxkbcommon-dev_0.10.0-1_amd64.deb
# 本地强制覆盖 降级安装
sudo dpkg --force-overwrite libxkbcommon0_0.10.0-1_amd64.deb
sudo dpkg --force-overwrite libxkbcommon0-dev_0.10.0-1_amd64.deb

sudo apt--fix-broken install # 修复无错误
```

## 下午

- 复工 继续写上位机框架 参考接口模式
  > **TODO:**
  >
  > - 规范机器人的描述格式 (并实现ROS直接读取)
  > - DOxygen comment
- USB VPC实验
- H7 slave框架
