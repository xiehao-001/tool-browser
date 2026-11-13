# Browser Search Tool

`@chatecnu-work/dsh-tool-browser` · v0.1.0-dev · MulanPSL-2.0 AND MIT

Browser Search Tool gives an agent a managed browser for search and page interaction, plus a web search provider that works without an API key. When DeepSeek credentials are configured, the provider switches to the official DeepSeek search backend; otherwise it stays on the browser path.

Each session gets its own persistent browser profile and tab set, so logins and page state do not leak between sessions. Page content is returned as untrusted data, never as instructions.

## Highlights

- Registers the `browser` tool with `navigate`, `snapshot`, `click`, `type`, `wait`, `back`, `visible`, `screenshot`, `tabs`, `select_tab`, `new_tab`, `close_tab` and `close`.
- Runs a per-session Playwright (`playwright-core`) persistent context in background or visible mode, with its own tabs and profile directory.
- Stores profiles under `DSH_HOME/browser-profile/sessions/<hash>`, or under `CHATECNU_WORK_BROWSER_PROFILE` when that variable is set.
- Registers the `eduwork-search` provider (`/search-auto`), which points `web.searchProvider` at this plugin and uses the official DeepSeek provider when credentials exist.
- Sends sensitive actions and private-network navigations through the host permission-preset hook; `danger-full-access` sessions skip the confirmation.
- Wraps page text, links and accessibility snapshots in `<untrusted_web_content>` and labels them as data.
- Resolves Chromium from the EduWork package, an installed Edge/Chrome, or `EDUWORK_BROWSER_EXECUTABLE`; no browser binary is bundled.

## Install

Install this directory as a local DSH plugin bundle. From a shell:

```bash
dsh plugin --profile web add /absolute/path/to/tool-browser
```

Or add the directory through the **Plugins** panel in DSH (local bundle). Restart the DSH app after installation; plugins are activated from the bundle patch (`cordis.patch.yml`).

## Configuration

No configuration keys: the bundle patch inserts the plugin with defaults.

## Requirements

- DeepSeek Harness `>=0.2.1 <0.3.0`
- Peer packages: `@deepseek-ai/cordis`, `@deepseek-ai/dsh-fs`, `@deepseek-ai/dsh-permission-presets`, `@deepseek-ai/dsh-tools`, `@deepseek-ai/dsh-web`, `@deepseek-ai/dsh-credentials`, `@deepseek-ai/dsh-launch-environment`, `@deepseek-ai/dsh-web-search-deepseek`, `playwright-core`

## Notes and limits

- Chromium is not shipped with this package: restore the complete EduWork package, install Microsoft Edge or Google Chrome, or set `EDUWORK_BROWSER_EXECUTABLE`.
- The managed browser is separate from the right-sidebar browser and cannot see its tabs or login state.
- The official DeepSeek search backend needs a DeepSeek credential or `DEEPSEEK_API_KEY`; without one, search runs through the managed browser.
- Version `0.1.0-dev` is a development-stage release.

## 中文文档

[README.zh-CN.md](./README.zh-CN.md)

## License

MulanPSL-2.0 AND MIT — see [LICENSE](./LICENSE) and, where present, [LICENSE-MIT](./LICENSE-MIT). Extracted from the ECNU EduWork distribution (https://github.com/ECNU/EduWork); upstream copyright and license notices are preserved.
