# design-systems

Presentation Design System

1. Overview

本プロジェクトのPresentationは、以下の原則を基礎とする。

- 高密度な情報表示
- コンテンツ主体のPresentation
- Semantic Tokenによる一貫した表現
- 控えめな視覚階層
- Progressive Disclosure
- Narrativeによる明確な情報構造
- 小さく再利用可能なPresentation Component
- ThemeによるLight / Dark両対応
- 意味を色だけに依存しない
- 情報密度を保ちながら可読性を維持する
- 装飾ではなく構造によって理解を助ける

Presentationそのものを目立たせるのではなく、Audienceが内容へ集中し、短時間で構造と意味を理解できることを最優先する。

Presentationにおける視覚表現は、情報を飾るためではなく、

Understand
Compare
Explain
Emphasize
Remember

を支援するために使用する。

---

2. Design Principles

2.1 Content First

Presentationはコンテンツより目立ってはならない。

通常状態では、

- Background
- Border
- Divider
- Decoration
- Icon
- Footer

などの視覚的主張を抑える。

強調は以下の場合に限定する。

- Main Message
- 重要なData
- Decision
- Conclusion
- Warning
- Error
- 比較上重要な差分
- 現在説明している対象

強い装飾によって重要度を作るのではなく、

Position
Scale
Spacing
Contrast
Grouping

によってHierarchyを形成する。

---

2.2 One Slide, One Message

1枚のSlideには原則として1つのMain Messageを持たせる。

Slideは単なる情報のContainerではなく、Narrativeの1単位として扱う。

推奨構造:

Main Message
    ↓
Evidence
    ↓
Context

悪い例:

Q3 Update

Revenue
Hiring
Roadmap
Customer Feedback
Infrastructure

推奨:

Enterprise expansion drove most of Q3 growth

+24% YoY

Enterprise   █████████████████
SMB          ██████
Consumer     ███

Slide Titleは可能な限りTopicではなくConclusionやFindingを表す。

---

2.3 Dense, Not Cramped

高密度なPresentationを許容する。

ただし単純に、

- Font Sizeを小さくする
- Marginを削る
- 要素間隔を詰める

ことで情報量を増やしてはならない。

情報密度は、

- Grid
- Alignment
- Grouping
- Typography hierarchy
- Visual hierarchy
- Concise writing
- Progressive Disclosure

によって実現する。

Information Density → High
Visual Noise        → Low
Reading Effort      → Low

を目標とする。

---

2.4 Semantic Design

色、文字サイズ、余白などを直接的な値ではなく意味によって扱う。

悪い例:

font-size: 32pt
color: #888888

推奨:

type.heading.md
text.muted

Presentation Componentは、

「何色か」

ではなく、

「どの役割を持つか」

を指定する。

---

2.5 Narrative First

PresentationはSlideの集合ではなくNarrativeとして設計する。

Audienceが常に、

今何を説明しているか
↓
何が重要か
↓
なぜ重要か
↓
次に何を理解すべきか

を追える状態を作る。

Slide単体の美しさより、Slide間の関係性と説明順序を優先する。

---

2.6 Progressive Disclosure

Audienceへ一度に提示する情報量を制御する。

複雑な内容を一度にすべて表示する必要はない。

Step 1
↓
Step 2
↓
Step 3

のように段階的に情報を追加してよい。

例:

Problem

↓

Problem
Cause

↓

Problem
Cause
Solution

説明順序と表示順序を可能な限り一致させる。

Progressive Disclosureは情報を隠すためではなく、理解する順序を制御するために使用する。

---

2.7 Evidence First

主張だけでなく、それを支えるEvidenceを示す。

Claim
+
Evidence

を基本構造とする。

Evidenceには、

- Data
- Chart
- Example
- Screenshot
- Quote
- Experiment Result
- Observation

などを使用する。

DecorationをEvidenceの代替として使用しない。

---

3. Canvas

3.1 Aspect Ratio

標準:

16:9

を使用する。

基準Canvas:

1920 × 1080

Design Tokenは特定解像度ではなく相対的なScaleとして扱う。

---

3.2 Safe Area

重要なContentをSlide端に近づけすぎない。

推奨:

horizontal margin   72–96px
vertical margin     56–72px

Title、Body、Chart、Diagramなどは原則Safe Area内へ配置する。

BackgroundやDecorative SurfaceはCanvas端まで延長してよい。

---

4. Grid

標準:

12 Column Grid

推奨:

outer margin    72–96px
column gap      20–32px
baseline        8px

