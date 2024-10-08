# Vue.ts with Vite on Github Pages

Here I learn how to use Vue.ts and how to build and deploy to make it accessible via Github Pages.

## Initialization

### Create and run project

Need node-js for this:
```bash
npm init vite@latest FOLDERNAME --template vue
```

Select Vue > TypeScript

```bash
cd FOLDERNAME
npm install
npm run dev
```
This runs now locally.

### Fix intellisense

Create shims-vue.d.ts in src folder and paste this:
```typescript
declare module '*.vue' {
    import { DefineComponent } from 'vue'
    const component: DefineComponent<{}, {}, any>
    export default component
  }
```
to solve intellisense not finding vue modules.

### Enhance HTTP Requests

Install Axios:
```bash
npm install axios
```

Import Axios with:
```typescript
import axios from 'axios'
```


## Creating a dist for github-pages:

### Adjust files

Open vite.config.ts and add base: '/repo-name'
```typescript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/repo-name'
})
```

Open package.json and change script to
```json
"scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
```

### Build and Deploy

```bash
npm run build

npm install --save-dev gh-pages
npm run deploy
```

### Cleaning

Build will create .vue.js (sometimes, idk) files for some reason, to remove them do:
```bash
git restore .
git clean -f
```
You very probably didn't place this in a repo and even if, you didn't commit before this step, so good luck!

### Conclusion

This will create a branch named 'gh-pages'.

Go to the repo on Github > Settings > Pages then select the branch gh-pages as source and save.

The page will be accessible on https://username.github.io/repo-name/