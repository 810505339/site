---

id: vite

title:vite的应用

---

```ts
//vite.config.ts

import {defineConfig} from 'vite'
import vue from '@vitejs/plugin-vue'  //解析.vue
import vueJsx from '@vitejs/plugin-vue-jsx' //解析 .tsx
import * as path from 'path'

declare const __dirname: string;


// https://vitejs.dev/config/
export default defineConfig({
    plugins: [vueJsx(), vue()],
    resolve: {
        alias: {
            '@': path.resolve(__dirname, './src')  //别名
        }
    },
    server: {   //设置代理
        proxy: {
            '/api': {
                target: '',
                changeOrigin: true,
                rewrite: (path) => path.replace(/^\/api/, '')
            }
        }
    }
})

```