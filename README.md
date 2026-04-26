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
![](附件/Pasted%20image%2020260426150542.png)
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

### 文章书写
文章属性中有`layout: doc`时，该文章才会展示。
在.md文档的开头加上如下格式。
```markdown
---
title: 文章标题
date: 2024-03-20
author: 作者
tags: VitePress
cover: url... 
layout: doc
---
```

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

