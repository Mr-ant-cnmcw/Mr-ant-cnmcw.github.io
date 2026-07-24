---
title: Markdown 扩展功能
published: 1970-01-01
updated: 1970-01-01
description: "了解 Firefly 中的 Markdown 功能"
tags: [演示, 示例, Markdown, Firefly]
category: "文章示例"
slug: markdown-extended
draft: true
---

## GitHub 仓库卡片

您可以添加链接到 GitHub 仓库的动态卡片，在页面加载时，仓库信息会从 GitHub API 获取。

::github{repo="CuteLeaf/Firefly"}

使用代码 `::github{repo="CuteLeaf/Firefly"}` 创建 GitHub 仓库卡片。

```markdown
::github{repo="CuteLeaf/Firefly"}
```

## 提醒框(Admonitions)配置

Firefly 采用了 [rehype-callouts](https://github.com/lin-stephanie/rehype-callouts) 插件，支持了四种风格的提醒框主题：`GitHub`、`Obsidian`、`VitePress` 和 `Docusaurus`。您可以在 `src/config/siteConfig.ts` 中进行配置：

```typescript
// src/config/siteConfig.ts
export const siteConfig: SiteConfig = {
  // ...
  rehypeCallouts: {
    // 选项: "github" | "obsidian" | "vitepress" | "docusaurus"
    theme: "github",
  },
  // ...
};
```

注意：**更改配置后需要重启开发服务器才能生效。**

以下是各个主题支持的类型列表，每个主题风格和语法不同，可根据喜好选择。

### 1. GitHub 主题风格

这是 GitHub 官方支持的 5 种基本类型。

![GitHub](./images/github.avif)

**基本语法**

```markdown
> [!NOTE] NOTE
> 突出显示用户应该考虑的信息。

> [!TIP] TIP
> 可选信息，帮助用户更成功。

> [!IMPORTANT] IMPORTANT
> 用户成功所必需的关键信息。

> [!WARNING] WARNING
> 关键内容，需要立即注意。

> [!CAUTION] CAUTION
> 行动的负面潜在后果。

> [!NOTE] 自定义标题
> 这是一个带有自定义标题的示例。
```

---

### 2. Obsidian 主题风格

[Obsidian](https://obsidian.md/) 风格支持非常丰富的类型和别名。

<details>
<summary>点击展开 Obsidian 语法列表</summary>

```markdown

> [!NOTE] NOTE
> 通用的笔记块。

> [!ABSTRACT] ABSTRACT
> 文章的摘要。

> [!SUMMARY] SUMMARY
> 文章的总结（同 Abstract）。

> [!TLDR] TLDR
> 太长不看（同 Abstract）。

> [!INFO] INFO
> 提供额外信息。

> [!TODO] TODO
> 需要完成的事项。

> [!TIP] TIP
> 实用技巧或提示。

> [!HINT] HINT
> 暗示（同 Tip）。

> [!IMPORTANT] IMPORTANT
> 重要信息（Obsidian 风格通常使用类似的图标）。

> [!SUCCESS] SUCCESS
> 操作成功。

> [!CHECK] CHECK
> 检查通过（同 Success）。

> [!DONE] DONE
> 已完成（同 Success）。

> [!QUESTION] QUESTION
> 提出问题。

> [!HELP] HELP
> 寻求帮助（同 Question）。

> [!FAQ] FAQ
> 常见问题（同 Question）。

> [!WARNING] WARNING
> 警告信息。

> [!CAUTION] CAUTION
> 注意事项（同 Warning）。

> [!ATTENTION] ATTENTION
> 引起注意（同 Warning）。

> [!FAILURE] FAILURE
> 操作失败。

> [!FAIL] FAIL
> 失败（同 Failure）。

> [!MISSING] MISSING
> 缺失内容（同 Failure）。

> [!DANGER] DANGER
> 危险操作警告。

> [!ERROR] ERROR
> 错误信息（同 Danger）。

> [!BUG] BUG
> 报告软件缺陷。

> [!EXAMPLE] EXAMPLE
> 展示一个例子。

> [!QUOTE] QUOTE
> 引用一段话。

> [!CITE] CITE
> 引证（同 Quote）。

> [!NOTE] 自定义标题
> 这是一个带有自定义标题的示例。
```
</details>

![Obsidian](./images/obsidian.avif)

---

### 3. VitePress 主题风格

[VitePress](https://vitepress.dev/) 风格提供了一套现代化的、扁平的默认样式。目前仅包含与 GitHub 一致的 **5 种** 基础类型。

<details>
<summary>点击展开 VitePress 语法列表</summary>

```markdown
> [!NOTE] NOTE
> 对应 GitHub 的 Note。

> [!TIP] TIP
> 对应 GitHub 的 Tip。

> [!IMPORTANT] IMPORTANT
> 对应 GitHub 的 Important。

> [!WARNING] WARNING
> 对应 GitHub 的 Warning。

> [!CAUTION] CAUTION
> 对应 GitHub 的 Caution。

> [!TIP] 自定义标题
> VitePress 风格同样支持自定义标题。
```
</details>

![VitePress](./images/vitepress.avif)

---

### 4. Docusaurus 主题风格

[Docusaurus](https://docusaurus.io/docs/markdown-features/admonitions) 风格提供了一套现代化的提醒框样式，支持 5 种类型。

<details>
<summary>点击展开 Docusaurus 语法列表 </summary>

支持以下类型的提醒框：`note` `tip` `info` `warning` `danger`

```markdown
:::note
突出显示用户应该考虑的信息，即使在快速浏览时也是如此。
:::

:::tip
可选信息，帮助用户更成功。
:::

:::info
一般信息。
:::

:::warning
由于潜在风险需要用户立即注意的关键内容。
:::

:::danger
行动的负面潜在后果。
:::

:::tip[自定义标题]
可选信息，帮助用户更成功。
:::
```

</details>

![Docusaurus](./images/docusaurus.avif)


## Markdown 中 Mermaid 图表完整指南

本段演示如何在 Markdown 文档中使用 Mermaid 创建各种复杂图表，包括流程图、时序图、ER 图、类图、状态图、XY 图、甘特图、思维导图等。

> Mermaid 图表由 [Merman](https://github.com/Latias94/merman) 实现。Firefly 在 Astro 构建阶段生成亮色和深色两套静态 SVG，无需在浏览器中加载 Mermaid 渲染运行时。可以前往 [Merman Playground](http://frankorz.com/merman/) 实时编辑语法并预览渲染结果。

### 流程图示例

流程图非常适合表示流程或算法步骤。




```mermaid
graph TD
    A[开始] --> B{条件检查}
    B -->|是| C[处理步骤 1]
    B -->|否| D[处理步骤 2]
    C --> E[子过程]
    D --> E
    subgraph E [子过程详情]
        E1[子步骤 1] --> E2[子步骤 2]
        E2 --> E3[子步骤 3]
    end
    E --> F{另一个决策}
    F -->|选项 1| G[结果 1]
    F -->|选项 2| H[结果 2]
    F -->|选项 3| I[结果 3]
    G --> J[结束]
    H --> J
    I --> J
```

### 时序图示例

时序图显示对象之间随时间的交互。

```mermaid
sequenceDiagram
    participant User as 用户
    participant WebApp as 网页应用
    participant Server as 服务器
    participant Database as 数据库

    User->>WebApp: 提交登录请求
    WebApp->>Server: 发送认证请求
    Server->>Database: 查询用户凭据
    Database-->>Server: 返回用户数据
    Server-->>WebApp: 返回认证结果
    
    alt 认证成功
        WebApp->>User: 显示欢迎页面
        WebApp->>Server: 请求用户数据
        Server->>Database: 获取用户偏好
        Database-->>Server: 返回偏好设置
        Server-->>WebApp: 返回用户数据
        WebApp->>User: 加载个性化界面
    else 认证失败
        WebApp->>User: 显示错误消息
        WebApp->>User: 提示重新输入
    end
```

### ER 图示例

ER 图（实体关系图）非常适合表示数据库结构。

```mermaid
erDiagram
    USER {
        int id PK
        string username
        string email
        datetime created_at
    }
    ARTICLE {
        int id PK
        string title
        text content
        datetime published
        int author_id FK
    }
    COMMENT {
        int id PK
        text content
        datetime created_at
        int user_id FK
        int article_id FK
    }
    CATEGORY {
        int id PK
        string name
        string description
    }
    USER ||--o{ ARTICLE : "writes"
    USER ||--o{ COMMENT : "posts"
    ARTICLE ||--o{ COMMENT : "has"
    ARTICLE }o--o{ CATEGORY : "belongs to"
```

### 类图示例

类图显示系统的静态结构，包括类、属性、方法及其关系。

```mermaid
classDiagram
    class User {
        +String username
        +String password
        +String email
        +Boolean active
        +login()
        +logout()
        +updateProfile()
    }
    
    class Article {
        +String title
        +String content
        +Date publishDate
        +Boolean published
        +publish()
        +edit()
        +delete()
    }
    
    class Comment {
        +String content
        +Date commentDate
        +addComment()
        +deleteComment()
    }
    
    class Category {
        +String name
        +String description
        +addArticle()
        +removeArticle()
    }
    
    User "1" -- "*" Article : 写作
    User "1" -- "*" Comment : 发表
    Article "1" -- "*" Comment : 拥有
    Article "1" -- "*" Category : 属于
```

### 状态图示例

状态图显示对象在其生命周期中经历的状态序列。

```mermaid
stateDiagram-v2
    [*] --> 草稿
    
    草稿 --> 审核中 : 提交
    审核中 --> 草稿 : 拒绝
    审核中 --> 已批准 : 批准
    已批准 --> 已发布 : 发布
    已发布 --> 已归档 : 归档
    已发布 --> 草稿 : 撤回
    
    state 已发布 {
        [*] --> 活跃
        活跃 --> 隐藏 : 临时隐藏
        隐藏 --> 活跃 : 恢复
        活跃 --> [*]
        隐藏 --> [*]
    }
    
    已归档 --> [*]
```

### XY 图示例

XY 图表非常适合展示趋势和对比数据。

```mermaid
xychart-beta
    title "月度访问量趋势"
    x-axis [1月, 2月, 3月, 4月, 5月, 6月]
    y-axis "访问量" 0 --> 5000
    bar [2500, 3200, 4100, 3800, 4500, 4800]
    line [2500, 3200, 4100, 3800, 4500, 4800]
```

### 饼图示例

饼图适合直观展示各部分在整体中的占比。

```mermaid
pie showData
    title 内容类型占比
    "技术文章" : 45
    "项目记录" : 30
    "生活随笔" : 15
    "其他" : 10
```

### 甘特图示例

甘特图可以按时间轴展示项目阶段、任务依赖和当前进度。

```mermaid
gantt
    title 博客版本发布计划
    dateFormat YYYY-MM-DD
    axisFormat %m/%d
    section 准备
    需求整理 :done, req, 2026-07-01, 3d
    视觉设计 :done, design, after req, 4d
    section 开发
    功能实现 :active, dev, after design, 7d
    内容迁移 :content, after design, 5d
    section 发布
    构建检查 :test, after dev, 2d
    正式上线 :milestone, release, after test, 0d
```

### 思维导图示例

思维导图适合梳理主题层级和知识结构。

```mermaid
mindmap
  root((Firefly))
    内容
      技术文章
      生活记录
    体验
      搜索
      深色模式
      图表
    工程
      Astro
      Svelte
      Merman
```

### 时间线示例

时间线用于按年份或阶段呈现项目的重要事件。

```mermaid
timeline
    title Firefly 演进时间线
    2024 : 建立博客
         : 完成基础主题
    2025 : 加入搜索与图库
         : 完善内容系统
    2026 : 升级 Astro 7
         : 使用 Merman 渲染图表
```

### 用户旅程图示例

用户旅程图能够描述用户在不同阶段的行为和体验评分。

```mermaid
journey
    title 读者浏览文章的旅程
    section 发现内容
      打开首页: 5: 读者
      搜索主题: 4: 读者
    section 阅读文章
      浏览正文: 5: 读者
      查看图表: 5: 读者
    section 继续探索
      查看相关文章: 4: 读者
      分享文章: 3: 读者
```

### Git 图示例

Git 图可以清晰展示分支、提交和合并历史。

```mermaid
gitGraph
    commit id: "init"
    branch feature
    checkout feature
    commit id: "add-diagrams"
    commit id: "polish-themes"
    checkout main
    merge feature id: "merge-feature"
    commit id: "release"
```

### 看板示例

看板适合展示任务在不同工作阶段之间的分布。

```mermaid
kanban
  todo[待办]
    task1[整理需求]
    task2[准备示例]
  doing[进行中]
    task3[接入 Merman]
  done[已完成]
    task4[服务端渲染]
    task5[亮暗主题]
```

### Sankey 图示例

Sankey 图通过连线宽度展示流量在不同节点之间的流向。

```mermaid
sankey-beta
Home,Post list,1200
Home,Search,450
Post list,Post detail,900
Search,Post detail,320
Post detail,Related posts,260
Post detail,External shares,180
```

### 总结

Mermaid 是在 Markdown 文档中创建各种类型图表的强大工具。本文演示了流程图、时序图、ER 图、类图、状态图、XY 图、饼图、甘特图、思维导图、时间线、用户旅程图、Git 图、看板和 Sankey 图。这些图表可以帮助您更清晰地表达复杂的概念、流程和数据结构。

要使用 Mermaid，只需在代码块中指定 mermaid 语言，并使用简洁的文本语法描述图表。图表会在构建时自动渲染为 SVG，无需客户端 JavaScript 加载。

可以前往 [Merman Playground](http://frankorz.com/merman/) 尝试更多语法，再将图表代码粘贴到文章中。



## Markdown 中 PlantUML 图表指南

PlantUML 是一种使用纯文本描述图表的工具。你只需要写一段结构化语法，就可以生成时序图、类图、用例图、活动图等常见工程图。

它特别适合写在技术博客和项目文档里：

- 图表和正文一起版本管理，便于协作与审阅
- 修改图只需要改文本，适合频繁迭代
- 能和 Markdown 无缝结合，保持文档统一

在 Firefly 中，`plantuml` 代码块会在构建阶段编码并生成服务器 SVG 地址，页面端再根据亮暗主题自动切换图源，并支持缩放、拖拽和全屏交互。

如果你想快速上手，可以记住这个最小模板：

```plantuml
@startuml
Alice -> Bob: Hello
Bob --> Alice: Hi
@enduml
```

### 活动图示例

```plantuml
@startuml
start
:用户提交订单;
if (库存充足?) then (是)
	:冻结库存;
	:创建支付单;
	if (支付成功?) then (是)
		:生成发货单;
		:通知仓库拣货;
	else (否)
		:取消订单;
		:释放库存;
	endif
else (否)
	:提示缺货;
endif
stop
@enduml
```

### 状态图示例

```plantuml
@startuml
[*] --> 草稿

草稿 --> 待审核 : 提交
待审核 --> 草稿 : 驳回
待审核 --> 已发布 : 审核通过
已发布 --> 已归档 : 到期归档
已发布 --> 草稿 : 撤回修改

state 已发布 {
	[*] --> 可见
	可见 --> 隐藏 : 手动隐藏
	隐藏 --> 可见 : 恢复展示
}

已归档 --> [*]
@enduml
```

### 用例图示例

```plantuml
@startuml
left to right direction
actor 游客
actor 用户
actor 管理员

rectangle 博客系统 {
	usecase "浏览文章" as UC1
	usecase "搜索内容" as UC2
	usecase "发表评论" as UC3
	usecase "点赞收藏" as UC4
	usecase "审核评论" as UC5
	usecase "发布文章" as UC6
}

游客 --> UC1
游客 --> UC2
用户 --> UC1
用户 --> UC2
用户 --> UC3
用户 --> UC4
管理员 --> UC5
管理员 --> UC6
@enduml
```

### 组件图示例

```plantuml
@startuml
package "Firefly Site" {
	[Astro App] as App
	[Markdown Parser] as Parser
	[PlantUML Encoder] as Encoder
	[Theme Switcher] as Theme
	[Search Indexer] as Search
}

cloud "PlantUML Server" as PU
database "Content Store" as Content

App --> Parser : parse markdown
Parser --> Encoder : encode plantuml blocks
Encoder --> PU : request svg
App --> Theme : switch dark/light src
App --> Search : build page index
Parser --> Content : read posts
@enduml
```

### 部署图示例

```plantuml
@startuml
node "User Device" {
	artifact "Browser"
}

node "CDN / Edge" {
	artifact "Static Assets"
}

node "Cloudflare Worker" {
	artifact "SSR Handler"
}

node "PlantUML Service" {
	artifact "SVG Renderer"
}

database "Object Storage" {
	artifact "Markdown Content"
}

"Browser" --> "Static Assets" : GET js/css/img
"Browser" --> "SSR Handler" : request page
"SSR Handler" --> "Markdown Content" : read post
"Browser" --> "SVG Renderer" : fetch diagram svg
@enduml
```

### ER 图示例

```plantuml
@startuml
entity User {
	*id : uuid <<PK>>
	--
	username : varchar
	email : varchar
	created_at : datetime
}

entity Post {
	*id : uuid <<PK>>
	--
	author_id : uuid <<FK>>
	title : varchar
	content : text
	published_at : datetime
}

entity Comment {
	*id : uuid <<PK>>
	--
	post_id : uuid <<FK>>
	user_id : uuid <<FK>>
	body : text
	created_at : datetime
}

User ||--o{ Post : writes
User ||--o{ Comment : creates
Post ||--o{ Comment : has
@enduml
```

### 时序图示例（登录与刷新令牌）

```plantuml
@startuml
autonumber
actor User as 用户
participant Web as 前端页面
participant API as 网关接口
participant Auth as 认证服务
database Redis as 会话缓存

用户 -> 前端页面 : 输入账号密码并提交
前端页面 -> 网关接口 : POST /login
网关接口 -> 认证服务 : 校验凭据
认证服务 -> 会话缓存 : 写入 refresh_token
认证服务 --> 网关接口 : access_token + refresh_token
网关接口 --> 前端页面 : 200 登录成功

... access_token 过期 ...

前端页面 -> 网关接口 : POST /refresh
网关接口 -> 认证服务 : 校验 refresh_token
认证服务 -> 会话缓存 : 轮换 refresh_token
认证服务 --> 网关接口 : 新 access_token
网关接口 --> 前端页面 : 200 新令牌
@enduml
```

### C4 风格容器图示例

```plantuml
@startuml
!includeurl https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Person(user, "博客访客", "阅读文章与搜索内容")

System_Boundary(system, "Firefly Blog") {
	Container(web, "Web App", "Astro + Svelte", "渲染页面与交互")
	Container(worker, "SSR Worker", "Cloudflare Workers", "处理服务端渲染请求")
	ContainerDb(content, "Content Store", "Markdown / Object Storage", "存储文章与资源元数据")
	Container(search, "Search Index", "Pagefind", "提供全文检索")
}

System_Ext(plantuml, "PlantUML Server", "生成 SVG 图表")

Rel(user, web, "访问", "HTTPS")
Rel(web, worker, "请求 SSR 页面", "HTTPS")
Rel(worker, content, "读取文章")
Rel(web, search, "查询关键词")
Rel(web, plantuml, "请求图表 SVG")

LAYOUT_LEFT_RIGHT()
@enduml
```






---

## 剧透

您可以为文本添加剧透。文本也支持 **Markdown** 语法。

内容 :spoiler[被隐藏了 **哈哈**]！

```markdown
内容 :spoiler[被隐藏了 **哈哈**]！
```

## 图片画廊网格 (Image Grid)

您可以使用 `[grid]` 和 `[/grid]` 标签将多张图片纵向并排展示。这对于展示照片画廊或对比图非常有用。系统会自动根据包裹在其中的图片数量（最多支持并排展示4张）以响应式网格进行布局。

**自动补齐图片高度：** 同一排中如果有高度、大小或者比例不一的图片，会像「九宫格画廊相册」一样自动撑满。较短或不协调的图片会自动使用 object-cover 进行完美中心裁剪补充视野。图片边框水平彻底对齐无缝隙，但被裁剪后，只有点击图片通过灯箱才能查看完整图片，所以建议尽量避免使用长宽比例不一致的图片在同一排中。

**图注恒定底端对齐：** 不论上面的图片长宽如何变化，在同一行的所有图像解释文字（图注）都会对标到一条完美的水平基线上了。

[grid]
![示例图片一](./images/firefly1.avif)
![示例图片二](./images/firefly2.avif)
![示例图片二](./images/firefly3.avif)
[/grid]

**基本语法**

```markdown
[grid]
![示例图片一](./images/firefly1.avif)
![示例图片二](./images/firefly2.avif)
![示例图片二](./images/firefly3.avif)
[/grid]
```


---