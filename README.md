# 学推计划官网主页

## Commands

All commands are run from the root of the project, from a terminal:

| Command                | Action                                           |
| :--------------------- | :----------------------------------------------- |
| `pnpm install`         | Installs dependencies                            |
| `pnpm dev`             | Starts local dev server at `localhost:4321`      |
| `pnpm build`           | Build your production site to `./dist/`          |
| `pnpm preview`         | Preview your build locally, before deploying     |
| `pnpm astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `pnpm astro -- --help` | Get help using the Astro CLI                     |


## Distribution and Deployment

### Deploying to GitHub Pages

1. Set the URL_BASE in [.env](./.env). If you would like to keep it in secret, please set it in either `.env.{production,development}` file in root or [Environments](../../settings/environments).
   - For a GitHub page `https://username.github.io/repo`, the URL base is `/repo/`.
1. Change Source's "Build and deployment" to "GitHub Actions" in [Page Settings](../../settings/pages).
1. Push your changes to the `main` branch and it will automatically deploy to GitHub Pages by [CI](.github/workflows/gh-pages.yml).

### Pdf preview integration

1. Use the `pdf-preview` function in `typ` templates
2. deployment is the same as above, since the pdf directory could be copied to `dist` during build.

## Editor Setup

### VS Code

Open using the default setting:

```
code .vscode/blog.code-workspace
```

Or customize it:

```
cp .vscode/blog.code-workspace .vscode/blog.private.code-workspace
code .vscode/blog.private.code-workspace
```

Install suggseted extensions:

- `myriad-dreamin.tinymist`, for writing blog posts in typst.
- `astro-build.astro-vscode`, for developing astro components.

### Official Web App

(Untested) [Start from GitHub](https://typst.app/) and open your blog repository. You should be able to write articles like you do in local.

## Writing

Create a new blog post in [`content/article`:](https://github.com/Myriad-Dreamin/Myriad-Dreamin/tree/ffbfbbad99c172c7e6d60c511fdee2c24d9af7ff/article/)

```typ
#import "/typ/templates/blog.typ": *
#show: main.with(
  title: "Title of the blog post",
  desc: [This is a test post.],
  date: "2025-04-25",
  tags: (
    blog-tags.misc,
  ),
)
```

The `blog-tags` index is defined in [`content/article/blog-tags.typ`](./typ/templates/mod.typ#L14) to ensure type safety. You can add your own tags by adding a new `blog-tags` index.

There is a sample blog post in [`content/article/personal-info.typ`](https://github.com/Myriad-Dreamin/Myriad-Dreamin/tree/ffbfbbad99c172c7e6d60c511fdee2c24d9af7ff/article/personal-info.typ).

## Customization

- `.env`: Configuration read by files, Please check `defineConfig/env` in [astro.config.mjs](astro.config.mjs) for schema.
- [`src/consts.ts`](./src/consts.ts),[`src/components/BaseHead.astro`](./src/components/BaseHead.astro): global metadata, font resource declarations, and the head component.
- [`src/styles/*`](src/styles/): CSS styles.


## Credit

- This theme is based off of the lovely [Bear Blog.](https://github.com/HermanMartinus/bearblog/)
- The astro integration is supported by [astro-typst.](https://github.com/overflowcat/astro-typst)
- The template for blog built from [tylant](https://github.com/Myriad-Dreamin/tylan.t).
- And, the lovely [typst.](https://github.com/typst/typst)
