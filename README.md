# 圣诞珍珠画02

6枚一套的圣诞珠钻画挂饰（圣诞老人、小鹿、圣诞树、雪人、圣诞袜、花环）四张轮播的批量模板：

1. 下雪开场："OK wait... this might be the cutest little Christmas craft gift ever 😭"
2. 整套6个："I really thought it was just one ornament... but the whole kit comes with 6 😭"
3. 自己做："and you make them yourself... which honestly makes them even sweeter 🥹"
4. 挂上树："we finished one... and then ended up hanging all 6 on the tree 😅" + "grab yours today 👇👇"

文案、emoji、字幕样式、产品、人物选角和负面约束固定，写在 `template/carousel.json`。脚本给每套、每张画面写一条提示词，场景、机位、景别等可变点的取值由脚本定好并在各套之间轮换，不靠模型自己挑。质感、配色、主打款、地点、桌面、套装工具每套抽一次，用到它的几张共用同一个取值：第3张正在做的和第4张最后挂上的是同一款，6款在各套之间均衡轮换。同时写出可以直接交给 [pinshuai-batch-image](https://github.com/Kangaroochan/pinshuai-batch-image) 的 `jobs.json`，一次出完全部套数。

只写提示词，不出图。本 skill 从 [圣诞珍珠画01](https://github.com/Kangaroochan/christmas-pearl-painting-01) 复制而来，脚本和规则沿用；别的参考图要做提示词多样化，用 [pinshuai-prompt-diversify](https://github.com/Kangaroochan/pinshuai-prompt-diversify)。

## 安装

克隆到 Codex 的技能目录，文件夹名保持 `圣诞珍珠画02`：

```powershell
git clone https://github.com/Kangaroochan/christmas-pearl-painting-02.git "$env:USERPROFILE\.codex\skills\圣诞珍珠画02"
```

脚本需要 Python 3，只用标准库。

## 使用

在 Codex 里调用 `$圣诞珍珠画02`，说要几套、什么深度（1～10，默认 10）。也可以直接跑：

```powershell
python scripts/make_batch.py --sets 10 --depth 10 -o D:/出图任务/圣诞02
python scripts/make_batch.py --check
```

修复画面问题时用适用于全部选项的通用手部/受力/自然排列规则，不删选项、换安全场景或限制构图；改前改后的差异统计不能降低（2026-11-01 用户要求）。用户明确说不要的画面例外，直接从模板删掉。

## 文件

- `SKILL.md`：skill 规则
- `template/carousel.json`：模板；`template/参考图/`：原始四张截图；`template/产品图/`：6款挂饰和包装盒的裁图
- `scripts/make_batch.py`：按模板生成一批；`scripts/sample_prompts.py`：抽取引擎
- `references/lessons.md`：出图经验记录

## 许可

MIT
