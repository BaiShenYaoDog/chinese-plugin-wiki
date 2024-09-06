---
description: 关于 Oraxen 的一些常见问题
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# 常见问题

## Oraxen 是一个模组吗?

不,Oraxen 并不是一个模组。这是一个插件,通过 Minecraft 资源包让你在你的服务器上实现自定义贴图/模型的方块或者物品等内容。

## Oraxen 会影响我自己的服务器资源包吗?

你可以将任何资源包合并至 Oraxen 生成的资源包当中。\
Oraxen 会自动将包含所有资源包的资源包发送给玩家。\
只需要将你的服务器资源包复制到 Oraxen/pack/assets 即可。

## 我使用了 Bungee/Velocity 怎么解决重复加载资源包的问题?

从技术角度来讲,这类代理服务端本质上是让玩家离开一个服务器并加入另一个服务器。这个时候 Minecraft 会自动卸载资源包。\
如果你想放置这种情况你可以安装 [BungeePackLayer](https://www.spigotmc.org/resources/%E2%9C%82%EF%B8%8F-bungee-pack-layer-optimize-resource-pack-sending.94978/)\
这是一个 Bungee/Velocity 插件,只要每个服务器上的资源包相同,就不会重复给玩家发送资源包。

## 我可以关闭 Oraxen 的默认内容吗?

是的,你可以在 `settings.yml` 中关闭默认内容。

{% hint style="info" %}
Required 会自动重新释放,大部分默认内容都可以被关闭。
{% endhint %}

## Oraxen 会破环原版特性吗?

Oraxen 的本质是在不丢失功能的情况下向游戏添加自定义内容,所以简短的回答肯定是否定的,但是 Minecraft 有一些限制(比如,你不能真正意义上的制作方块/装备),所以我们不得不破坏一些原版特性:\
\- 默认情况下,皮革装备会看着有所不同(尽管在背包中仍然保持相同纹理)\
\- 新增的放款将会使用原版未使用的蘑菇柄块的变体方块,这可能导致在使用这些不寻常变体方块地方或者你并排放置两个蘑菇柄块,可能就会出现贴图错误,但是你可以右键方块或者重新加入服务器来修复问题。

## 当我新增一个物品的时候,会导致其他物品的贴图错乱。

通常情况下,Oraxen 会自动为所有物品设置 CustomModelData。\
但是在一些特使情况下,你手动设置了相同的 CustomModelData 值,可能会导致贴图错乱。

{% hint style="info" %}
请不要忘记使用 /o reload all 命令重载插件,并使用 /o pack send @a 重新发送资源包(也可以重新加入服务器)
{% endhint %}

## 我的贴图只在使用 Optifine 的情况有效。

从 Minecraft 1.11 开始,贴图/模型文件的命名只能使用 小写字母、数字以及\_ 组成,但是 Optifine 支持使用其他命名,所以请使用正确的命名格式,以防止出现问题。

## 如何更新 Oraxen?

你可以观看这个视频查看教程(需要魔法): [https://youtu.be/LkansZwVaPY](https://youtu.be/LkansZwVaPY)

## 怎么不显示物品的简介?

你可以使用这个插件(可能需要魔法): [https://github.com/lolgeny/item-tooltip-remover](https://github.com/lolgeny/item-tooltip-remover)

## 我要在哪里提出新功能建议或者反馈问题?

第一种方案: 注册并登录 github 然后前往这个仓库: [git.io/oraxen](https://github.com/Th0rgal/Oraxen)

第二种方案: 加入我们的 [Discord](https://discord.com/invite/4Qk5kBT9UX),然后验证你的购买,前往 支持/请求 频道

### 我只向使用 Oraxen 的技能。

前往 settings.yml 配置文件,修改以下配置项:

```yaml
  upload:
    enabled: false
Pack:
  generation:
    generate: false
    compression: BEST_COMPRESSION
    protection: false
  dispatch:
    send_pack: false
  enable_configs_updater: false
Misc:
  reset_recipes: false
  auto_update_items: false
```

修改完后,请删除 Oraxen/pack、Oraxen/Items、Oraxen/glyphs 目录下的文件
