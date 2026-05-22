# INSTRUCTION FOR AI: Create a Concept Map — "Thời kỳ quá độ như một cây cầu lịch sử"

You are a frontend developer and visual designer. Your task is to produce a **single self-contained HTML file** that renders a concept map. Read every section of this document carefully before writing any code.

---

## 1. VISUAL STYLE REFERENCE

The output must look hand-drawn / sketch-style:

| Property | Value |
|---|---|
| Background | `#e9e9e9` (light gray) |
| Font | Google Font **"Caveat"** (handwritten feel), fallback: cursive |
| Node border | Irregular, sketch-like — achieve with SVG `feTurbulence` filter |
| Node shadow | Solid yellow `#f5c518`, offset `5px 5px 0px`, no blur |
| Node fill | `#ffffff` |
| Node border color | `#1a1a1a`, stroke-width ~2.5px |
| Arrow style | Curved SVG paths, hand-drawn look, no perfect straight lines |
| Arrowhead | Simple filled triangle via SVG `<marker>` |
| Accent color | Yellow `#f5c518` — used for shadows, highlights, timeline badges |
| Decorative elements | Stars ✦, lightbulb icon (top center), exclamation badge (bottom center) |
| Canvas size | minimum 1600 × 950px, centered in viewport with overflow scroll |

---

## 2. LAYOUT STRUCTURE

The map is organized horizontally like a bridge (cây cầu) from left to right:

```
[LEFT]                    [CENTER]                   [RIGHT]
Điểm xuất phát  ──────►  THỜI KỲ QUÁ ĐỘ  ──────►  Mục tiêu CNXH

                 [TOP-LEFT]      [TOP-RIGHT]
                 Vì sao cần?     Đặc điểm VN
                         ↑           ↑
                         └───[CENTER]───┘
                                 ↓
                 [BOTTOM-LEFT]          [BOTTOM-RIGHT]
                 Điều kiện KQ           Điều kiện CQ
                         └──────────┬──────────┘
                              [BOTTOM-CENTER]
                              Các nhịp cầu
```

Use `position: absolute` inside a relatively-positioned canvas div. Suggested node center coordinates:

| Node | x | y |
|---|---|---|
| CENTER (main) | 750 | 420 |
| LEFT | 120 | 420 |
| RIGHT | 1380 | 420 |
| TOP-LEFT | 420 | 170 |
| TOP-RIGHT | 1050 | 170 |
| BOTTOM-CENTER | 750 | 720 |
| BOTTOM-LEFT | 350 | 620 |
| BOTTOM-RIGHT | 1150 | 620 |

---

## 3. CONTENT FOR EACH NODE

### NODE: CENTER (largest node, most prominent)
```
THỜI KỲ QUÁ ĐỘ LÊN CNXH
= CÂY CẦU LỊCH SỬ
```
Style: font-size ~26px, font-weight 700, double-border effect, largest yellow shadow.

---

### NODE: LEFT — "Điểm xuất phát"
Title: **ĐIỂM XUẤT PHÁT**
- Thuộc địa nửa phong kiến
- Kinh tế nghèo nàn, lạc hậu
- Lực lượng sản xuất thấp
- Chiến tranh kéo dài

Arrow from this node → pointing RIGHT toward CENTER.

---

### NODE: RIGHT — "Mục tiêu"
Title: **MỤC TIÊU CNXH**
- Dân giàu — Nước mạnh
- Dân chủ — Công bằng — Văn minh
- Nhân dân lao động làm chủ
- Quan hệ hữu nghị quốc tế

Below the node, show 3 yellow pill-shaped badges in a row:
`2025` → `2030` → `2045`

Arrow from CENTER → pointing RIGHT toward this node.

---

### NODE: TOP-LEFT — "Vì sao cần quá độ?"
Title: **VÌ SAO CẦN QUÁ ĐỘ?**
- Không thể có CNXH ngay lập tức
- Xã hội cũ còn nhiều tàn dư
- LLSX chưa phát triển cao
- Cần cải tạo cái cũ, xây dựng cái mới

