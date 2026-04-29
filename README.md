---
title: VitePress-Butterfly 主题 README
date: 2024-05-20
author: 57Darling02
layout: doc
---

# VitePress-Butterfly 主题外联知识库使用方法

**本仓库是VitePress-Butterfly 主题外联知识库的使用建议。**

推荐使用obsidian管理本仓库文章。
### obsidian配置
博客通过相对定位获取资源，因此需要
1. 指定插入附件的位置为相对位置
2. 指定插入链接(Link)的位置为相对位置
> 不要使用wiki形式！
3. 展示所有文件类型，用以显示主题配置文件`site_config.yml`
参考配置页面如图:
![](附件/Pasted%20image%2020260426190853.png)
### 博客配置
本仓库根目录下`site_config.yml`为配置文件。


修改配置文件，将网站变成你的形状😤：进行主题配置信息，更改首页背景图、网站名称、侧边栏个人信息等等。


如果需要使用自定义资源，请直接创建public文件夹。此文件夹中放置图片等资源。

例如：
```
public/image/avatar.png
public/wallpaper/1.webp
```

配置中这样引用：

```yaml
avatar: "/image/avatar.png"
background: "/wallpaper/1.webp"
```

### 写文章
```md
---
title: Hello World
date: 2026-01-01
author: Me
layout: doc
---

# Hello World
```

文章需要带 `layout: doc`才 会进入首页、归档、标签等文章流。
#### 4.2 写页面

如果希望展示自己的页面，本文也提供VUE完成自己的页面 例如[友链页面](https://vitepress.57d02.cn/FriendLink/)的效果 在知识库中的配置见[模板仓库的FriendLink文件夹](https://github.com/57Darling02/wiki_template/tree/main/FriendLink)

比如我希望xxx/FriendLink创建页面，则只需要在目标链接对应目录下完成页面：

- 写好vue页面于FriendLink/FriendLinkPage.vue
- 在FriendLink/index.md中引入，配置`layout: page`

```md
---
title: FriendLink
layout: page
---

<script setup>
import FriendLinkPage from './FriendLinkPage.vue'
</script>
<ClientOnly>
  <FriendLinkPage />
</ClientOnly>
```

然后在 `site_config.yml` 的 `menuItems` 中手动配置,告知访客入口即可。

短内容可以先使用自定义 layout，例如：

```md
---
layout: shuoshuo
date: 2026-01-01
---

今天也在认真生活。
```

这类内容当前只会被构建保留，不会影响现有文章展示；之后可以再做专门的“说说”页面。

推送知识库后，它会通知主题仓库重新部署。
#### 封面配置

::: warning
注意，封面的图片资源不可以相对引用，需要像配置文件那样，配置`public/cover.png`后使用
:::


```markdown
---
title: Hello World
date: 2026-01-01
author: Me
cover: public/cover.png 
layout: doc
---
```


#### tags
博客提供tags筛选功能，如有多个tags请用空格隔开。
tags属性不能为最后一个属性！建议把layout属性放在最后。

