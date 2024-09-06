---
description: 了解如何在 spigot 服务端上安装 Oraxen
cover: https://images.polymart.org/resource/629/default.jpg
coverY: 0
---

# 开始使用

## 什么是 Oraxen?

Oraxen 是一个 Minecraft 服务器插件,允许你在你的服务器上创建自定义贴图/模型的方块或者物品。处理资源包的构建和上传(使用 Polymath),并且完全开源,具有扩展性极强的API。

## 它是怎么工作的?

当你安装 Oraxen 插件后启动服务器,插件将会读取配置中物品,然后生成自定义贴图所需要的 json 模型文件。 并且它会将构建出来的资源包文件通过压缩算法压缩和加密后上传至 Polymath 服务器。Polymath 是一款使用 Python 语言开发的一个开源 Minecraft 资源包托管服务器。 默认情况下 Oraxen 会使用官方的 Polymath 服务器,这个服务器在瑞士。当一个玩家加入服务器的时候 Oraxen 会自动将 Polymath 服务器的资源包发送给玩家。

## 如何快速安装 Oraxen

安装 Oraxen 十分简单,只需要以下几步:

1.将 Oraxen 和 [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)  放入你的 plugins 目录

2.启动你的服务器

3.开始使用 Oraxen

{% hint style="info" %}
Oraxen has been tested with Spigot and Paper 1.18 -> 1.21
{% endhint %}