すべての要素を厳密にColumnへ合わせる必要はない。

ただし、

- Title
- Paragraph
- Chart
- Table
- Diagram
- Caption

の基準線は意図的に揃える。

Alignmentを主要なVisual Hierarchyとして使用する。

---

5. Typography

PresentationとContent用Fontを分離する。

font.ui
font.mono

推奨:

General Presentation:
  Sans Serif
  Weight 400–500

Technical Content:
  Monospace
  Weight 400

極端なFont Weightは使用しない。

font.normal      400
font.medium      500
font.semibold    600

"700+"は原則として使用しない。

強調はWeightだけに依存しない。

---

5.1 Type Scale

標準:

caption.xs        13–14pt
caption.sm        15–16pt

body.sm           17–18pt
body.md           20–22pt
body.lg           24–26pt

heading.sm        26–30pt
heading.md        32–36pt
heading.lg        40–44pt

title.default     42–48pt
title.hero        52–60pt

metric.md         40–48pt
metric.lg         56–72pt

極端に巨大なTypographyは原則使用しない。

大きさだけでBrand Expressionを作らない。

---

5.2 Slide Title

標準:

32–40pt
font.medium / semibold

Titleは短くする。

可能な限り、

Topic

ではなく、

Message
Finding
Conclusion

を書く。

悪い例:

Revenue Analysis

推奨:

Enterprise drove 78% of revenue growth

---

5.3 Body

基本:

20–22pt

Dense Slide:

17–18pt

17pt未満の文章が多数必要になる場合は、情報構造そのものを再検討する。

---

5.4 Line Height

Title       1.05–1.15
Body        1.25–1.4
Long Text   1.4–1.5
Code        1.35–1.5

---

5.5 Line Length

Paragraphは横に伸ばしすぎない。

目安:

40–70 characters / line

長文をCanvas幅いっぱいに配置しない。

---

6. Color

固定色ではなくSemantic Colorを使用する。

Text

text.default
text.muted
text.hidden
text.accent
text.selected

用途:

Token| 用途
"text.default"| 通常のContent
"text.muted"| 補助情報
"text.hidden"| 非常に弱い補足情報
"text.accent"| 強調・重要情報
"text.selected"| 現在説明中の対象

---

6.1 Semantic State

status.info
status.success
status.warning
status.error

必要な場合:

status.created
status.modified
status.deleted
status.conflict

意味を色だけで表現しない。

以下を必要に応じて併用する。

Label
Icon
Position
Shape
Annotation

---

6.2 Accent

Accent Colorは限定的に使用する。

主な用途:

Main finding
Important data
Current step
Selected series
Important keyword

1枚のSlide内で複数のAccent Colorを競合させない。

原則として、

1 Primary Accent

を基本とする。

---

7. Surface

Surface hierarchy:

surface.background
surface.default
surface.panel
surface.elevated

視覚階層:

Background
↓
Content
↓
Supporting Surface
↓
Emphasized Surface

Surface間の差は小さくする。

強い色差ではなく、

- Brightness
- Border
- Whitespace

によって分離する。

---

7.1 Card

すべてのContentをCardで囲まない。

まず、

Spacing
Alignment
Typography

によってGroupingする。

Cardを使用するのは、Contentが独立したSurfaceとして意味を持つ場合のみとする。

悪い例:

┌──────┐ ┌──────┐ ┌──────┐
│ Card │ │ Card │ │ Card │
└──────┘ └──────┘ └──────┘

┌──────┐ ┌──────┐ ┌──────┐
│ Card │ │ Card │ │ Card │
└──────┘ └──────┘ └──────┘

すべてが同じ視覚的重要度になり、Hierarchyが失われる。

---

8. Spacing

Spacing Scale:

spacing.4
spacing.8
spacing.12
spacing.16
spacing.24
spacing.32
spacing.40
spacing.48
spacing.64
spacing.80
spacing.96

PresentationではWhitespaceを情報構造として扱う。

目安:

Inside small group      8–16px
Between groups         24–40px
Between sections       48–64px
Major separation       64–96px

関連性が強いほど近く配置する。

---

9. Radius

角丸は控えめに使用する。

radius.none     0px
radius.xs       2px
radius.sm       4px
radius.md       6px
radius.lg       8px

標準:

4–6px

過度なPill Shapeや大型Rounded CardをBrand Expressionとして使用しない。

---

10. Border

border.default
border.muted
border.selected

Borderは原則:

1px

重要な区切りのみ:

2px

を許容する。

BorderはDecorationではなく構造の表現として使用する。

---

