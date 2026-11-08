\---

name: claude-electron-security

description: Enforces type safety, strict context isolation, and native dialog confirmations across Electron main and renderer processes.

\---



\# Electron Architecture \& Security Rules



When modifying `src/electron/main.cjs`, `src/electron/preload.cjs`, or `sunnyBrain.ts`:



1\. \*\*Context Isolation\*\*:

&#x20;  - Never enable `nodeIntegration: true` or set `contextIsolation: false` in `webPreferences`.

&#x20;  - All IPC channels must be explicitly declared in `preload.cjs` using `contextBridge.exposeInMainWorld`.



2\. \*\*Native Action Interlocks\*\*:

&#x20;  - Any IPC tool handler that executes system commands, modifies files, or accesses hardware MUST invoke `dialog.showMessageBox` for user confirmation before proceeding.



3\. \*\*IPC Type Safety\*\*:

&#x20;  - Every new IPC channel added to `main.cjs` must have a matching TypeScript interface signature in `src/types/electron.d.ts`.

&#x20;  - Never pass unsanitized strings directly to shell commands (`exec`/`spawn`).

