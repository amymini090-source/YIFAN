# 张逸凡 Portfolio v2 — 数据驱动版

> 品牌营销 × 内容运营 × 终端陈列 × AI 工具

---

## 📁 项目结构

```
zhangyifan-portfolio-v2/
│
├── index.html              ← 纯容器结构，零硬编码内容
│
├── css/
│   └── style.css           ← 全部样式（含 Modal / Accordion / Carousel）
│
├── js/
│   ├── main.js             ← 光标 / 加载 / 导航 / Hero / 滚动显现
│   ├── render.js           ← 读取数据，自动生成 DOM
│   ├── modal.js            ← 作品弹窗 + Tab 切换
│   ├── carousel.js         ← 图片轮播（弹窗内）
│   └── accordion.js        ← 经历展开面板
│
├── data/                   ← ★ 唯一内容数据源，新增内容只改这里
│   ├── projects.js         ← 所有作品数据
│   └── experience.js       ← 所有工作经历数据
│
├── assets/
│   ├── images/             ← 项目截图（按文件名替换）
│   └── icons/              ← favicon 等
│
├── README.md
└── .gitignore
```

---

## ⚡ 核心升级（v1 → v2）

| 功能 | v1 | v2 |
|------|----|----|
| 内容维护方式 | 直接改 HTML | 只改 `data/` 文件 |
| 新增作品 | 复制整段 HTML | 在 `projects.js` 加一个对象 |
| 新增经历 | 复制整段 HTML | 在 `experience.js` 加一个对象 |
| 作品展示 | 悬停看简介 | 点击弹窗：轮播图 + 3个Tab |
| 经历展示 | 固定一行 | Accordion 展开：职责/成果/总结 |
| 图片降级 | 手动设置 | data-fallback 自动处理 |
| 扩展性评分 | 50分 | 90分 |

---

## 🚀 快速开始

```bash
# VS Code 安装 Live Server 插件后：
# 右键 index.html → Open with Live Server

# 或 Python：
python -m http.server 5500
```

---

## ✏️ 新增一个作品（全流程）

**第一步**：把项目截图放入 `assets/images/`，例如 `project-new.jpg`

**第二步**：打开 `data/projects.js`，在数组末尾追加：

```js
{
  id: 7,                           // 唯一 ID（递增）
  title: '新项目名称',
  subtitle: '副标题 / 地点',
  category: '类别标签',
  period: '2025.xx — 2025.xx',
  cover: 'assets/images/project-new.jpg',
  fallback: 'https://占位图URL',   // 本地图不存在时自动使用
  tags: ['标签1', '标签2'],
  wide: false,                     // true = 占 2 列
  images: [
    { src: 'assets/images/new-1.jpg', fallback: '...', caption: '图注' },
    { src: 'assets/images/new-2.jpg', fallback: '...', caption: '图注' },
  ],
  overview: '<p>项目概述...</p>',
  process:  '<p>设计过程...</p>',
  result:   '<ul><li>成果...</li></ul>',
}
```

**第三步**：刷新浏览器，卡片自动出现 ✅

---

## ✏️ 新增一段工作经历

打开 `data/experience.js`，追加：

```js
{
  id: 4,
  period: '2026.xx — 2026.xx',
  role: '职位名称',
  company: '公司/组织',
  summary: '一句话摘要（折叠状态可见）',
  tags: ['技能1', '技能2'],
  detail: {
    responsibilities: ['职责1', '职责2'],
    achievements:     ['成果1', '成果2'],
    reflection:       '个人总结文字',
  }
}
```

---

## 🌐 部署到 GitHub Pages

```bash
git init
git add .
git commit -m "feat: portfolio v2 launch"
git remote add origin https://github.com/YOUR_USERNAME/zhangyifan-portfolio.git
git branch -M main
git push -u origin main
# → GitHub 仓库 Settings → Pages → Branch: main → Save
# → https://YOUR_USERNAME.github.io/zhangyifan-portfolio
```

---

## 🖼️ 图片命名对照表

| 文件名 | 用途 |
|--------|------|
| `project-zhiwu.jpg` | 知物零售店封面 |
| `project-linyutang.jpg` | 林语堂文创店封面 |
| `project-bosch.jpg` | 博世展厅封面 |
| `project-yinfa.jpg` | 银发小院封面 |
| `project-metro.jpg` | 地铁站设计封面 |
| `project-aigc.jpg` | AIGC 系列封面 |
| `zhiwu-1.jpg` … | 弹窗轮播详图 |
| `og-cover.jpg` | 社交分享封面 1200×630 |

> 图片缺失时自动降级至 Unsplash 占位图，不影响预览。

---

## 📄 License

个人求职展示用途 · © 2025 张逸凡