11. Shadow

Shadowは原則として使用しない。

使用を許容するもの:

Floating screenshot
Overlay
Layered architecture diagram
Intentional depth

通常のGroupingには、

Spacing
Border
Surface

を優先する。

---

12. Visual Hierarchy

Hierarchyは以下の順序を基本とする。

1. Position
2. Scale
3. Spacing
4. Contrast
5. Weight
6. Surface
7. Color

強調が必要になるたびにAccent ColorやBoldへ依存しない。

---

12.1 Focal Point

原則として1枚のSlideにつき1つのFocal Pointを作る。

例:

Main statement
Important metric
Highlighted chart series
Key diagram node
Critical comparison

複数の要素を同時にPrimaryとして扱わない。

---

12.2 Reading Order

基本:

Top → Bottom
Left → Right

を尊重する。

意図的に異なる順序を使用する場合は、視線誘導を明確にする。

---

13. Presentation Components

Presentationは固定されたTemplateではなく、小さなComponentのCompositionとして構築する。

主要Component:

SlideTitle
SectionLabel
BodyText
Metric
Caption
Callout
Figure
Chart
Table
Diagram
CodeBlock
Quote
Divider
Source
Footer
StepIndicator

各Componentは過度な装飾を持たない。

意味はCompositionによって形成する。

---

14. Slide Structure

標準的なSlide:

Slide
├── Context / Section
├── Main Message
├── Content
│   ├── Primary Evidence
│   └── Supporting Evidence
└── Source / Footer

すべてのSlotを使用する必要はない。

---

15. Slide Archetypes

15.1 Title Slide

構造:

Title
Subtitle / Context
Author / Date

余白を大きく取る。

LogoやBrand ElementをContentより目立たせない。

---

15.2 Section Slide

Section Number
Section Title
Short Context

Narrative上の大きな切り替わりに使用する。

通常Slideより低密度にする。

---

15.3 Key Message

Main Statement

Supporting Evidence

1つのConclusionやDecisionを強く伝える場合に使用する。

---

15.4 Text + Visual

┌──────────────┬──────────────────┐
│ Text         │ Visual           │
│              │                  │
│ Explanation  │ Chart / Diagram  │
└──────────────┴──────────────────┘

一般的な説明Slideとして使用する。

---

15.5 Comparison

A                B
────────         ────────
Content          Content

比較対象には可能な限り同一構造を使用する。

意図しないVisual Weightの差を作らない。

---

15.6 Data Slide

Finding
↓
Chart
↓
Annotation / Context

Dataそのものではなく、Dataから得られる意味をTitleにする。

---

15.7 Process

01 → 02 → 03 → 04

実際に順序やFlowが存在する場合のみArrowを使用する。

単なる並列要素にArrowを使用しない。

---

15.8 Architecture

Input
↓
Processing
↓
System
↓
Output

すべてのNodeを同じ強さで表示せず、重要なFlowを優先する。

---

15.9 Code

Main Message
Code
Annotation

Codeを装飾ではなくContentとして扱う。

---

15.10 Appendix

詳細情報を高密度で表示してよい。

ただし、

- Font Size
- Contrast
- Alignment
- Grouping

の最低基準は維持する。

---

16. Metrics

Metricは数字だけでなく意味とセットで表示する。

悪い例:

24%

推奨:

24%
Q3 revenue growth
↑ 8 pts YoY

構造:

Value
Label
Comparison / Context

Valueだけを巨大化しすぎない。

---

17. Charts

ChartはDataを飾るためではなく、関係性を説明するために使用する。

目的:

Change
Difference
Relationship
Distribution
Composition

目的に応じてChart Typeを選択する。

---

17.1 Chart Color

chart.default
chart.muted
chart.accent
chart.reference

Semantic Stateが必要な場合:

status.success
status.warning
status.error

すべてのSeriesを異なる強い色にしない。

基本:

Context      → muted
Primary      → default
Important    → accent

---

17.2 Gridline

GridlineはDataより弱くする。

grid → border.muted

必要なGridlineだけを残す。

---

17.3 Axis

Axis Label:

text.muted

Axisそのものを強調しない。

---

17.4 Direct Label

可能な場合はLegendではなくDirect Labelを使用する。

推奨:

Enterprise ───────── 42%
SMB        ───────   31%
Consumer   ────      18%

AudienceにChartとLegendを往復させない。

---

17.5 Annotation

重要なEventや変化には直接Annotationを付ける。

例:

Product launch
      ↓
──────●────────────

      +24%

Annotationを大量に配置しない。

---

