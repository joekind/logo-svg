# Logo SVG — Craft & Anti-patterns

Read when building or refining paths. Keep `SKILL.md` workflow first.

## 大胆高级（形，不是材质）

高级感检查清单：

- [ ] 剪影在 24px 仍是「一个字能说清的形」
- [ ] 有一处故意过头：更厚 / 更斜 / 更空 / 更尖
- [ ] 去掉行业 literal 后仍像有主见的标
- [ ] 深色底上不发灰、不碎、不像缺零件的线稿
- [ ] 与另外两案并排：形差大于色差

推比例时问：若把字重或负形再推 20%，会不会更像品牌？会 → 推。

单调急救：

1. 砍零件到只剩记忆点  
2. 推比例：更厚 / 更空 / 顶满（对称也可以很狠）  
3. 容器改异形，或让图形咬边/冲出  
4. 换策略表（撞击 / 稳衡 / 负形 / 字母极端 / 容器关系）  

对称不是问题；没有记忆点才是问题。

## Product-icon mode（燥点同款 · 更大胆）

Canonical baseline — 燥点派对 nav mark（公式，不是天花板）:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" fill="none">
  <rect x="3" y="3" width="26" height="26" rx="8" fill="#d6ef5a"/>
  <circle cx="12" cy="14" r="3.2" fill="#0a0a0c"/>
  <circle cx="20" cy="14" r="3.2" fill="#0a0a0c"/>
  <path d="M10 21c1.4 2.2 3.2 3.2 6 3.2s4.6-1 6-3.2"
        stroke="#0a0a0c" stroke-width="2.2" stroke-linecap="round"/>
</svg>
```

### Recipe

1. Read product palette (`brand.primary` / CSS variables). One loud tile color — saturation can be high.
2. `viewBox="0 0 32 32"` (or 24 / 64).
3. Container: rounded square is OK as **one** option; prefer at least one concept with cut corner, circle bite, parallelogram, or glyph escaping the tile.
4. Glyph in ink: 2–4 primitives; make it oversized relative to the tile when you want punch.
5. Stroke OK if thick (`≥2` on 32) and round caps — never hairline decoration.
6. Test at 24 CSS px on dark and light headers.

### Coffee / bakery twists（bolder than “drop on square”）

| Brand vibe | Bold bet（换隐喻，别三案同构） |
|---|---|
| DRIP | D 半截冲出砖外；或砖被滴形斜切掉一角 |
| LOAF | **禁止默认三件套**：L横笔拱 / 上升拱顶 / 炉口负形。改走：咬口容器、面团溢出砖、可颂新月、剖层三明治、表情化炉香脸、pretzel 扭结… |
| 派对 | 荧光砖 + 表情极端化（只留嘴或只留一眼） |

Do **not** ship three “rounded tile + centered drip/star” variants.  
Bakery 自测：若三案都能用「拱门/炉子/面包丘」一句话概括 → 想象力失败，重开概念长名单。

---

## Identity mode — SVG conventions

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 256" width="256" height="256"
     role="img" aria-labelledby="title">
  <title id="title">Brand symbol</title>
  <g id="symbol">
    <path fill="#111111" fill-rule="evenodd" d="…"/>
  </g>
</svg>
```

- Symbol canvas: `viewBox="0 0 256 256"`. Lockups: height 256, width follows.
- Padding inside viewBox ≈ 4–8%, consistent across a set.
- Coordinates: integers or 1–2 decimals. No `127.99999`.
- Group: `symbol`, `wordmark` when both exist.
- One file per variant: `brand-symbol-black.svg`, `brand-horizontal-color.svg`.

## Construction recipe (before path data)

Describe in words first, then code:

- Unit on 256 grid (8 or 16). Snap key sizes to multiples.
- ≤4 radii, reused. Angles: 0 / 15 / 30 / 45 / 60 / 90 only unless a concept needs otherwise.
- One memory hook. Footprint aspect ≈ 0.8–1.25.
- Optical centre slightly above geometric centre.

Prefer primitives: `circle`, `ellipse`, `rect` with `rx`, then `path`. Final silhouette may merge to one path.

## Paths

- Commands: `M L H V A C Q Z`. Prefer absolute while designing.
- Circular geometry → `A` arcs (consistent radii), not dozens of Bézier wobbles.
- Béziers: anchors at extrema; handles horizontal/vertical there; few points.
- Quarter-circle cubic handle length ≈ `0.5523 × r`.
- Always `Z` closed fills.
- Holes: one path + `fill-rule="evenodd"`, or opposite winding with `nonzero`.

