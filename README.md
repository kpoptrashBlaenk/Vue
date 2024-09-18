Need node-js for this:

> npm init vite@latest FOLDERNAME --template vue
> Vue
> TypeScript
> cd FOLDERNAME
> npm install
> npm run dev


create shims-vue.d.ts in src folder and paste this:
//////////////////////////////////////////////////
declare module '*.vue' {
    import { DefineComponent } from 'vue'
    const component: DefineComponent<{}, {}, any>
    export default component
  }
//////////////////////////////////////////////////
to solve intellisense not finding vue modules



Creating a dist for github pages:

Open vite.config.ts and add base: / in defineConfig (usually it's <rep-name> but github-pages doesn't use a subfolder since i's its own site)
//////////////////////////////////////////////////
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

export default defineConfig({
  plugins: [vue()],
  base: '/'
})
//////////////////////////////////////////////////

Open package.json and change script to
//////////////////////////////////////////////////
"scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
//////////////////////////////////////////////////

> npm run build

> npm install --save-dev gh-pages
> npm run deploy