17.6 Avoid

原則として以下を使用しない。

3D Chart
Heavy gradient
Decorative shadow
Exploded pie
Excessive gridline
Rainbow palette

---

18. Tables

Tableは比較が必要な場合に使用する。

Spreadsheetをそのまま貼り付けない。

基本構造:

Header
────────────────────────
Row
Row
Row

Vertical Borderは原則使用しない。

---

18.1 Alignment

Text      → Left
Number    → Right
Label     → Left

同一Column内のAlignmentを統一する。

---

18.2 Highlight

重要Row / Columnのみ、

Accent
Surface
Weight

によって強調する。

すべてのCellを囲わない。

---

18.3 Density

1枚のSlideでは概ね、

5–8 columns
6–10 rows

を目安とする。

これ以上必要な場合は、

Split
Summarize
Highlight
Appendix

を検討する。

---

19. Diagram

Diagramは構造・関係・Flowを説明する。

基本要素:

Node
Container
Connector
Label
Annotation

---

19.1 Node

Nodeは必要以上にCard化しない。

Icon
Label
Metadata

だけで成立する場合はBorderやBackgroundを省略してよい。

---

19.2 Connector

意味によって使い分ける。

Line
→ relationship

Arrow
→ direction / flow

関係性がない要素をLineで接続しない。

---

19.3 Flow

重要なFlow:

Foreground / Accent

補助Flow:

Muted

としてHierarchyを作る。

---

19.4 Diagram Density

すべての内部構造を1枚に表示しない。

必要に応じて、

Overview
↓
Subsystem
↓
Detail

へ分割する。

---

20. Code

Technical PresentationではCodeを主要Contentとして扱う。

Font:

font.mono

推奨:

18–22pt

Dense:

16–18pt

---

20.1 Syntax Highlight

Syntax Colorは抑制する。

基本:

code.default
code.muted
code.accent
code.comment
status.error

多数の色を使用しない。

---

20.2 Highlight

説明中の行のみ、

Surface
Left Border
Accent

などを使用して強調する。

その他の行を読めないほど薄くしない。

---

21. Imagery

Imageは以下の役割がある場合に使用する。

Evidence
Context
Example
Object
Place
Person
Product

空白を埋めるためのDecorative Imageは使用しない。

---

21.1 Cropping

ImageはLayoutに合わせて意図的にCropする。

重要なSubjectを中途半端に切らない。

---

21.2 Screenshot

Screenshotはそのまま縮小して配置しない。

必要に応じて、

Crop
Zoom
Annotation
Highlight

を行い、説明対象を明確にする。

---

22. Iconography

同一のIcon LanguageをPresentation全体で使用する。

サイズ:

icon.sm       18–20px
icon.md       24–28px
icon.lg       32–40px
icon.xl       48–64px

用途:

Meaning
Status
Category
Direction

装飾目的で大量に使用しない。

一般的でないIconにはLabelを併用する。

---

23. Callout

重要な補助情報を局所的に強調する。

構造:

Label
Message

例:

KEY FINDING

Latency decreased by 38%

1枚のSlideに複数のCalloutを乱用しない。

---

24. Quote

Quoteは文章そのものに意味がある場合に使用する。

構造:

“Quote”

Source

巨大なQuotation MarkなどのDecorationは不要。

Quoteの文章を主役にする。

---

25. Source

Data、Quote、外部情報には必要に応じてSourceを表示する。

推奨:

13–15pt
text.muted

Sourceは読める状態を維持する。

長いURLそのものより、

Organization / Publication / Date

など識別可能な情報を優先する。

---

26. Footer

Footerは最小限とする。

使用可能:

Section
Slide Number
Confidentiality
Brand Mark

毎Slideに大型のLogoやDecorative Footerを置かない。

---

27. Motion

Motionは内容の理解を助ける場合のみ使用する。

用途:

Progressive Reveal
Sequence
Cause → Effect
Before → After
Spatial Relationship

Animationそのものを見せることを目的としない。

---

27.1 Default Motion

基本:

Appear
Fade

を使用する。

---

27.2 Directional Motion

方向に意味がある場合のみ使用する。

Left → Right
Process

Bottom → Top
Growth

MotionとContentの意味を一致させる。

---

27.3 Progressive Reveal

Audienceがまだ説明されていない情報を先読みすることで理解が阻害される場合、段階表示する。

A

↓

A
B

↓

A
B
C

表示済みの要素を不用意に消さず、必要なContextを維持する。

---

28. Transition

Deck全体でTransition Styleを統一する。

基本:

