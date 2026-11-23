---
name: logo-svg
description: >-
  Designs bold, premium hand-written SVG logos (product-icon or identity mark).
  Use when the user asks for a logo, 标志, 商标, 品牌标, SVG logo, app icon,
  favicon, 小程序图标, 角标, or says /logo-svg — including bakery, coffee,
  breakfast, cafe, and other brand marks. Prefer this over GenerateImage for
  vector logos. Triggers on Chinese or English logo requests.
---

# Logo SVG · 大胆 · 高级 · 真矢量

Skill 根目录：`~/.cursor/skills/logo-svg`。用用户的语言。短说明、真文件、清晰选型。

**默认目标：大胆高级好看。** 单调、安全、考卷几何 = 失败。  
不依赖 `GenerateImage`。好看来自：**敢想的剪影** + 色/比例自信 + 读图改 path。

## 审美硬杠（比模式更先）

交稿前每案必须通过：

1. **一眼记忆点**：眯眼 2 秒仍记得的一个特征（缺口、斜切、负形、穿插、极端比例…）
2. **对称可用**：轴对称、中心对称都允许，很多高级标就是稳的对称；险在记忆点与比例，不在强行歪掉
3. **比例大胆**：极厚字重 / 极细长 / 大留白吃掉画布 / 图形顶满边缘——选一种做满，别温吞
4. **高级 ≠ 装饰**：禁止靠渐变、阴影、描边光晕、玻璃、纹理救命；高级来自剪影与间距
5. **三案形要不同**：禁止三案同一套「圆角砖 + 居中通用符号」只改色；普通缺口圆、厚弧+偏置圆核、斜条挖洞、三层胶囊、无诡计切一刀字母仍默认禁用（除非 twist 极强）

**自测一句：**「换成别的行业名字，这形还成立吗？」若只靠「滴=咖啡」硬凑，重做。

### 禁止的「单调 SVG 口音」

| 烂口音 | 改成 |
|---|---|
| 圆角方 + 居中通用符号（无 twist） | 符号与容器发生关系，或换策略 |
| 对称但空洞 | 对称留下，把记忆点做绝（更大负形 / 更重块面） |
| 细线描边插画 | 实心大块面，少 stroke |
| 说明性小零件堆砌 | 一个想法做到过瘾 |
| 奶油底黑标审一切 | product-icon 用品牌色；展示用深色底 |

细节与范例见 [reference.md](reference.md)。

## 模式

| 模式 | 何时 | 大胆高级怎么落 |
|---|---|---|
| **product-icon** | 小程序/H5/App/角标；要燥点那种完成感 | 抢眼主色 + 情绪/字母**做绝**；砖可异形；24px 仍辨认 |
| **identity** | 店招/VI/单色印刷 | 黑剪影本身够狠；上色是后话 |

自动判定：UI/小程序/派对/潮 → product-icon；店招/商标/黑白 → identity。都像则两模式可混出（一彩色角标 + 一黑稿）。

### 燥点公式（product-icon 基线，但要更大胆）

色砖 + 一个记忆点 + 1～2 色。**不要停在「可爱小脸」复刻**——同一公式可做成：斜切开的砖、半截字母冲出砖外、负形咬掉四分之一。

## 硬规则

1. 禁止 `GenerateImage` / 文生图当方案或终稿（有图仅当用户自带参考）。
2. 主交付 `.svg`；渲染图只自检。
3. 禁止自动描图碎 path 当完成稿。
4. 精做 **2～3** 案；剪影必须明显不同；覆盖 ≥2 种构造策略。
5. 一案一个想法；不画说明书。

## 工作流

```
- [ ] 1. Brief + 选模式；定 1 个主色（product-icon）
- [ ] 2. 写 8～12 概念句（强制换隐喻）→ 删掉说明书式 literal（炉口/拱顶/通用滴）→ 留 2～3 个最险且清晰的；对称可以留
- [ ] 3. 先用中文写「剪影怎么狠」（不对称点、比例、唯一记忆点）再写 SVG
- [ ] 4. 渲染 → Read 真看 → 专治单调：加锋利、减零件、推比例（≥1 轮）
- [ ] 5. Checkpoint：短文案 + **Metaphor Exploration Spec** HTML 选型页 → 等选型
- [ ] 6. 打磨；写入 assets 若用户要
- [ ] 7. （可选）终稿 kit——**只放 final，不放 A/B/C**  
      默认：**Brand Identity Spec** 一页（规范壳 + 色卡字标 + FIG 袋/杯套/手机/网站）+ 定稿 SVG；禁止文生图烤 logo。  
      详见下方「终稿 kit 约定」。
```


### 终稿 kit 约定（`final/index.html` · Brand Identity Spec）

默认做成**品牌规范书 / 建筑制图感**一页，不要普通作品集圆角卡片墙。参考定稿：`logo-svg-bakery/final/index.html`。

