# demo_marble_view

World Labs Marble 弹珠 viewer 静态演示页。

## 在线访问

启用 GitHub Pages（Settings → Pages → Branch: `main`）后，访问：

```
https://yinmingjun.github.io/demo_marble_view/
```

## 目录结构

```
.
├── index.html              # 入口（4 个按钮导航）
├── README.md
└── details/
    ├── marble_blue.html    # 蓝色弹珠 - 嵌入 ceramic splat viewer
    ├── marble_green.html   # 绿色弹珠 - 嵌入 ceramic splat viewer
    ├── marble_orange.html  # 橙色弹珠 - 重定向到 World Labs VR
    └── marble_purple.html  # 紫色弹珠 - 重定向到 World Labs World
```

## 按钮对应

| 按钮 | 行为 |
|---|---|
| 蓝色弹珠 | 嵌入 World Labs ceramic splat viewer |
| 绿色弹珠 | 嵌入 World Labs ceramic splat viewer |
| 橙色弹珠 | 重定向到 `marble.worldlabs.ai/worldvr/<id>` |
| 紫色弹珠 | 重定向到 `marble.worldlabs.ai/world/<id>` |

## 本地预览

直接用浏览器打开 `index.html` 即可（无需服务器）。注意 `details/` 下的页面通过相对路径跳转，目录结构不能打乱。
