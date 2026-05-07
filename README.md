# topic-trace

> 热点视频素材生成器 — 将热点话题转化为短视频创作素材

## 功能简介

topic-trace 是一个独立的 Claude Code skill，能够根据你输入的热点话题，自动生成：

- **视频号文案**：有文化底蕴和情感共鸣的完整视频稿
- **小红书适配**：优化后的标题、正文和话题标签
- **视觉素材Prompt**：可用于 Midjourney、即梦、DALL-E 等工具生成封面和配图

## 快速开始

### 安装

1. 将 `topic-trace/` 文件夹复制到 Claude Code 的 skills 目录：
   - Windows: `C:\Users\<用户名>\.claude\skills\topic-trace\`
   - macOS: `~/.claude/skills/topic-trace/`

2. 重启 Claude Code 或运行 `/skills reload`

3. 开始使用：
   ```
   /topic-trace [你的热点话题]
   ```

### 示例

**输入**：
```
/topic-trace 最近喊话齐先生的视频挺火的
```

**输出**：
- 视频号完整文案（约600字）
- 小红书适配版本
- 素材来源参考
- 封面图Prompt和配图Prompt

## 架构说明

```
topic-trace/
├── skill.md                    # 主入口
└── steps/                     # 各步骤提示词
    ├── step1_search.md         # 素材挖掘
    ├── step2_create.md         # 内容创作
    ├── step3_humanizer.md     # 去人味
    ├── step4_platform.md       # 多平台适配
    └── step5_image_prompt.md   # 视觉素材
```

### 自定义扩展

如果你想替换某个步骤：

1. **替换Step**：修改对应 `steps/stepX_xxx.md` 文件
2. **添加Step**：创建新文件，修改 `skill.md` 添加调用
3. **删除Step**：注释掉 `skill.md` 中对应的Step调用

具体操作见设计文档。

## 工作流程

1. **素材挖掘**：多源搜索旧闻、诗词、典故，交叉验证
2. **内容创作**：融合素材，创作视频号风格文案
3. **去人味**：消除AI机械化表达，更自然流畅
4. **多平台适配**：转化为小红书风格内容
5. **视觉素材**：生成封面和配图的AI图像Prompt

## 设计原则

- **零配置**：安装后直接使用
- **质量优先**：每个环节只输出最优解
- **模块化**：各步骤可独立替换

## 注意事项

- 生成内容仅供参考，使用前请自行核实素材真实性
- 封面和配图Prompt需要配合 Midjourney、即梦、DALL-E 等工具使用
- 建议根据实际平台数据调整话题标签

## 更新日志

- v1.0: 初始版本

---

*如果你觉得这个工具有用，欢迎反馈和改进建议*