**页面壳**
- 深底 `#0A0A0A` + 极淡网格底纹；外框 `.spec-shell`：**直角** + `1px` 细分割线（`border-radius: 0`）。
- 字体：展示用衬线（如 Fraunces）+ UI 无衬线（如 DM Sans）+ **等宽标注**（如 JetBrains Mono）做 FIG / HEX / 章节号。
- 顶栏：色点 + 品牌名｜`BRAND IDENTITY SYSTEM`｜`REV · FINAL KIT`。
- **不要**放「HTML/CSS 仿真…」「任意 agent…」「APPLICATIONS · CSS + SVG」这类说明句。

**01 / PRIMARY MARK（左栏）**
- 主标居中，外包虚线框 + 四角准星。
- 底栏 `SCALE TEST`：32 / 24 / 16 px 真阶梯 + 字号标注。

**02 / PALETTE & TYPE（右栏）**
- 色卡条：色块底 + 英文色名 + HEX（至少主色砖 + 墨/奶油；可加强调色）。
- 字标：Display 字体名 + UI 字体名，等宽小标签。

**03 / BRAND APPLICATIONS（2×2 十字网格）**
- 四格直角拼接（中缝细线），每格底栏 `.cap-bar`：`FIG 0N — 名称` + 品类（PACKAGING / BEVERAGE / IOS DIGITAL / WEB STOREFRONT）。
- mockup 内少写行业文案；网站 hero 用居中标 + 字标即可。
- **袋：** 在 HTML 里**内联** ¾ 纸袋 SVG 代码（侧褶 + 扁提手；源稿见 skill `assets/blank-bag.svg`，复制进页面时把 gradient/filter `id` 加 `bag-` 前缀防冲突）+ 正面绝对定位叠定稿 logo；约 `left:52.5%; top:56%`。禁止 `<img src="…袋图">` 照片底；禁止文生图烤袋。
- **杯套：** CSS 杯体 + 腰封嵌标。
- **手机：** 正面整机；主屏只放定稿 app icon（iOS 圆角壳 + 轻高光）；无幽灵图标；无 Dock 塞标（Dock 可省略）。
- **网站：** 顶栏 Mac 红绿灯 `#ff5f57` / `#febc2e` / `#28c840`；地址栏可有域名占位。

### 概念策略（逼出大胆）

每案选自不同策略，勿三案同策略：

| 策略 | 做法 |
|---|---|
| 撞击 | 两形咬合/穿插，交界即记忆点（可对称） |
| 稳衡 | 轴对称但比例极端：超重、超空、顶满 |
| 负形优先 | 先画「空」再画实，空比实更重要 |
| 字母极端化 | 字重夸张或结构极端，仍可读 |
| 容器关系 | 异形容器，或符号咬边/冲出；斜切可选不强制 |

### 构造速记

- **product-icon：** `24`/`32` viewBox；主色实底；墨色图形；可少量粗 stroke（≥2 on 32）
- **identity：** `256` viewBox；实心黑；`evenodd` 负形；少锚点
- 共通：整数坐标；光学重心略上；小尺寸测试 24/32

## Checkpoint（选型页 · Metaphor Exploration Spec）

聊天里仍用短 checkpoint 文案等用户选型；**同时**输出 HTML 选型页（同轮或同目录 `index.html`），版式对齐制图规范壳。参考：`logo-svg-bakery/bold-v2/index.html`。

```markdown
**Mode:** product-icon | identity
**Bold bet:** <一案一句：这案的险在哪>

### A — … ← recommended
**Idea:** …
**Why:** …
**Risk:** <若太险，诚实说>

### B / C — …

**Next:** 选方向。要 kit / 写入项目再说。
```

### 选型页 HTML 约定

- 深底 `#0A0A0A` + 淡网格；外框 `.spec-shell`：**直角** + `1px` 细线；Fraunces + DM Sans + **JetBrains Mono**。
- 顶栏：色点 + 品牌名｜`METAPHOR EXPLORATION`｜`ROUND · BOLD Vx`。
- 导语区：左 `01 / CONCEPT DIRECTIONS` + 大标题；右一句设计目标（≤2 行）。
- **三栏直角网格**（`DIR 01/02/03`）：每栏 = 编号条 → 虚线准星框内主标 → `32/24/16` 缩放标尺 → 底栏英文名 + ≤35 字中文形描述。
- 推荐案加 `.concept-featured` + 角标 `SELECTED`（焦糖色准星）；其余标 `OPTION`。
- **不要**圆角卡片堆、不要第四案填充、不要长文案说明页。

**选型页 vs 终稿：** 选型只比剪影与小尺寸；应用 mockup 仅在选型后的 `final/`（Brand Identity Spec）。

## 红旗（有则重做）

- 用户一看就说「单调 / 模板 / AI 味几何」
- 三案同构；只有色差没有形差
- 靠渐变阴影装高级
- 24px 糊掉或记忆点消失

## 诚实边界

- 不保证商标；矢量没有生图氛围噪点——**用形的胆量补**，不装材质
- 没渲染别谎称看过小尺寸
