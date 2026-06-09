# demo_marble_view

World Labs Marble 主题的交互式宇宙探索静态演示页 — 浏览星空 → 选择主题 → 选择观测方式 → 跳转对应的 marble.worldlabs.ai VR 场景。

## 在线访问

启用 GitHub Pages(Settings → Pages → Branch: `main`)后访问:

```
https://yinmingjun.github.io/demo_marble_view/
```

## 本地预览

无构建步骤,直接用浏览器打开 `index.html` 即可。所有跳转使用相对路径,目录结构不能打乱。



## 页面流程

```
index.html                                 封面 / 进入按钮
   │
   ▼
details/entry.html                         开场视频 → 浮动文字时间线
   │
   ├─ "走近太阳"            ─► details/entry_sun.html            主题封面(百叶窗入场)
   │                              │
   │                              ▼ 点击图片
   │                          details/entry_sun_select.html      2 个选择热区
   │                              ├─ 太阳如何影响地球?   ─► marble.worldlabs.ai (新标签页)
   │                              └─ 太阳真的是静止火球? ─► marble.worldlabs.ai (新标签页)
   │
   ├─ "宇宙之眼"            ─► details/entry_cosmos.html         主题封面(百叶窗入场)
   │                              │
   │                              ▼ 点击图片
   │                          details/entry_cosmos_select.html   3 个观测方式热区
   │                              ├─ 光学      ─► marble.worldlabs.ai (新标签页)
   │                              ├─ 射电      ─► marble.worldlabs.ai (新标签页)
   │                              └─ 中微子    ─► marble.worldlabs.ai (新标签页)
   │
   └─ "火星探秘"            ─► details/entry_mars.html           主题封面(百叶窗入场)
                                  │
                                  ▼ 点击图片
                              details/entry_mars_select.html     3 个降落地点热区
                                  ├─ 日落是蓝色?    ─► marble.worldlabs.ai (新标签页)
                                  ├─ 曾经有水吗?    ─► marble.worldlabs.ai (新标签页)
                                  └─ 仍然保存着什么? ─► marble.worldlabs.ai (新标签页)
```

每个二级页面左上角有浮动 home 按钮,点击回到 `index.html`。

## 目录结构

```
.
├── index.html
├── README.md
├── .gitignore
├── details/
│   ├── entry.html               # 开场:视频 + 时间线浮动文字 + 3 个主题入口
│   ├── entry_sun.html           # 走近太阳 · 主题封面
│   ├── entry_sun_select.html    # 走近太阳 · 2 选 1(影响地球 / 静止火球)
│   ├── entry_cosmos.html        # 宇宙之眼 · 主题封面
│   ├── entry_cosmos_select.html # 宇宙之眼 · 3 选 1(光学 / 射电 / 中微子)
│   ├── entry_mars.html          # 火星探秘 · 主题封面
│   └── entry_mars_select.html   # 火星探秘 · 3 选 1(三个问题)
└── images/
    ├── entry_mov.mp4            # 开场视频
    ├── entry_mov2.mp4           # (备用,未使用)
    ├── *.png                    # 原始素材
    └── *.jpg                    # q85 压缩版本(页面实际引用)
```

## 设计与技术要点

- **纯静态**:HTML/CSS/JS,无构建、无依赖。每个页面自包含样式
- **入场动画**:`entry_cosmos.html`、`entry_mars.html` 使用 12 条横向叶片的「百叶窗」3D 翻转(`rotateX 0→90°`)波浪式揭示图片,完成后整体淡出消失
- **图片热区**:`entry_*_select.html` 用 `aspect-ratio` 容器锁住底图比例,绝对定位的 `<a class="hotspot">` 以百分比覆盖文字区域,响应式缩放下位置不偏。默认无边框,悬停加亮 + 白边 + 微光晕
- **外链行为**:跳转到 `marble.worldlabs.ai` 的热区都用 `target="_blank" rel="noopener noreferrer"`,新标签页打开,select 页保留在原标签便于继续选择
- **悬停文本**:热区用 `aria-label` 而非 `title`,屏幕阅读器可读到说明,但鼠标悬停不触发浏览器 tooltip
- **图片体积**:同名 `.png`/`.jpg` 共存,HTML 引用 `.jpg`(q85,整体省 ~67% 体积)。需要替换素材时改 `.png` 后重新生成 jpg
- **Home 浮标**:除 `index.html` 外,每页左上角固定 44×44 圆形按钮(半透明黑底 + 毛玻璃 + 白色房子 SVG),`z-index: 1000` 高于内容层
