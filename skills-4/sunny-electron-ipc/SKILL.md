\---

name: sunny-electron-ipc

description: Maintain type-safe Electron IPC bridging and context isolation between main.cjs, preload.cjs, and React components.

\---

\## Architecture Guidelines

1\. \*\*Context Isolation\*\*: Never expose raw Node.js modules (`fs`, `child\_process`) directly to the React renderer. Always route through `preload.cjs` using `contextBridge.exposeInMainWorld`.

2\. \*\*Type Safety\*\*: Whenever a new IPC handler is added to `main.cjs`, immediately update the type definitions in `src/types/electron.d.ts`.

3\. \*\*Error Boundaries\*\*: Wrap all IPC calls in try/catch blocks within `sunnyBrain.ts` to prevent UI crashes if background processes time out.

