# Default Vue 3 + Vite + TypeScript Template
Vite + Vue template with TypeScript
- [ESLint](https://eslint.org/) is used for linting and [Prettier](https://prettier.io/) is used for code formatting.
- [Vue Router](https://router.vuejs.org/) is included for multi-page apps, remove it if not needed.
- [Pinia](https://pinia.esm.dev/) is included for state management, remove it if not needed.
- Helm charts for Kubernetes are also included.
- [PostCSS](https://postcss.org/) is used for CSS processing and includes CSS Nesting support plugin.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).
JetBrains IDEs are also recommended, but make sure to use Vue Language Server (Volar).
If you use Vim or Emacs, you probably already know what you're doing. 

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize Vite configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Dockerfile

Dockerfile is included for building a Docker [NGINX](https://nginx.com) image with the app production build. Basic configuration is included in `conf` folder, but it's recommended to customize it for your needs.

## GitHub Actions

GitHub Actions workflow is included for building Docker image and pushing it to GitHub Container Registry, 
and subsequently [publishing Helm charts to GitHub Pages](https://helm.sh/docs/topics/chart_repository/).

## Project Setup

Node 20 or higher is required.
Node installation is recommended via [nvm](https://github.com/nvm-sh/nvm).

If you are interested in GitHub Actions workflow that works with this project, you need to set up GitHub Variables for your repository at `https://github.com/<workspace>/<project>/settings/variables/actions`:
- `DOCKER_IMAGE_NAME` - The name of the Docker image for uploading to the repository. Format: `<workspace>/<project>`

Also `gh-pages` branch should be created for publishing Helm charts. To create empty gh-pages branch, run the following commands:

```sh
git switch --orphan gh-pages
git commit --allow-empty -m "gh-pages branch created"
git push -u origin gh-pages
```

Project is set up with [pnpm](https://pnpm.io/).
Also, project is [Corepack](https://github.com/nodejs/corepack)-ready, it's usually already included in modern Node.js versions.
So, there is no need to install `pnpm` globally, just run `corepack enable` and `pnpm install`.

```sh
corepack enable
pnpm install
```

### Compile and Hot-Reload for Development

```sh
pnpm dev
```

### Type-Check, Compile and Minify for Production

```sh
pnpm build
```

### Lint with [ESLint](https://eslint.org/)

```sh
pnpm lint
```

### Format with [Prettier](https://prettier.io/)

```sh
pnpm format
```
