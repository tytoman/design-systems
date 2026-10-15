Design System

1. Overview

本プロジェクトのUIは、Zed Editorに見られる以下の原則を基礎とする。

- 高密度な情報表示
- コンテンツ主体のUI
- Semantic Tokenによる一貫した表現
- 控えめな視覚階層
- Progressive Disclosure
- Keyboard-first Interaction
- 小さく再利用可能なUI Component
- ThemeによるLight / Dark両対応
- 状態を色だけに依存しない
- UI Densityを保ちながら可読性を維持する

UIそのものを目立たせるのではなく、ユーザーが操作対象となるコンテンツへ集中できることを最優先する。

---

2. Design Principles

2.1 Content First

UIはコンテンツより目立ってはならない。

通常状態では背景、境界線、アイコン、ボタンなどの視覚的主張を抑える。

強調は以下の場合に限定する。

- 選択中
- Hover中
- Focus中
- エラー
- 警告
- 重要なPrimary Action

---

2.2 Dense, Not Cramped

高密度なUIを採用する。

ただし単純に余白を削るのではなく、

- 一貫したSpacing
- 明確なAlignment
- Typography hierarchy
- Surface hierarchy

によって読みやすさを維持する。

標準的な操作要素は18〜32px程度の高さを基本とする。

---

2.3 Semantic Design

色や余白を直接指定するのではなく、意味を持つTokenを使用する。

悪い例:

color: #888888
padding: 4px

推奨:

color: text.muted
padding: spacing.4

コンポーネントは「どの色か」ではなく「何を意味するか」を指定する。

---

2.4 Progressive Disclosure

補助操作は常時表示しない。

例:

通常

filename.rs


Hover

filename.rs                  Rename  Delete

以下の要素は必要に応じてHover時のみ表示する。

- 補助Action
- Context Action
- Secondary Button
- Additional metadata

---

2.5 Keyboard First

主要操作はKeyboardから実行可能にする。

可能な限り、

- Shortcut
- Focus navigation
- Command palette
- Escapeによるキャンセル
- Enterによる確定

を提供する。

Keyboard Shortcutは単なる説明文ではなく、UI Componentとして扱う。

---

3. Design Tokens

---

3.1 Color

固定色ではなくSemantic Colorを使用する。

Text

text.default
text.muted
text.hidden
text.disabled
text.placeholder
text.accent
text.selected

用途:

Token| 用途
"text.default"| 通常テキスト
"text.muted"| 補助情報
"text.hidden"| 非常に弱い情報
"text.disabled"| 無効状態
"text.placeholder"| Placeholder
"text.accent"| リンク・強調
"text.selected"| 選択状態

---

Semantic State

status.info
status.success
status.warning
status.error

追加でVersion Control等が必要な場合:

status.created
status.modified
status.deleted
status.conflict

---

3.2 Surface

背景色にはSurface hierarchyを使用する。

surface.background
surface.default
surface.editor
surface.panel
surface.elevated
surface.modal

視覚階層:

Background
    ↓
Surface
    ↓
Editor / Panel
    ↓
Elevated Surface
    ↓
Modal

Surface間の差は小さくする。

強い色差ではなく、

- 微妙なBrightness差
- Border
- 必要最低限のShadow

で階層を表現する。

---

3.3 Interactive Element

操作要素用Token:

element.background
element.hover
element.active
element.selected
element.disabled

背景を通常状態では表示しないGhost系Element:

element.ghost.background
element.ghost.hover
element.ghost.active
element.ghost.selected
element.ghost.disabled

Ghost ElementはToolbar、Icon Button、List Actionなどで優先的に使用する。

---

3.4 Border

border.default
border.muted
border.focused
border.selected
border.disabled

Borderは原則1px。

Surface間の区切りにはShadowよりBorderを優先する。

---

3.5 Typography

UIとコンテンツ用フォントを分離する。

font.ui
font.mono

推奨:

UI Font:
  Sans Serif
  Weight 400–500

