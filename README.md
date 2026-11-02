# Emon Hossain · academic website

A compact academic site built with [Hugo](https://gohugo.io/) and the included PaperMod theme. The published address is **https://emonhossainraihan.github.io/**. No purchased domain is needed.

## Preview and build

Install **Hugo Extended 0.154.5** (the version pinned in the workflow), then run from this folder:

```sh
hugo server -D
```

Open the local URL printed by Hugo. For a production build:

```sh
hugo --gc --minify
```

Hugo writes the generated site into `public/`. Edit the source files, not the generated HTML.

## Where to edit

- `data/academic.yml`: homepage introduction, interests, and academic links.
- `content/teaching/`: courses, lecture notes, assignments, and downloadable files.
- `content/papers/`: research and publication pages.
- `content/blog/`: mathematical notes and posts.
- `content/about.md`, `content/officehours.md`, `content/location.md`: personal and student information.
- `static/cv.pdf` and `static/picture.jpeg`: CV and profile photograph.
- `assets/css/extended/`: local design overrides.
- `config.yml`: navigation, metadata, and the GitHub Pages URL.

Existing course URLs and downloads are retained.

## Write LaTeX in Markdown

Mathematics is enabled sitewide. Goldmark's passthrough extension preserves LaTeX before **MathJax 4.1.3** renders it in the browser.

```markdown
An inline equation: \(f(x) = x^2\).

The dollar form also works: $e^{i\pi} + 1 = 0$.

$$
\begin{aligned}
\int_0^1 x^2\,dx &= \frac{1}{3},\\
A &= \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}.
\end{aligned}
$$
```

- Use one backslash for commands (`\alpha`, `\frac`) and two only for mathematical line breaks.
- `\(...\)` and `$...$` are inline; `\[…\]` and `$$...$$` are display math.
- Use a fenced `latex` code block when you want to show source instead of rendering it.
- AMS equations, `\label` / `\eqref`, matrices, `CD` diagrams, and `\ce{...}` chemistry notation are supported.
- Put matrices and `aligned` inside display delimiters. Standalone AMS `equation`, `align`, `gather`, and `multline` environments (including their starred forms) are also preserved. Numbered environments support equation references.
- TikZ/`tikzcd`, custom LaTeX packages, and complete `.tex` documents require a separate LaTeX compiler. Export their output as an image or PDF.
- For a literal dollar sign outside mathematics, write `\\$`.
- Set `math: false` in a page's front matter to omit MathJax for that page.
- MathJax is loaded from jsDelivr; visitors need internet access for equation rendering.

The page [`content/writing-mathematics.md`](content/writing-mathematics.md) contains rendered examples at `/writing-mathematics/`.

Create a note using the included archetype:

```sh
hugo new content blog/my-note.md
```

It starts as a draft. Set `draft: false` when ready to publish.

## Publish on the free GitHub Pages address

The repository must remain named **`emonhossainraihan.github.io`** under the **`emonhossainraihan`** account.

1. Open [the repository's Pages settings](https://github.com/emonhossainraihan/emonhossainraihan.github.io/settings/pages).
2. Set **Build and deployment → Source** to **GitHub Actions**.
3. If **Custom domain** still contains the former domain, click **Remove**. GitHub stores this setting separately from the repository; deleting `CNAME` alone does not clear it for an Actions deployment.
4. Commit and push your source changes to `main`.
5. Watch **Actions → Build and deploy academic site**. A successful deployment publishes to **https://emonhossainraihan.github.io/**.

The `CNAME` file has been removed and `baseURL` is set to the free address. The workflow builds a clean artifact in the runner's temporary directory, so old generated files in the historical `public/` folder cannot enter the deployment. It also checks that the artifact has no `CNAME`.

Pull requests build the site without deploying it. Pushes to `main` and manual workflow runs build and deploy.

## References

- [Hugo mathematics configuration](https://gohugo.io/content-management/mathematics/)
- [Hugo deployment to GitHub Pages](https://gohugo.io/host-and-deploy/deploy-to-github-pages/)
- [GitHub: remove a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#removing-a-custom-domain)
- [MathJax LaTeX support](https://docs.mathjax.org/en/latest/input/tex/index.html)
