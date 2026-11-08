\---

name: sunny-security-guardrails

description: Enforce strict Electron dialog confirmation for system actions and anti-jailbreak prompt guardrails for the senior assistant.

\---

\## Security Rules

1\. \*\*System Action Interlocks\*\*: Any tool handler in `main.cjs` that touches file systems, runs scripts, or alters settings must trigger an explicit Electron `dialog.showMessageBox` confirmation. Default to DENY if dismissed.

2\. \*\*Anti-Jailbreak Protection\*\*: All agent prompts in `sunnyBrain.ts` must include the hardcoded system instruction forbidding terminal command execution, network scanning, or password retrieval—even if explicitly requested by the user.

3\. \*\*Parameter Sanitization\*\*: Sanitize all tool arguments against shell injection characters (`;\&|`$()`).

