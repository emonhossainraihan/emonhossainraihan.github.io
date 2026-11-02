---
title: "Writing mathematics"
description: "A short guide to writing mathematical notes with Markdown and LaTeX."
summary: "Inline equations, aligned calculations, matrices, and commutative diagrams."
math: true
showToc: true
hideMeta: true
---

These examples show the LaTeX syntax supported in these notes. Write the source directly in a Markdown file; the site typesets it with MathJax.

## Inline mathematics

Use `\( ... \)` for a formula inside a sentence. For example, `\(f(x) = x^2\)` produces \(f(x) = x^2\). The familiar `$ ... $` syntax also works: $e^{i\pi}+1=0$.

Use a single backslash for commands such as `\alpha`, `\frac`, and `\mathbb`. Reserve `\\` for line breaks inside a matrix or aligned calculation.

## Display equations

Put a longer equation between `$$` on separate lines, or between `\[` and `\]`.

```latex
$$
\int_0^1 x^2\,dx = \frac{1}{3}.
$$
```

$$
\int_0^1 x^2\,dx = \frac{1}{3}.
$$

## Aligned calculations and matrices

```latex
$$
\begin{aligned}
\nabla \cdot (\phi \mathbf{v})
  &= \nabla \phi \cdot \mathbf{v}
     + \phi \nabla \cdot \mathbf{v},\\
A &= \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}.
\end{aligned}
$$
```

$$
\begin{aligned}
\nabla \cdot (\phi \mathbf{v})
  &= \nabla \phi \cdot \mathbf{v}
     + \phi \nabla \cdot \mathbf{v},\\
A &= \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}.
\end{aligned}
$$

For automatic numbering, use an `equation` environment on its own, without surrounding `$$`. AMS environments and `\label` / `\eqref` are supported:

```latex
\begin{equation}
E = mc^2 \label{eq:energy}
\end{equation}

See equation \(\eqref{eq:energy}\).
```

\begin{equation}
E = mc^2 \label{eq:energy}
\end{equation}

See equation \(\eqref{eq:energy}\).

## Commutative diagrams

Simple diagrams use the AMS `CD` environment:

```latex
$$
\begin{CD}
A @>f>> B\\
@VgVV @VVhV\\
C @>>k> D
\end{CD}
$$
```

$$
\begin{CD}
A @>f>> B\\
@VgVV @VVhV\\
C @>>k> D
\end{CD}
$$

MathJax supports mathematical LaTeX, rather than compiling a complete `.tex` document. For TikZ or `tikzcd`, export the diagram as an SVG, PNG, or PDF and link it from the note.

## Add a note

Create a new file with `hugo new content blog/my-note.md`, replace the title and description, and set `draft: false` when it is ready. Preview drafts with `hugo server -D`.

Keep source examples in fenced code blocks, as above, to display the LaTeX itself. For an ordinary dollar sign outside mathematics, write `\\$`.

MathJax loads from a public CDN, so an internet connection is needed to typeset equations. The Markdown and course downloads remain ordinary static files on GitHub Pages.