```svg
<path fill-rule="evenodd" d="M128 16 A112 112 0 1 1 127.9 16 Z M128 80 A48 48 0 1 0 128.1 80 Z"/>
```

## Fills vs strokes

- Masters: prefer fills. Convert meaningful strokes to outlines for production.
- If stroke must stay during exploration: constant width; check joins at small size.
- No filters, masks-as-crutches, embedded rasters, external images, emoji in masters.

## Letterforms

- No live `<text>` in finals — construct as paths.
- Letter test: modified letter must still read as that letter at a glance.
- Junctions: no notches, slivers, lumps, ink traps where strokes meet.

## Optical corrections

- Round/pointed forms: slight overshoot (~1–3%) past the alignment line.
- Horizontals slightly thinner than verticals of the same “weight”.
- Reversed (white on black): often needs slightly thinner strokes/forms.
- Bone effect on blunt rounded joins: soften curvature ramp (squircle-ish corners).

## Small-size pass

At 16–24 px:

- Gaps that close → open or remove
- Multiple similar masses → merge to one silhouette
- Hairlines → thicken or drop
- Optional dedicated `*-small.svg` simplified drawing for favicon

## Render helpers (optional)

Any available path is fine; pick one and actually look:

```bash
# Example: rsvg
rsvg-convert -w 512 concept-a.svg -o renders/concept-a.png

# Example: headless chrome via project shot script, or temporary HTML + Playwright
```

If `~/.claude/skills/logo-design/scripts/` exists:

```bash
python3 ~/.claude/skills/logo-design/scripts/render_png.py concept-a.svg --out-dir renders --size 512
python3 ~/.claude/skills/logo-design/scripts/svg_audit.py concept-a.svg
```

Never use those scripts as an excuse to call GenerateImage.

## Category cliché starters (extend per brief)

| Category | Usually avoid without a fresh form |
|---|---|
| Coffee | Twin beans, full cup+steam comic, Starbucks-like badge |
| Bakery | Croissant silhouette, wheat sheaf, rolling pin, chef hat |
| Tech / AI | Circuit chip, node graph, generic hexagon, infinite loop |
| Finance | Up arrow, shield, globe, unbroken circle coin |
| Pets | Untwisted paw, bone, cartoon face |

## Anti-patterns (AI exam logos)

- Three concepts that are the same circle language with different cutouts
- “Rounded square + offset circle + arc” kit reused every brief
- Stack of 3 capsules / bars as a fake monogram
- Literal product illustration labeled as a mark
- Gradient or drop shadow used to hide weak geometry
- Card UI around the logo (borders, glass, shadows) when presenting
- Marketing adjectives instead of describing the shape
- Shipping a concept that failed the render self-check “to have three”

## Checkpoint HTML（Metaphor Exploration Spec）

- Tailwind CDN OK；深底 `#0A0A0A` + 淡网格；`max-w-[1040px]`；直角 `.spec-shell`
- 顶栏元数据 + 导语双栏 + **三栏** `DIR 01–03`（推荐案 `SELECTED` / 其余 `OPTION`）
- 每栏：准星虚线框主标 → 真像素阶梯 32 / 24 / 16 → 英文名 + ≤35 字中文形描述
- 等宽标注（JetBrains Mono）；**无圆角卡片**；无第四案填充；无长文说明
- 参考：`logo-svg-bakery/bold-v2/index.html`；终稿壳见 Brand Identity Spec

## After approval — kit checklist

- [ ] Final geometry + optical pass
- [ ] Black / white / mono SVG
- [ ] Optional 1–2 brand colours; greyscale still works
- [ ] Horizontal + stacked lockup if wordmark needed
- [ ] Small-size / favicon drawing
- [ ] One-pager: clear space, min size, misuse
- [ ] Trademark caveat stated once
- [ ] Optional `final/index.html` Brand Identity Spec（规范书壳 + 色卡字标 + FIG 01–04 mockup）— 见 SKILL「终稿 kit 约定」
- [ ] 直角细线壳 + 等宽标注；袋用**内联 SVG**（源稿 `assets/blank-bag.svg`）叠标
- [ ] 网站顶栏三点 = Mac 红绿灯 `#ff5f57` / `#febc2e` / `#28c840`
- [ ] 手机无幽灵图标、无 Dock 塞标；文案通用少行业话
