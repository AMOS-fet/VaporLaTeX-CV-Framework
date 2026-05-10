# VaporLaTeX CV Framework

A highly customizable, Vaporwave/Retro-Tech themed LaTeX framework designed for modern and creative resumes. This project provides a set of UI components inspired by 80s/90s operating systems, featuring dynamic shadows, halftone patterns, neon aesthetics and fully responsive layouts.

## Features
- **Dynamic Shadow Engine**: Customizable shadows with patterns (dots, grids, stripes) and a 10% opacity blending base to emulate real retro-printing effects.
- **Fluid Grid System**: The `vaporbox` command automatically calculates internal margins and background panels based on the requested number of columns.
- **Smart Typography**: Split windows (`vaporwindowsplit`) include automatic hyphenation and perfect vertical alignment.
- **VaporWindow**: Classic OS-style windows with title bars, control buttons (minimize/maximize/close) and aesthetic scrollbars.

## Prerequisites
Ensure you have a modern LaTeX distribution and include the following packages in your preamble:

```
\usepackage{xcolor}
\usepackage{fontawesome5}
\usepackage[most]{tcolorbox}
\usepackage{etoolbox}
\usepackage{tikz}
\usetikzlibrary{patterns.meta, patterns}
\usepackage{ragged2e}
\usepackage[italian, english]{babel} % Crucial for \vaporitem hyphenation
```

---

## Color Palette
The framework includes a retro-neon palette. You can pass these variable names to any component to change its theme:

| Color Code | Aesthetic | RGB Value |
| :--- | :--- | :--- |
| `vpBlack` | Soft Dark | 45, 45, 45 |
| `vpDeepNight` | Dark Purple/Navy | 43, 25, 61 |
| `vpBlue` | Deep Royal Blue | 26, 38, 160 |
| `vpPink` | Neon Hot Pink | 255, 113, 206 |
| `vpCyan` | Bright Neon Blue | 1, 205, 254 |
| `vpPurple` | Bright Violet | 185, 103, 255 |
| `vpGreen` | Toxic/Matrix Green | 39, 230, 95 |
| `vpYellow` | Retro Sun Yellow | 255, 202, 6 |
| `vpOrange` | Sunset Orange | 255, 108, 17 |

---

## Components & Usage

### 1. Header: `\vaporname`
The main component for the CV title, designed as a 3D typographic block.
```latex
\vaporname[Color]{FirstName}{LastName}[Role][ShadowPattern]
```
* **Example:** `\vaporname[vpDeepNight]{John}{Doe}[Software Dev][dots]`

### 2. Standard Window: `vaporwindow`
A classic OS-style window container for generic text blocks.
```latex
\begin{vaporwindow}[Color]{Window Title}[ShadowPattern]
    Content goes here...
\end{vaporwindow}
```

### 3. Dynamic Grid: `vaporbox`
An advanced container for contact info or skills. It automatically divides the space into columns and generates the underlying white background panels proportionally.
```latex
\begin{vaporbox}[Color][Width][ShadowPattern][Number of Columns]
    \vaporelement{icon}{Text 1} & \vaporelement{icon}{Text 2} \\
\end{vaporbox}
```
* **Arguments:**
  * `#1`: Theme color (default: `vpBlack`)
  * `#2`: Total width (default: `\linewidth`)
  * `#3`: Shadow pattern (default: `lines`)
  * `#4`: **Number of columns** (default: `2`). If set to `1`, `3`, etc., the background adapts automatically.
* **Example (3 columns):** `\begin{vaporbox}[vpBlue][\linewidth][grid][3]`

### 4. Grid Items: `\vaporelement`
Small "pills" to be used exclusively inside `vaporbox`.
```latex
\vaporelement{FontAwesomeIconName}[Optional_URL]{Text}
```
* **Example:** `\vaporelement{github}[https://github.com/user]{github.com/user}`

### 5. Split Window: `vaporwindowsplit`
Optimized for Work Experience or Education. It divides the space into a left column (25%) for dates/roles and a right column (75%) for descriptions.
```latex
\begin{vaporwindowsplit}[Color]{Title}[ShadowPattern]
    \vaporitem{Keyword}{Description...}
\end{vaporwindowsplit}
```

### 6. Split Items: `\vaporitem`
To be used inside `vaporwindowsplit`. It guarantees perfect top-alignment and forces hyphenation for long words in the narrow left column.
```latex
\vaporitem{Date/Role}{Description}
```

---

## Shadow Engine Patterns
Any component that accepts the `[ShadowPattern]` argument can use the following styles:

1. `dots`: Halftone dots.
2. `lines`: 45-degree diagonal lines.
3. `crosshatch`: Intersecting diagonal lines.
4. `grid`: Square grid.
5. `solid`: Solid color fill.
6. `random`: The engine will pick a random pattern at each compilation.