Code / Technical Content:
  Monospace
  Weight 400

---

Text Size

text.xs      10px
text.sm      12px
text.md      14px
text.lg      16px

基本UI:

12px / 14px

を中心とする。

---

Heading

heading.xs     14px
heading.sm     16px
heading.md     18px
heading.lg     20px
heading.xl     22px

UI内で極端に大きな見出しは使用しない。

---

Font Weight

font.normal      400
font.medium      500
font.semibold    600

"700+"は原則として使用しない。

強調はWeightだけでなく、

- Color
- Spacing
- Surface

も併用する。

---

3.6 Line Height

UI:

1.2–1.4

長文:

1.5–1.6

コード:

1.5–1.65

---

3.7 Spacing

基本Spacing Scale:

0
1px
2px
3px
4px
6px
8px
12px
16px
20px
24px
32px
40px
48px

Semantic Token:

spacing.0
spacing.1
spacing.2
spacing.3
spacing.4
spacing.6
spacing.8
spacing.12
spacing.16
spacing.20
spacing.24
spacing.32
spacing.40
spacing.48

主要UIでは以下を多用する。

2px
4px
6px
8px
12px

---

3.8 Density

UI Density:

compact
default
comfortable

Defaultを基準とする。

例:

Token| Compact| Default| Comfortable
Small Gap| 2| 4| 6
Medium Gap| 4| 6| 8
Large Gap| 6| 8| 12

密度変更時もComponent構造は変更しない。

SpacingのみをScaleさせる。

---

3.9 Radius

角丸は控えめに使用する。

radius.none     0px
radius.xs       2px
radius.sm       4px
radius.md       6px
radius.lg       8px

標準:

4px

ButtonやInputで過度なPill Shapeは使用しない。

---

3.10 Shadow

ShadowはFloating UIに限定する。

通常Surfaceでは使用しない。

shadow.none

shadow.elevated
0 2px 3px rgba(0, 0, 0, 0.12)

shadow.modal
0 8px 24px rgba(0, 0, 0, 0.18)

使用対象:

Popover
Dropdown
Context Menu
Tooltip
Modal
Floating Panel

---

4. Iconography

UI Iconは小型を基本とする。

icon.indicator    10px
icon.xs           12px
icon.sm           14px
icon.md           16px
icon.xl           48px

標準:

16px

密度の高いUI:

12px / 14px

---

Icon Color

icon.default
icon.muted
icon.disabled
icon.placeholder
icon.accent

原則としてIcon固有の固定色は使用しない。

---

5. Interaction States

Interactive Componentは最低限以下を実装する。

default
hover
active
focus
selected
disabled

---

Default

視覚的主張を最小化する。

---

Hover

背景またはForegroundを軽く変化させる。

background → element.hover

---

Active

Hoverより一段強い状態。

background → element.active

---

Focus

Keyboard Focusを明確に表示する。

border → border.focused

必要に応じてFocus Ringを追加する。

---

Selected

選択されたItemは背景とForegroundの両方で表現する。

---

Disabled

Opacityだけに依存しない。

foreground → disabled
background → disabled
interaction → disabled
cursor → default

---

6. Buttons

Buttonは用途に応じてVariantを使用する。

subtle
filled
outlined
outlinedGhost
tinted
transparent

---

6.1 Subtle

標準Button。

通常状態では背景を持たない。

Default:
  background: transparent

Hover:
  background: element.ghost.hover

Active:
  background: element.ghost.active

ToolbarやPanel Actionでは原則Subtleを使用する。

---

6.2 Filled

重要なPrimary Action用。

例:

Create
Save
Confirm
Run

同一画面内で乱用しない。

---

6.3 Outlined

Secondary Action用。

border: border.default

---

6.4 Outlined Ghost

通常時の視覚的重要度をさらに下げたOutlined Button。

---

6.5 Tinted

Semantic Action用。

accent
success
warning
error

例:

Delete → error
Retry → warning
Apply → accent

