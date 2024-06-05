# Vite + JoyID

## Trouble Shooting
`Buffer is not defined`
1. Install `@esbuild-plugins/node-globals-polyfill`
2. In `vite.config.js`
```ts
import { NodeGlobalsPolyfillPlugin } from '@esbuild-plugins/node-globals-polyfill'

export default defineConfig({
    // ...other config settings
    optimizeDeps: {
        esbuildOptions: {
            // Node.js global to browser globalThis
            define: {
                global: 'globalThis'
            },
            // Enable esbuild polyfill plugins
            plugins: [
                NodeGlobalsPolyfillPlugin({
                    buffer: true
                })
            ]
        }
    }
})
```
