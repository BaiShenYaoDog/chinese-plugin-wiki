---
description: How to add new glyphs to the game?
cover: https://i.imgur.com/T76ianD.png
coverY: 0
---

# 自定义文字

## What is a glyph?

A glyph is a textured unicode symbol. It can be used in any texts (chat, item name, lore and more). They can be used to do very, very powerful things (custom inventories, extra bars) but their simplest use is to be emoji.

## How to add a Glyph?

You first need to create a png texture. For example the heart.png file contained in `default/chat`.

![heart.png](<../../../.gitbook/assets/heart (1).png>)

You can then add your section to any yaml file from the glyphs directory. The code must be different for every glyph. This is the number that corresponds to the number of the unicode character that will be used. The texture is the path and name of the texture file. Height allows you to set the displayed character scale while ascent defines the vertical shift of the displayed result.

```yaml
heart:
  texture: default/chat/heart
  ascent: 8
  height: 8
```

## My glyphs don't work?

This is likely due to misconfiguration of the glyphs' config.\
Please check your console for any errors, as it should tell you exactly which glyph is misconfigured and how it is. ![](https://user-images.githubusercontent.com/62521371/185404681-e0c1a881-e30b-446a-9f33-20dd88bae27c.png)

## Multi-Bitmap glyphs

If you have a png consisting of several emotes, you can make it a multi-bitmap.\
This means you can, tie several glyphs to one image. This step requires some extra configuration to work however.\
In fonts.yml there is a section for `bitmaps`.\
Here you need to specify an `id`, which you will use in your glyph-configs.\
You also need to specify the path to the texture, as well as how many rows and columns the bitmap has.\
Below is an example of an entry in `fonts.yml`:

```yaml
bitmaps:
  example_bitmap:
    texture: example/example_bitmap
    rows: 4
    columns: 9
    ascent: 8
    height: 8
```

![](../../../.gitbook/assets/example\_bitmap.png)

As you can see, the image shown above has 4 rows and 9 columns.\
The ascent and height property will be the one used for all glyphs tied to this bitmap.\
Now that you have your bitmap configured, you can link a glyphs to it.\
In your glyph config, you need to specify the bitmap id, as well as the row and column of the glyph you want to use.\
Below is an example of a glyph config using the bitmap above.

```yaml
example_glyph:
  texture: default/chat/example_glyph
  bitmap:
    id: example_bitmap
    row: 1
    column: 1
  #ascent: 8 # Not needed as bitmap specifies it
  #height: 8 # Not needed as bitmap specifies it
```

This will link the glyph to the first emoji on the first row in the image above.

## Emoji List

To make a glyph appear under `/oraxen emojis` you need to specify that it is one, like below.\
If not specified, this will default to `false`

```yaml
heart:
  texture: default/chat/heart
  is_emoji: true
```

It will also, by default, only show emojis the player has the permission for.\
In `settings.yml` you can toggle the `only_show_emojis_with_permission` setting.\
This will show all emojis to every player, and adds a hover-message indicating if they have permission or not. ![img](https://cdn.discordapp.com/attachments/758785982005903431/1002564595099111474/unknown.png)

## How to use it in the chat?

You need to add a chat subsection to your glyph section:

```yaml
chat:
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

The placeholders can be used in chat by players with the required permission (if permission is specified, it is not mandatory).

## How to make glyphs tabcomplete?

Simply set `tabcomplete: true` in the chat-section.\
If not specified, this will default to `false` Tabcompletion is currently only available for servers on 1.19.3 and above.

```yaml
chat:
  tabcomplete: true
  placeholders:
    - "<3"
  permission: "oraxen.emoji.heart"
```

## Do not remove shifts.yml

This file is used elsewhere in the default pack and removing it improperly will make the plugin fail to load.\
There is no real reason to delete this file. It will simply be recreated on startup.\
If you know what you are doing, changes made inside the file will not be overwritten, only if deleting the file. Same applies to `interface.yml`. They are used in for example language files, so deleting them means those fail.

### My shift glyph does not move anything?

This is commonly because the shift-glyphs are set to use a transparent image.\
For example, if you edit the null.png in `Oraxen/pack/textures/required` to be transparent.\
Shifts cannot use a transparent image, and your image used for them needs to be atleast a 1x1 pixel.\\

## PlaceholderAPI

### What's my glyph placeholder?

The section name is the glyph id. In this example the glyph id is `heart`, the placeholder is `%oraxen_glyphid%`, so in this example: `%oraxen_heart%`\
Glyph-ID is the first line in any glyphs config, it is not the texturename or the placeholder.\\

### How do I use this in Prefixes / Luckperms

To add a glyph to a luckperms prefix, commonly to display ranks, simply add `%oraxen_glyphid%` to your prefix solution of choice.\
For example, if using LuckPerms, you can use the command: `/lp group default meta setprefix %oraxen_glyphid%` and it will replace it with the glyph.\
Because most plugins only parse the placeholders one time, the %luckperms\_prefix% will not be parsed again.\
You will most likely need to get the Utils-Expansion for PlaceholderAPI aswell.\
To get this, go to [this link](https://api.extendedclip.com/media/Utils-Expansion-1.0.1.jar), and place it in your plugins/PlaceholderAPI/expansions folder.\
Then in your plugin of choice use `%utils_parse:2_luckperms_prefix%` to parse the prefix again.\
Keep in mind your chatplugin must support PlaceholderAPI for this to work.\
If this does not work for whatever reason, you can always use the raw unicode from your glyph-config's `char`-property

### How do I use a glyph in name/lore of an item?

Any glyph can be used in name and lore of your item configurations.

```
<glyph:heart>
```

Where heart is replaced by your glyph section name.
