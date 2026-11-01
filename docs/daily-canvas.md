# Daily Canvas integration

This fork documents the lightweight [Daily Canvas](https://github.com/baymac/daily-canvas) desktop adapter. The upstream CLI and extension continue to supply browser access; Daily does not embed a second browser or copy browser credentials.

1. Install BrowserSkill and connect its extension in your regular browser profile, following the upstream quick start.
2. Open Daily Canvas → Settings → Connections → Desktop assistant.
3. Choose **Find browsers**, select the connected instance for that profile, and save.
4. Open Assistant and ask for a browser task, for example “Read this article and save its useful ideas to my canvas with tags and sources.”

Daily binds `session start --browser <instance_id>` explicitly. It uses Agent Windows, observes before actions, passes current refs to click/fill/select/press/scroll operations, and stops its session on success, failure or cancellation. Existing user tabs require explicit borrowing and any extension approval. A Stop or denial is preserved; the adapter does not switch instances, restart a daemon or change automation settings to bypass it.

The fixed adapter does not expose evaluation, cookie extraction, browser storage, arbitrary CLI flags or a shell tool to the model. Optional screenshots are returned as image blocks for a vision-capable model. Browser contents remain untrusted reference data. Actions that submit, publish, purchase or delete require an explicit user task.

The separate Daily Canvas Clipper extension handles manual page/link/image/selection/crop capture through the installed app's native messaging host. It works without an agent or BrowserSkill session. API keys stay on the desktop; captured sources are saved before AI enrichment. Chat can manipulate Canvas and Board through the same commands used by Daily's local MCP.

Adapter source and setup: [Daily Canvas desktop assistant](https://github.com/baymac/daily-canvas/blob/feat/desktop-web-clipper/docs/DESKTOP-ASSISTANT.md).
