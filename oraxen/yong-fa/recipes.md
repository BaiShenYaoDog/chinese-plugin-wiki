---
description: 如何使用 Oraxen 自定义配方
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966826759293136996/unknown.png
coverY: 0
---

# 配方

自定义配方是 Minecraft 已经官方实现的功能,允许开发者使用数据包自定义配方。工作台允许你制作装备,剑等物品,这些物品被称为有序配方(ShapedRecipes),还有无序配方(ShapelessRecipes),只需要放入正确的物品就可以合成,还有熔炉配方(FurnaceRecipes)等。Oraxen的目标是支持所有配方,但是目前就只实现了有序配方。

## 如何创建配方?

你可以在这里查看所需的命令和权限列表: [文档地址 ](commands.md#create-recipes)

### 第一步: 打开构建器菜单

首先使用: **/o recipe builder SHAPED** 这个命令,会给你打开一个工作台:

然后把配方放入左边,然后把结果放入右边的格子。

### 完了,我材料忘记拿了,我可以关闭菜单吗?

是的,你可以随便关闭菜单,再次打开只需要输入: **/o recipes open** 就可以打开历史配方设置,恢复修改。

### 我配置好了我的配方,我要怎么加载?

首先你需要注册你的配方,使用命令 **/o recipes save <配方ID>** 保存,不过可惜的是,Oraxen 并不会加载配方,你必须要重启服务器。

{% hint style="info" %}
你也可以使用命令 **/o recipes save <**配方ID**>** <权限> 来保存配方,玩家必须要拥有<权限>这个权限才可以使用这个配方
{% endhint %}

## 如何修改我的配方?

你只需要编辑对应配方的配置文件,就可以修改配方、结果、权限了。
