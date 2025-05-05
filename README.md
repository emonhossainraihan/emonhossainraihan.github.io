## Where `katex` loaded

define `layout>partials>math.html` + `https://tuedsci.github.io/blog/hugo-katex/`

- `https://discourse.gohugo.io/t/how-to-render-math-equations-properly-with-katex/40998`

## Workflow

- Progress in server mode `hugo server`
- Generate `hugo`

For decoration check [markdown-cheatsheet](https://github.com/im-luka/markdown-cheatsheet?tab=readme-ov-file#footnote).

@v4 + @v3

```
Error: Error: No uploaded artifact was found! Please check if there are any errors at build step, or uploaded artifact name is correct.
    at getSignedArtifactMetadata (/home/runner/work/_actions/actions/deploy-pages/v3/src/internal/api-client.js:94:1)
    at processTicksAndRejections (node:internal/process/task_queues:95:5)
    at Deployment.create (/home/runner/work/_actions/actions/deploy-pages/v3/src/internal/deployment.js:68:1)
    at main (/home/runner/work/_actions/actions/deploy-pages/v3/src/index.js:30:1)
Error: Error: No uploaded artifact was found! Please check if there are any errors at build step, or uploaded artifact name is correct.
```

actions/upload-artifact@v3

```
Error: This request has been automatically failed because it uses a deprecated version of `actions/upload-artifact: v3`. Learn more: https://github.blog/changelog/2024-04-16-deprecation-notice-v3-of-the-artifact-actions/
```