---

6.6 Transparent

背景変化を持たず、Foregroundのみ変化させる。

非常に軽量な補助操作に使用する。

---

6.7 Button Size

button.compact    18px
button.default    22px
button.medium     28px
button.large      32px

標準:

22–28px

---

7. Icon Button

IconのみのButtonには必ずTooltipを付ける。

[ Icon ]

Tooltip:

Action Name

Ctrl Shift P

Icon Buttonは通常Subtle Variantを使用する。

---

8. Input

標準Input:

height: 28–32px
border: 1px
radius: 4px
padding-inline: 6–8px
font-size: 12–14px

States:

default
hover
focus
error
disabled

Focus時:

border → border.focused

Error時:

border → status.error

---

9. Checkbox

構造:

[ ] Label

States:

unchecked
checked
indeterminate
disabled
focused

Control Size:

14–16px

---

10. Switch

Boolean設定にのみ使用する。

Label                         [ ON ]

Checkboxとの使い分け:

即座に状態が変化する設定
→ Switch

フォーム送信時に確定する選択
→ Checkbox

---

11. List Item

List Itemは本Design Systemの主要Componentとする。

基本構造:

┌─────────────────────────────────────┐
│ Start   Content             End     │
└─────────────────────────────────────┘

Slots:

start
content
end
hoverEnd

---

Density

extraDense
dense
default
sparse

---

States

default
hover
selected
focused
disabled

---

Example

▾  src                         3 files
   main.rs                     M
   app.rs
   theme.rs                    +

補助Action:

main.rs                  Rename Delete

はHover時のみ表示してよい。

---

12. Tree

TreeはList Itemを基礎として構築する。

構造:

Chevron
Icon
Label
Metadata
Actions

Indent:

12–16px / level

階層表現を色ではなくIndentで行う。

---

13. Tabs

Tab Bar:

height: 28–32px

Tab:

Icon
Label
Modified Indicator
Close Action

Selected Tab:

- Background
- Foreground
- Border

の最低2つ以上で状態を表現する。

Close Buttonは原則Hover時のみ表示する。

---

14. Panel

Panel構造:

Panel
├── Header
│   ├── Title
│   └── Actions
│
└── Content

Panel同士は強いShadowではなくBorderで分離する。

---

15. Toolbar

Toolbarは非常に高密度に保つ。

height: 28–32px

主に以下を使用する。

Icon Button
Button Subtle
Divider
Dropdown
Breadcrumb

Filled ButtonをToolbar内で乱用しない。

---

16. Tooltip

原則として以下にTooltipを付ける。

- Icon Button
- 意味が明確でないIcon
- Shortcutを持つAction
- Truncated Label
- Disabled Actionの理由

Tooltip構造:

Action Name

Shortcut
Description

例:

Toggle Sidebar

Ctrl+B

---

17. Popover

PopoverはElevated Surfaceを使用する。

surface: elevated
border: default
shadow: elevated
radius: md
padding: 4–8px

Popover内部も高密度を維持する。

---

18. Context Menu

Menu Item:

Icon
Label
Shortcut

推奨Height:

24–28px

Dangerous Action:

text → status.error

---

19. Dropdown

Trigger:

Button Subtle
または
Input-like Control

Dropdown Surface:

surface.elevated

Selected ItemにはCheckまたはSelected Stateを表示する。

---

20. Modal

Modalのみ比較的強いElevationを許可する。

構造:

Modal
├── Header
├── Content
└── Footer

Primary Actionは原則1つ。

例:

Cancel      Delete

---

21. Empty State

構造:

Large Icon

Title

Description

Primary / Secondary Action

Icon:

48px

大きなIllustrationは原則使用しない。

---

22. Separator

Separator:

1px
border.muted

Spacingによるグループ化を優先し、Separatorを乱用しない。

---

23. Scrollbar

Scrollbarは通常時に目立たせない。

Default:
  low contrast

Hover:
  higher contrast

Trackを常時強調しない。

