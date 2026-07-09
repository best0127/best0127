# GitHub Profile 页面改造设计

## 目标
将 best0127 的 GitHub Profile README 改造为动态交互风格，移除"关于我"文字段落。

## 最终布局（从上到下）

| 顺序 | 内容 | 技术方案 |
|------|------|----------|
| ① | 打字动画横幅 | `readme-typing-svg` 霓虹粉色循环打字 |
| ② | 奖杯墙 + 访问计数 | `github-profile-trophy` + `komarev.com/ghpvc` |
| ③ | 技术栈徽章 | shields.io（保留现有） |
| ④ | GitHub 统计卡片 | `github-readme-stats` x 3（保留现有） |
| ⑤ | 3D 贡献立方体 | `yoshi389111/github-profile-3d-contrib` Action |
| ⑥ | 贪吃蛇贡献动画 | `platane/snk` Action |

## 变更清单
1. **README.md**: 删除"关于我"段落，重写全部内容
2. **新增** `.github/workflows/snake.yml`: 贪吃蛇定时任务
3. **新增** `.github/workflows/profile-3d.yml`: 3D 贡献立方体定时任务

## 配色
沿用现有 Dracula 暗紫主题 + 霓虹粉点缀，保持整体一致性。