Arrow from CENTER ↑ pointing UP toward this node.

---

### NODE: TOP-RIGHT — "Đặc điểm Việt Nam"
Title: **ĐẶC ĐIỂM VIỆT NAM**
- Bỏ qua chế độ TBCN
- Không bỏ qua thành tựu nhân loại
- Tiếp thu KH-CN, quản lý tiên tiến
- Quá trình khó khăn, phức tạp, lâu dài

Arrow from CENTER ↑ pointing UP toward this node.

---

### NODE: BOTTOM-CENTER — "Các nhịp cầu trung gian"
Title: **CÁC NHỊP CẦU TRUNG GIAN**
Display content as a 2-column grid of small badges:
- Phát triển kinh tế
- Công nghiệp hóa — Hiện đại hóa
- Kinh tế TT định hướng XHCN
- Nhà nước pháp quyền XHCN
- Văn hóa và con người
- Hội nhập quốc tế

Arrow from CENTER ↓ pointing DOWN toward this node.

---

### NODE: BOTTOM-LEFT — "Điều kiện khách quan"
Title: **ĐIỀU KIỆN KHÁCH QUAN**
- Bối cảnh thời đại
- Toàn cầu hóa
- Cách mạng KH-CN
- Xu thế hợp tác & cạnh tranh

Arrow from this node → pointing toward BOTTOM-CENTER.

---

### NODE: BOTTOM-RIGHT — "Điều kiện chủ quan"
Title: **ĐIỀU KIỆN CHỦ QUAN**
- Đường lối đúng đắn của Đảng
- Nhà nước tổ chức & quản lý
- Nhân dân tham gia xây dựng
- Đoàn kết toàn dân tộc

Arrow from this node → pointing toward BOTTOM-CENTER.

---

## 4. ARROWS / CONNECTORS

Draw all arrows using a single inline `<svg>` layer positioned absolutely over the canvas:
- Use `<path d="M x1,y1 C cx1,cy1 cx2,cy2 x2,y2">` for curved paths
- Stroke: `#1a1a1a`, stroke-width: 2px, fill: none
- Add `marker-end="url(#arrowhead)"` on each path
- Define arrowhead in `<defs>`: a small filled polygon/triangle, fill `#1a1a1a`
- Curves should look slightly imperfect — vary the control points to avoid perfect symmetry

---

## 5. DECORATIVE ELEMENTS

- **Top center of canvas:** Hand-drawn style lightbulb — simple SVG outline, black stroke
- **Bottom center of canvas:** Yellow circle (`#f5c518`) with bold `!` inside
- **2–3 corners:** Small 4-pointed star shapes `✦` in dark color, font-size ~20px
- **Footer** (very bottom, centered, small italic text):
  *"Quá độ là quá trình lâu dài, nhiều bước trung gian."*

---

## 6. TECHNICAL REQUIREMENTS

- **Output: single HTML file**, no external JS libraries
- Google Fonts CDN only: `https://fonts.googleapis.com/css2?family=Caveat:wght@400;600;700&display=swap`
- All nodes: `position: absolute` inside a `position: relative` wrapper div
- SVG arrow layer: `position: absolute; top:0; left:0; width:100%; height:100%; pointer-events:none`
- Apply this SVG filter for sketch texture on nodes:
```xml
<filter id="sketch">
  <feTurbulence type="fractalNoise" baseFrequency="0.04" numOctaves="5" result="noise"/>
  <feDisplacementMap in="SourceGraphic" in2="noise" scale="1.5" xChannelSelector="R" yChannelSelector="G"/>
</filter>
```
- Wrap the canvas in a scrollable container for smaller screens
- No JavaScript needed unless used for minor polish

---

## 7. OUTPUT REQUIREMENT

Produce **only** the complete HTML file. Do not include any explanation, markdown code fences, or commentary before or after. Begin your response directly with `<!DOCTYPE html>` and end with `</html>`.