---

24. Status Indicators

StatusはSemantic Colorを使用する。

Info       blue-like semantic
Success    green-like semantic
Warning    yellow/orange-like semantic
Error      red-like semantic

実際のHueはTheme側で決定する。

Component側から色値を直接指定しない。

---

25. Theme Architecture

ThemeはSemantic Tokenを実装する。

Theme
├── Surface
├── Text
├── Icon
├── Border
├── Element
├── Status
├── Editor
├── Panel
├── Terminal
└── Syntax

ComponentはThemeの具体色を知らない。

---

26. Light / Dark Theme

Light / Dark双方で同じSemantic Hierarchyを維持する。

悪い例:

Dark ThemeではPanelが上位Surface
Light ThemeではPanelが下位Surface

推奨:

Themeにかかわらず

Background
<
Surface
<
Elevated
<
Modal

という視覚的階層を維持する。

---

27. Layout

基本レイアウトはFlex Layoutを使用する。

優先:

Flex
Grid
Absolute Position

Absolute PositionはOverlay等に限定する。

---

28. Alignment

高密度UIではAlignmentの乱れが特に目立つ。

以下を揃える。

Icon center
Text baseline
Control height
Panel padding
List indentation

Icon + Text:

gap: 4–6px

---

29. Standard Dimensions

推奨値:

Toolbar Height        28–32px

Tab Height            28–32px

Input Height          28–32px

Button Height
  Compact             18px
  Default             22px
  Medium              28px
  Large               32px

Icon
  Small               14px
  Default             16px

Panel Padding
  Dense               4px
  Default             8px
  Comfortable         12px

List Item
  Dense               20–24px
  Default             24–28px
  Sparse              28–32px

---

30. Motion

Animationは必要最低限とする。

使用対象:

Popover opening
Tooltip
Panel expansion
Selection
Loading

Duration:

fast       80–120ms
default    120–160ms
slow       180–220ms

300ms以上のAnimationは原則使用しない。

EditorやDesktop Toolでは操作レスポンスを優先する。

---

31. Accessibility

Interactive Componentは以下を持つ。

label
description
role
focus state
disabled state
keyboard interaction

必要に応じて:

expanded
checked
selected
value
keyboard shortcut

を提供する。

---

Focus Navigation

以下をサポートする。

Tab
Shift+Tab
Arrow Keys
Enter
Space
Escape

---

Color Independence

状態を色だけで伝えない。

例:

Error

× Error message

Selected

✓ Selected

---

32. Component Architecture

Componentは以下の構造を持つ。

Component
├── Variant
├── Size
├── State
├── Semantic Color
├── Accessibility
└── Content

例:

Button
├── variant: subtle
├── size: default
├── state: hover
├── color: accent
├── icon
└── label

---

33. Component API Rules

Component APIでは可能な限りPrimitive値を直接公開しない。

悪い例:

Button {
    height: 23,
    color: "#ff0000",
    padding: 7
}

推奨:

Button {
    size: Default,
    tone: Error,
    style: Subtle
}

---

34. Component Preview

全ComponentについてPreview画面を用意する。

最低限以下を表示する。

Default
Hover
Active
Focus
Disabled
Selected

Variantがある場合はすべて表示する。

例:

Button

Subtle
Filled
Outlined
Transparent

Default
Hover
Disabled

---

35. Component Status

Componentの成熟度を管理する。

Experimental
Ready
Stable
Deprecated

---

36. Naming

具体的な見た目ではなく意味で命名する。

悪い例:

GrayText
BlueButton
DarkPanel

推奨:

MutedText
AccentButton
PanelSurface

---

37. Visual Hierarchy

視覚階層は以下の順で作る。

1. Layout
2. Spacing
3. Typography
4. Surface
5. Border
6. Color
7. Shadow

Shadowを最初の手段にしない。

---

38. Do

推奨:

