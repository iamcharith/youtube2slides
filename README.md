# youtube2slides

Chrome side panel + local daemon based on `steipete/summarize`, rebranded for generating slide-ready output from YouTube videos and web content.

## Local setup

```powershell
npm i -g @steipete/summarize
summarize daemon install --token <extension-token>
summarize daemon status
```

If Windows Scheduled Task registration fails with `task XML is malformed` or `Access is denied`, run the daemon manually for the current session:

```powershell
summarize daemon run
```

The extension talks to the daemon at `http://127.0.0.1:8787` and requires the same token saved in the extension options.

## API config

Store local secrets in `%USERPROFILE%\.summarize\config.json` on Windows or `~/.summarize/config.json` on macOS/Linux, not in this repository:

```json
{
  "env": {
    "OPENAI_BASE_URL": "http://localhost:20128/v1",
    "OPENAI_API_KEY": "<api-key>"
  }
}
```

## Development

```powershell
corepack enable
pnpm install
pnpm -C apps/chrome-extension build
pnpm typecheck
pnpm lint
```

Load the built Chrome extension from `apps/chrome-extension/.output/chrome-mv3`.