Cut
Fade

特殊TransitionはNarrative上の意味がある場合に限定する。

---

29. Theme

Light / Darkの双方に対応する。

Light

適する用途:

Business Review
Report
Data-heavy Presentation
Document-oriented Content
Bright Environment

---

Dark

適する用途:

Technical Presentation
Stage Presentation
Product Presentation
Image-heavy Content
Dark Environment

ThemeによってSemantic Meaningを変更しない。

---

30. Density

Presentation Density:

sparse
default
dense

---

Sparse

用途:

Title
Section
Key Message
Decision
Hero Metric

---

Default

用途:

Explanation
Comparison
Chart
Diagram
Process

---

Dense

用途:

Architecture
Table
Code
Technical Analysis
Appendix

Density変更時もComponentのVisual Languageは維持する。

---

31. Accessibility

Presentationはさまざまな距離・Display・視聴環境で閲覧される。

以下を考慮する。

- Contrast
- Viewing distance
- Color vision
- Projector quality
- Video conferencing compression
- Small displays
- Reduced Motion

---

31.1 Color

意味をColorだけで表現しない。

悪い例:

Green
Red

のみで状態を示す。

推奨:

✓ Success
! Warning
× Error

など形状・Labelを併用する。

---

31.2 Text Size

本文:

18pt+

を基本とする。

SourceやCaption以外で極端に小さなTextを使用しない。

---

32. Remote Presentation

Video ConferenceではSlideが大幅に縮小表示されることを考慮する。

以下に依存しすぎない。

Thin lines
Tiny captions
Fine textures
Small chart labels
Subtle color differences

重要情報はLaptop Display上の小さなPreviewでも識別可能であることを目標とする。

---

33. Writing

Presentationでは文章そのものもDesignの一部として扱う。

Title

短く、結論を優先する。

Body

完全なParagraphより、短いStatementを優先する。

Bullet

Bulletを文章のDumpとして使用しない。

推奨:

3–5 items

程度。

各Itemはできる限り1〜2行以内にする。

---

34. Bullet List

Bulletは、

並列した複数の情報

を表す場合のみ使用する。

順序がある場合は、

01
02
03

を使用する。

関係性がある場合はDiagramを使用する。

Bulletですべてを表現しない。

---

35. Sectioning

長いPresentationではSectionを明確にする。

例:

01 Context
02 Findings
03 Decision
04 Plan

現在位置を常時大きく表示する必要はない。

Section切り替え時に十分なContextを提供する。

---

36. Content Reduction

Slideへ情報が収まらない場合、最初にFont Sizeを下げない。

以下の順序で整理する。

1. Remove redundant information
2. Shorten wording
3. Group related information
4. Move supporting detail
5. Split slide
6. Reduce typography only if necessary

情報量の問題をTypographyだけで解決しない。

---

37. Presentation Primitives

Presentation Componentは可能な限り以下のPrimitiveへ分解する。

Text
Metric
Image
Shape
Line
Icon
Chart
Table
Code
Annotation

複雑なComponentはこれらをCompositionして構築する。

固定的な装飾をComponent内部へ持ち込みすぎない。

---

38. Avoid

原則として以下を使用しない。

Decorative gradient
Glass effect
Heavy shadow
Gradient text
Random geometric shape
3D icon
Excessive rounded card
Decorative stock photo
Rainbow chart
Oversized logo
Tiny body text
Unnecessary animation

視覚的な個性はDecorationではなく、

Typography
Grid
Density
Precision
Color semantics
Composition
Restraint

によって形成する。

---

39. Brand Character

Presentationから受ける印象:

Precise
Technical
Calm
Dense
Structured
Confident
Neutral
Content-driven

避ける印象:

Flashy
Over-designed
Decorative
Marketing-heavy
Template-driven
Playful without purpose

---

40. Final Principles

Content
>
Decoration

Message
>
Template

Structure
>
Visual Effects

Evidence
>
Claim Alone

Narrative
>
Individual Slide

Progressive Disclosure
>
Showing Everything at Once

Position
>
Color

Whitespace
>
Card

Semantic Meaning
>
Fixed Styling

Clarity
>
Density for Density's Sake

Audience Understanding
>
Visual Novelty

本Design Systemは、情報量の多いTechnical / Business Presentationに耐えられる高いDensityを持ちながら、視覚的ノイズを抑え、内容そのものを主役とする。

Brandは装飾によって表現するのではなく、

Typography、Grid、Semantic Color、情報密度、精密なAlignment、抑制されたHierarchy

によって形成する。