- 小さいControl
- 12–14px中心のUI Text
- 14–16px Icon
- Semantic Color
- 1px Border
- Subtle Hover
- Keyboard Shortcut
- Tooltip
- Ghost Button
- Hover Action
- Tight Spacing
- Clear Alignment

---

39. Don't

避ける:

- 巨大なButton
- 過剰なPadding
- 強いDrop Shadow
- 大量のCard
- 不要なGradient
- 過剰なRounded Corner
- 固定HEX Color
- Colorだけによる状態表現
- 常時表示されるSecondary Action
- 24px以上のIcon乱用
- Web Landing Page風UI

---

40. Recommended Default Style

迷った場合は以下を使用する。

Font Size:
14px

Secondary Font Size:
12px

Icon:
16px

Gap:
4px

Control Height:
28px

Border:
1px

Radius:
4px

Panel Padding:
8px

Button:
Subtle

Surface Separation:
Border

Secondary Action:
Hover only

Elevation:
None

---

41. Example Component Composition

Panel Header

┌─────────────────────────────────────────────┐
│ Project                            +  ⋯      │
├─────────────────────────────────────────────┤

Specification:

height: 30px

padding:
  horizontal: 8px

title:
  size: 12–14px
  weight: 500

actions:
  icon: 14px
  button: subtle

---

42. Example List

▾ src
  ◇ main.rs                         M
  ◇ app.rs
  ◇ theme.rs                       +

Specification:

height:
24px

icon:
14px

font:
12–14px

indent:
12px

hover:
ghost background

selected:
selected background

---

43. Example Toolbar

[≡] [←] [→]     Project / src / main.rs     [Run] [⋯]

Specification:

height:
30px

button:
subtle

icon:
14–16px

gap:
2–4px

border-bottom:
1px

---

44. Example Settings Screen

Settings

Appearance
────────────────────────────────

Theme
Interface theme                    [System ▼]

UI Density
Interface spacing                 [Default ▼]

Font Size
Application font size             [14     ]

────────────────────────────────

Editor

Font
Editor font                       [Monospace ▼]

Font Size
Editor font size                  [15     ]

基本構造:

Setting Row
├── Label
├── Description
└── Control

Setting間はCard化せず、SpacingとSeparatorで整理する。

---

45. Implementation Priority

Design Systemを実装する場合は以下の順で進める。

1. Color Tokens
2. Typography
3. Spacing
4. Surface
5. Icon
6. Button
7. Input
8. List Item
9. Tooltip
10. Popover
11. Menu
12. Panel
13. Modal
14. Settings Components
15. Component Preview

---

46. Core Principle

このDesign Systemで最も重要なのは、特定の見た目を再現することではない。

重要なのは、

Semantic Tokens
        ↓
Reusable Components
        ↓
Consistent Interaction
        ↓
Dense Product UI

という構造を維持することである。

個々の画面で、

このButtonは何色にするか

を考えるのではなく、

このActionは何を意味するのか

を決める。

同様に、

paddingを何pxにするか

ではなく、

このComponentにはどの密度が必要か

を決める。

これによりTheme、UI Density、Platformが変化しても、一貫したInterfaceを維持できる。

---

47. Quick Reference

UI Font             Sans Serif
Code Font           Monospace

UI Text             12–14px
Heading             14–22px

Icon                14–16px

Button              22–28px
Input               28–32px
Toolbar             28–32px
Tab                 28–32px

Base Gap            4px
Panel Padding       8px

Border              1px
Radius              4px

Default Button      Subtle
Default Surface     Flat
Default Elevation   None

Secondary Actions   Hover only

Color               Semantic Token only

---

48. Summary

本Design Systemは次の特性を持つ。

High Density
Minimal Decoration
Semantic Tokens
Subtle Surfaces
Small Controls
Keyboard First
Progressive Disclosure
Strong Component Reuse
Theme Independence
Accessible Interaction

目指すUIは、

«「見た目が派手なUI」ではなく、長時間使っても邪魔にならず、高密度な情報を高速に操作できるUI»

である。
