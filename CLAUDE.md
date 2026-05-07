# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

topic-trace is a Claude Code skill that transforms hot topics into short video content materials. It generates:
- Video script (video account style)
- Xiaohongshu (Little Red Book) adapted version
- AI image prompts for cover and配图

## Architecture

This is a **skill plugin**, not a code project. No build/test commands needed.

```
topic-trace/
├── skill.md              # Main entry point - invokes the 5-step pipeline
└── steps/               # Step-by-step prompts
    ├── step1_search.md      # Step 1: Material mining (WebSearch)
    ├── step2_create.md      # Step 2: Content creation
    ├── step3_humanizer.md   # Step 3: Remove AI flavor
    ├── step4_platform.md    # Step 4: Multi-platform adaptation
    └── step5_image_prompt.md # Step 5: Visual prompts
```

## Pipeline Flow

Each step reads previous step's output and produces input for the next step:

1. **Step 1** (search): User热点话题 → WebSearch → 素材清单
2. **Step 2** (create): 素材清单 + 热点话题 → 视频号文案
3. **Step 3** (humanizer): AI文案 → 去人味文案
4. **Step 4** (platform): 去人味文案 → 小红书适配版
5. **Step 5** (image): 文案 → 封面prompt + 配图prompt

Final output structure is defined in README.md.

## Extending

- **Replace a step**: Edit the corresponding `steps/stepX_xxx.md` file
- **Add a step**: Create new file, update `skill.md` to call it
- **Change output format**: Modify the final markdown structure in README.md
