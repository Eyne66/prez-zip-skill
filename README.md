# prez-zip-skill
`prez-zip` 是一个在 Codex 使用的可复用汇报 HTML 生成 Skill。

你只需要专注：你想说什么、想给大家看什么图。把口头汇报稿、PDF、Word、图片和图片位置需求放进一个文件夹，调用这个 Skill，它会帮你生成极简发布会风格的 HTML 演示页。以后的汇报手拿把掐，自用款非常赞，是花了五六个小时调出来的最喜欢的风格。

## 功能亮点

- 自动读取给定文件夹里的 PDF、Word、Markdown、图片素材。
- 自动提取标题、章节、关键词、强调文字和流程结构。
- 自动压缩成适合汇报展示的短句和关键词。
- 支持首屏图、结尾图、指定位置插图。
- 输出可直接打开的 `index.html`。
- 文件夹可直接 ZIP 分享，美滋滋。

## 文件结构

```text
prez-zip-release/
├── README.md
├── prez-zip/
│   ├── SKILL.md
│   └── assets/
│       └── keynote-report-template.html
└── examples/
    └── yu-jian-report/
        ├── index.html
        ├── 底图.png
        └── 文学何为.png
```

## 安装方法

把 `prez-zip` 文件夹复制到你的 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R prez-zip ~/.codex/skills/
```

然后重启 Codex 或开启一个新会话。

## 使用方法

在新会话里直接说：

```text
使用 prez-zip skill。
读取这个文件夹并生成一个可 ZIP 分享的汇报 HTML 包：
/path/to/your/report-folder

主稿：文件夹中的 PDF 或 Word
首屏图：cover.png
结尾图：end.png，标注 xxx
风格：极简，发布会感
```

你也可以补充更具体的需求：

```text
第一页只保留日期和汇报题目。
第二页不要改。
最后插入某张图片，并标注图片名称。
删去右上角导览。
```

## 风格溯源

`examples/yu-jian-report/` 中保留了一个示例作品：于坚诗歌研究选题汇报。

这个示例展示了 `prez-zip` 的目标风格：

- 全屏分章节演示
- 极简文字
- 大字号衬线标题
- 本地图片作为首屏或结尾视觉
- 适合课堂汇报、研究展示和移动端预览

本仓库中的示例图片仅用于展示该 Skill 的网页生成风格。复用时请替换为你自己的图片和稿件。

## GitHub Pages 在线预览

如果你把这个文件夹上传到 GitHub 仓库，例如仓库名为 `prez-zip-skill`，可以这样开启示例预览：

1. 打开仓库页面。
2. 进入 `Settings`。
3. 左侧选择 `Pages`。
4. `Build and deployment` 选择 `Deploy from a branch`。
5. Branch 选择 `main`，目录选择 `/root`。
6. 保存。

示例页面地址通常是：

```text
https://你的用户名.github.io/prez-zip-skill/examples/yu-jian-report/
```

Skill 本身的安装文件在：

```text
prez-zip/
```

示例网页在：

```text
examples/yu-jian-report/index.html
```

